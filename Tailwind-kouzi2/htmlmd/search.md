<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>搜索 - 影视资源</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            brand: '#22c55e',
            'brand-dark': '#16a34a',
            'brand-light': '#dcfce7',
          }
        }
      }
    }
  </script>
  <style>
    * { scrollbar-width: none; -ms-overflow-style: none; }
    *::-webkit-scrollbar { display: none; }
    html, body { overflow-x: hidden; }
    body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", sans-serif; }
    .nav-scroll { overflow-x: auto; white-space: nowrap; -webkit-overflow-scrolling: touch; }
    .nav-link { transition: background-color 0.15s; }
    .nav-link:hover { background-color: rgba(0,0,0,0.12); }
    .nav-active { font-weight: 700; text-decoration: underline; text-underline-offset: 4px; }
    /* 导航左右渐变遮罩 */
    .nav-fade-l, .nav-fade-r { position: absolute; top: 0; bottom: 0; width: 40px; z-index: 2; pointer-events: none; opacity: 0; transition: opacity 0.2s; }
    .nav-fade-l { left: 0; background: linear-gradient(to right, #22c55e, transparent); }
    .nav-fade-r { right: 0; background: linear-gradient(to left, #22c55e, transparent); }
    /* 滚动按钮 */
    .nav-arrow { position: absolute; top: 50%; transform: translateY(-50%); z-index: 3; width: 28px; height: 28px; border-radius: 50%; background: rgba(0,0,0,0.25); color: #fff; display: flex; align-items: center; justify-content: center; cursor: pointer; border: none; padding: 0; opacity: 0; transition: opacity 0.2s, background 0.15s; }
    .nav-arrow:hover { background: rgba(0,0,0,0.45); }
    .nav-arrow.visible { opacity: 1; }
    .nav-arrow-l { left: 6px; }
    .nav-arrow-r { right: 6px; }
    /* 移动端隐藏箭头，保留触摸滑动 + 渐变提示 */
    @media (max-width: 767px) { .nav-arrow { display: none; } }
    /* 更多下拉 */
    .nav-more-btn { display: flex; align-items: center; gap: 2px; background: rgba(0,0,0,0.18); border: none; color: #fff; font-size: 13px; padding: 0 12px; cursor: pointer; flex-shrink: 0; position: relative; z-index: 4; height: 100%; }
    .nav-more-btn:hover { background: rgba(0,0,0,0.32); }
    .nav-more-btn svg { transition: transform 0.2s; }
    .nav-more-btn.open svg { transform: rotate(180deg); }
    .nav-more-panel { position: absolute; top: 100%; right: 0; min-width: 360px; background: #fff; border-radius: 0 0 6px 6px; box-shadow: 0 6px 20px rgba(0,0,0,0.15); z-index: 50; padding: 10px 14px; display: none; }
    .nav-more-panel.show { display: block; }
    .nav-more-panel a { display: inline-block; padding: 5px 10px; font-size: 13px; color: #374151; border-radius: 4px; margin: 2px; text-decoration: none; }
    .nav-more-panel a:hover { background: #dcfce7; color: #16a34a; }
    .card-img { aspect-ratio: 3/4; }
    .card-img img { transition: transform 0.3s ease; }
    .movie-card:hover .card-img img { transform: scale(1.05); }
    .page-btn { transition: all 0.2s; }
    .page-btn:active { opacity: 0.75; transform: scale(0.97); }

    /* 高亮关键词 */
    mark.kw { background: #fef9c3; color: #b45309; padding: 0 2px; border-radius: 2px; font-weight: 600; }
  </style>
</head>
<body class="bg-gray-100 min-h-screen flex flex-col">

  <!-- 顶部导航栏 -->
  <header class="bg-white shadow-sm">
    <div class="max-w-[1200px] mx-auto px-3 md:px-6 h-14 flex items-center gap-2 md:gap-3">
      <a href="index.html" class="flex-shrink-0 text-xl md:text-2xl font-bold text-gray-900 tracking-tight">影视资源</a>
      <form id="topSearchForm" action="search.html" method="get" onsubmit="return doSearch(event,this)" class="flex-1 md:flex-none md:w-[420px] md:ml-auto flex items-center gap-2 min-w-0">
        <select name="type" class="flex-shrink-0 h-8 box-border border border-gray-300 rounded px-2 text-sm bg-white text-gray-700 cursor-pointer focus:outline-none focus:border-green-500">
          <option value="0">无尽资源</option>
          <option value="1">精选资源</option>
          <option value="2">热门资源</option>
        </select>
        <input name="wd" type="search" autocomplete="off" aria-label="搜索关键词" placeholder="请输入关键词搜索" value="茅山"
          class="flex-1 min-w-0 h-8 box-border border border-gray-300 rounded-l px-3 text-sm focus:outline-none focus:border-green-500" />
        <button type="submit" class="flex-shrink-0 -ml-2 h-8 box-border border border-transparent bg-[#22c55e] hover:bg-[#16a34a] text-white px-3 md:px-4 rounded-r text-sm font-medium active:opacity-75">搜索</button>
      </form>
    </div>
  </header>

  <!-- 绿色分类导航栏 -->
  <nav class="bg-[#22c55e] shadow">
    <div class="max-w-[1200px] mx-auto flex items-stretch">
      <!-- 可滚动区域 -->
      <div class="relative flex-1 min-w-0">
        <div class="nav-fade-l" id="navFadeL"></div>
        <div class="nav-fade-r" id="navFadeR"></div>
        <button class="nav-arrow nav-arrow-l" id="navArrowL" onclick="navScroll(-1)">
          <svg viewBox="0 0 24 24" class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M15 18l-6-6 6-6"/></svg>
        </button>
        <button class="nav-arrow nav-arrow-r" id="navArrowR" onclick="navScroll(1)">
          <svg viewBox="0 0 24 24" class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M9 18l6-6-6-6"/></svg>
        </button>
        <div class="nav-scroll flex items-center px-3 md:px-6" id="navScroll">
          <a href="index.html" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">最近更新</a>
          <a href="list.html?cat=电影" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">电影</a>
          <a href="list.html?cat=连续剧" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">连续剧</a>
          <a href="list.html?cat=综艺" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">综艺</a>
          <a href="list.html?cat=动漫" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">动漫</a>
          <a href="list.html?cat=动作片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">动作片</a>
          <a href="list.html?cat=喜剧片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">喜剧片</a>
          <a href="list.html?cat=爱情片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">爱情片</a>
          <a href="list.html?cat=科幻片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">科幻片</a>
          <a href="list.html?cat=恐怖片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">恐怖片</a>
          <a href="list.html?cat=剧情片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">剧情片</a>
          <a href="list.html?cat=战争片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">战争片</a>
          <a href="list.html?cat=国产剧" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">国产剧</a>
          <a href="list.html?cat=香港剧" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">香港剧</a>
          <a href="list.html?cat=台湾剧" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">台湾剧</a>
          <a href="list.html?cat=韩国剧" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">韩国剧</a>
          <a href="list.html?cat=日本剧" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">日本剧</a>
          <a href="list.html?cat=欧美剧" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">欧美剧</a>
          <a href="list.html?cat=海外剧" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">海外剧</a>
          <a href="list.html?cat=纪录片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">纪录片</a>
          <a href="list.html?cat=动画片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">动画片</a>
          <a href="list.html?cat=悬疑片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">悬疑片</a>
          <a href="list.html?cat=奇幻片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">奇幻片</a>
          <a href="list.html?cat=灾难片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">灾难片</a>
          <a href="list.html?cat=传记片" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">传记片</a>
          <a href="list.html?cat=泰剧" class="nav-link text-white text-sm px-3 py-2.5 flex-shrink-0">泰剧</a>
        </div>
      </div>
      <!-- 更多 -->
      <div class="relative flex-shrink-0">
        <button class="nav-more-btn" id="navMoreBtn" onclick="toggleNavMore()">
          更多
          <svg viewBox="0 0 24 24" class="w-3.5 h-3.5" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M6 9l6 6 6-6"/></svg>
        </button>
        <div class="nav-more-panel" id="navMorePanel">
          <a href="index.html">最近更新</a>
          <a href="list.html?cat=电影">电影</a>
          <a href="list.html?cat=连续剧">连续剧</a>
          <a href="list.html?cat=综艺">综艺</a>
          <a href="list.html?cat=动漫">动漫</a>
          <a href="list.html?cat=动作片">动作片</a>
          <a href="list.html?cat=喜剧片">喜剧片</a>
          <a href="list.html?cat=爱情片">爱情片</a>
          <a href="list.html?cat=科幻片">科幻片</a>
          <a href="list.html?cat=恐怖片">恐怖片</a>
          <a href="list.html?cat=剧情片">剧情片</a>
          <a href="list.html?cat=战争片">战争片</a>
          <a href="list.html?cat=国产剧">国产剧</a>
          <a href="list.html?cat=香港剧">香港剧</a>
          <a href="list.html?cat=台湾剧">台湾剧</a>
          <a href="list.html?cat=韩国剧">韩国剧</a>
          <a href="list.html?cat=日本剧">日本剧</a>
          <a href="list.html?cat=欧美剧">欧美剧</a>
          <a href="list.html?cat=海外剧">海外剧</a>
          <a href="list.html?cat=纪录片">纪录片</a>
          <a href="list.html?cat=动画片">动画片</a>
          <a href="list.html?cat=悬疑片">悬疑片</a>
          <a href="list.html?cat=奇幻片">奇幻片</a>
          <a href="list.html?cat=灾难片">灾难片</a>
          <a href="list.html?cat=传记片">传记片</a>
          <a href="list.html?cat=泰剧">泰剧</a>
        </div>
      </div>
    </div>
  </nav>

  <!-- 主内容区 -->
  <main class="flex-1 max-w-[1200px] mx-auto w-full px-3 md:px-6 py-4">

    <!-- 搜索结果摘要 -->
    <div class="bg-white rounded shadow-sm px-3 md:px-4 py-3 mb-4">
      <p class="text-xs md:text-sm text-gray-700">
        搜索关键词
        <mark class="kw" id="kwLabel">茅山</mark>
        — 共找到
        <span class="text-[#16a34a] font-bold">3</span>
        条结果
      </p>
    </div>

    <!-- 结果列表（横向卡片：海报 + 信息） -->
    <div class="space-y-3">

      <!-- 结果 1 -->
      <a href="info.html" class="movie-card flex bg-white rounded shadow-sm hover:shadow-md transition-shadow overflow-hidden">
        <div class="flex-shrink-0 w-[90px] md:w-[130px] overflow-hidden">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_c6d68453-34c9-43a6-a803-e124021e7782.jpg" alt="茅山学宫" class="w-full h-full object-cover aspect-[3/4]">
        </div>
        <div class="flex-1 min-w-0 p-2.5 md:p-3 flex flex-col">
          <h3 class="text-sm md:text-base font-bold text-gray-900 leading-snug line-clamp-1">
            <mark class="kw">茅山</mark>学宫
          </h3>
          <p class="text-[11px] md:text-xs text-gray-500 mt-1 line-clamp-1">国产动漫 · 玄幻 · 修仙 · 中国大陆 · 2025</p>
          <p class="text-[11px] md:text-xs text-gray-500 mt-0.5 line-clamp-1">导演：王畅</p>
          <p class="text-[11px] md:text-xs text-gray-500 mt-0.5 line-clamp-2 md:line-clamp-1">主演：魏拓晨,橙瑞,夜叉,可小幽,正经太郎,展羽,刘中正,带轮儿</p>
          <p class="text-xs text-gray-600 mt-1.5 line-clamp-2 md:line-clamp-3 leading-relaxed hidden md:block">
            蓝星人周雨肥在一场粒子对撞实验中意外跃迁到一个全民修仙的异世界大陆，为了找到这个世界的粒子加速器重返蓝星，道术小白周雨肥在猫妖黑猫和龙女林白的帮助下，结合现代思维知识逻辑，在<mark class="kw">茅山</mark>学宫开始学习<mark class="kw">茅山</mark>道术。
          </p>
          <div class="mt-auto pt-1.5 flex items-center justify-between text-[11px] md:text-xs">
            <span class="text-red-500">已更新至 14 集</span>
            <span class="text-gray-400">2026-06-04</span>
          </div>
        </div>
      </a>

      <!-- 结果 2 -->
      <a href="info.html" class="movie-card flex bg-white rounded shadow-sm hover:shadow-md transition-shadow overflow-hidden">
        <div class="flex-shrink-0 w-[90px] md:w-[130px] overflow-hidden">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_732f234b-9902-42ae-b1f2-c2c683059052.jpg" alt="茅山道士" class="w-full h-full object-cover aspect-[3/4]">
        </div>
        <div class="flex-1 min-w-0 p-2.5 md:p-3 flex flex-col">
          <h3 class="text-sm md:text-base font-bold text-gray-900 leading-snug line-clamp-1">
            <mark class="kw">茅山</mark>道士之天师斗僵尸
          </h3>
          <p class="text-[11px] md:text-xs text-gray-500 mt-1 line-clamp-1">恐怖片 · 玄幻 · 香港 · 1985</p>
          <p class="text-[11px] md:text-xs text-gray-500 mt-0.5 line-clamp-1">导演：刘观伟</p>
          <p class="text-[11px] md:text-xs text-gray-500 mt-0.5 line-clamp-2 md:line-clamp-1">主演：林正英,许冠英,钱小豪,楼南光</p>
          <p class="text-xs text-gray-600 mt-1.5 line-clamp-2 md:line-clamp-3 leading-relaxed hidden md:block">
            <mark class="kw">茅山</mark>派九叔受邀至任老爷家替老太爷迁葬，发现棺木异常，破解后引出一段惊心动魄的僵尸追逐战。经典港产<mark class="kw">茅山</mark>题材代表作。
          </p>
          <div class="mt-auto pt-1.5 flex items-center justify-between text-[11px] md:text-xs">
            <span class="text-red-500">高清正片</span>
            <span class="text-gray-400">2026-05-21</span>
          </div>
        </div>
      </a>

      <!-- 结果 3 -->
      <a href="info.html" class="movie-card flex bg-white rounded shadow-sm hover:shadow-md transition-shadow overflow-hidden">
        <div class="flex-shrink-0 w-[90px] md:w-[130px] overflow-hidden">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_25618832-40fa-4a65-b0fc-8605cc6ad350.jpg" alt="新茅山客栈" class="w-full h-full object-cover aspect-[3/4]">
        </div>
        <div class="flex-1 min-w-0 p-2.5 md:p-3 flex flex-col">
          <h3 class="text-sm md:text-base font-bold text-gray-900 leading-snug line-clamp-1">
            新<mark class="kw">茅山</mark>客栈
          </h3>
          <p class="text-[11px] md:text-xs text-gray-500 mt-1 line-clamp-1">剧情片 · 喜剧 · 中国大陆 · 2024</p>
          <p class="text-[11px] md:text-xs text-gray-500 mt-0.5 line-clamp-1">导演：常山</p>
          <p class="text-[11px] md:text-xs text-gray-500 mt-0.5 line-clamp-2 md:line-clamp-1">主演：张子贤,牛犇,梁静</p>
          <p class="text-xs text-gray-600 mt-1.5 line-clamp-2 md:line-clamp-3 leading-relaxed hidden md:block">
            一座坐落于江南古镇的老客栈"<mark class="kw">茅山</mark>客栈"重新开张，伴随着五湖四海客人的到访，店主与店员们经历着一桩桩啼笑皆非又温情脉脉的故事。
          </p>
          <div class="mt-auto pt-1.5 flex items-center justify-between text-[11px] md:text-xs">
            <span class="text-red-500">高清正片</span>
            <span class="text-gray-400">2026-04-19</span>
          </div>
        </div>
      </a>

    </div>

    <!-- 空态（默认隐藏，无结果时显示） -->
    <div id="emptyState" class="hidden bg-white rounded shadow-sm py-12 md:py-16 text-center mt-3">
      <div class="text-5xl text-gray-300 mb-3">⌕</div>
      <p class="text-sm text-gray-600 mb-1">未找到与「<span id="emptyKw" class="text-gray-900 font-medium">关键词</span>」相关的结果</p>
      <p class="text-xs text-gray-400">换个关键词试试，或返回 <a href="index.html" class="text-[#16a34a] hover:underline">首页</a> 浏览最近更新</p>
    </div>

    <!-- 底部分页 -->
    <div class="flex justify-center items-center gap-1 md:gap-2 mt-6 mb-2 flex-nowrap whitespace-nowrap">
      <button onclick="goPage('first')" class="page-btn border border-gray-300 bg-white hover:bg-gray-50 text-gray-700 px-3 py-1.5 text-sm rounded">首页</button>
      <button onclick="goPage('prev')" class="page-btn border border-gray-300 bg-white hover:bg-gray-50 text-gray-700 px-3 py-1.5 text-sm rounded">上一页</button>
      <span class="border border-gray-300 bg-white text-gray-700 px-3 py-1.5 text-sm rounded select-none">1/1</span>
      <button onclick="goPage('next')" class="page-btn border border-gray-300 bg-white hover:bg-gray-50 text-gray-700 px-3 py-1.5 text-sm rounded">下一页</button>
      <button onclick="goPage('last')" class="page-btn border border-gray-300 bg-white hover:bg-gray-50 text-gray-700 px-3 py-1.5 text-sm rounded">尾页</button>
    </div>

  </main>

  <!-- Footer -->
  <footer class="bg-white border-t border-gray-200 py-4 text-center text-sm text-gray-500 mt-2">
    <p>Powered by <span class="text-gray-700 font-medium">影视资源</span></p>
    <p class="mt-1">联系邮箱：<a href="mailto:admin@admin.com" class="text-gray-600 hover:text-green-600">admin@admin.com</a></p>
  </footer>

  <script>
    // 读取 URL ?wd= 回显并高亮（演示用，后端接入时由模板渲染）
    (function () {
      const params = new URLSearchParams(location.search);
      const wd = (params.get('wd') || '').trim();
      if (wd) {
        const input = document.querySelector('#topSearchForm input[name=wd]');
        if (input) input.value = wd;
        const label = document.getElementById('kwLabel');
        if (label) label.textContent = wd;
      }
    })();

// 移动端 placeholder 缩短，避免被截断
    (function(){
      var wd = document.querySelector('header input[name="wd"]');
      if(!wd) return;
      function syncPh(){ wd.placeholder = window.innerWidth < 768 ? '搜索' : '请输入关键词搜索'; }
      syncPh();
      window.addEventListener('resize', syncPh);
    })();

        function doSearch(e, form) {
      e.preventDefault();
      const wd = (form.wd.value || '').trim();
      if (!wd) { form.wd.focus(); return false; }
      location.href = 'search.html?wd=' + encodeURIComponent(wd) + '&type=' + encodeURIComponent(form.type.value || '0');
      return false;
    }

    // ======== 导航滚动 + 更多下拉 ========
    (function(){
      var sc = document.getElementById('navScroll');
      var aL = document.getElementById('navArrowL');
      var aR = document.getElementById('navArrowR');
      var fL = document.getElementById('navFadeL');
      var fR = document.getElementById('navFadeR');
      if (!sc) return;

      function check() {
        var sl = sc.scrollLeft, cw = sc.clientWidth, sw = sc.scrollWidth;
        var canL = sl > 2, canR = sl + cw < sw - 2;
        aL.classList.toggle('visible', canL);
        aR.classList.toggle('visible', canR);
        fL.style.opacity = canL ? 1 : 0;
        fR.style.opacity = canR ? 1 : 0;
      }
      check();
      sc.addEventListener('scroll', check);
      window.addEventListener('resize', check);

      window.navScroll = function(dir) {
        sc.scrollBy({ left: dir * 200, behavior: 'smooth' });
      };
    })();

    function toggleNavMore() {
      var btn = document.getElementById('navMoreBtn');
      var panel = document.getElementById('navMorePanel');
      var open = panel.classList.toggle('show');
      btn.classList.toggle('open', open);
    }
    // 点击外部关闭"更多"下拉
    document.addEventListener('click', function(e) {
      var btn = document.getElementById('navMoreBtn');
      var panel = document.getElementById('navMorePanel');
      if (!btn || !panel) return;
      if (!btn.contains(e.target) && !panel.contains(e.target)) {
        panel.classList.remove('show');
        btn.classList.remove('open');
      }
    });

    function goPage(type) {
      const tips = { first: '已在首页', prev: '已在首页', next: '已在尾页', last: '已在尾页' };
      alert(tips[type] || '');
    }
  </script>
</body>
</html>
