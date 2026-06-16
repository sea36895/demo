<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>影视资源 - 公共布局</title>
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
    /* layout placeholder 标识 */
    .layout-slot { border: 1.5px dashed #86efac; background: repeating-linear-gradient(45deg,#f0fdf4,#f0fdf4 8px,#ffffff 8px,#ffffff 16px); }
  </style>
</head>
<body class="bg-gray-100 min-h-screen flex flex-col">

  <!-- ============ HEADER 区块 ============ -->
  <header class="bg-white shadow-sm">
    <div class="max-w-[1200px] mx-auto px-3 md:px-6 h-14 flex items-center gap-2 md:gap-3">
      <a href="index.html" class="flex-shrink-0 text-xl md:text-2xl font-bold text-gray-900 tracking-tight">影视资源</a>
      <form action="search.html" method="get" onsubmit="return doSearch(event,this)" class="flex-1 md:flex-none md:w-[420px] md:ml-auto flex items-center gap-2 min-w-0">
        <select name="type" class="flex-shrink-0 h-8 box-border border border-gray-300 rounded px-2 text-sm bg-white text-gray-700 cursor-pointer focus:outline-none focus:border-green-500">
          <option value="0">无尽资源</option>
          <option value="1">精选资源</option>
          <option value="2">热门资源</option>
        </select>
        <input name="wd" type="search" autocomplete="off" aria-label="搜索关键词" placeholder="请输入关键词搜索"
          class="flex-1 min-w-0 h-8 box-border border border-gray-300 rounded-l px-3 text-sm focus:outline-none focus:border-green-500" />
        <button type="submit" class="flex-shrink-0 -ml-2 h-8 box-border border border-transparent bg-[#22c55e] hover:bg-[#16a34a] text-white px-3 md:px-4 rounded-r text-sm font-medium active:opacity-75">搜索</button>
      </form>
    </div>
  </header>

  <!-- ============ NAV 区块 ============ -->
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

  <!-- ============ MAIN 区块（slot 占位） ============ -->
  <main class="flex-1 max-w-[1200px] mx-auto w-full px-3 md:px-6 py-4">
    <div class="flex items-center gap-2 mb-4">
      <div class="w-1 h-5 bg-[#22c55e] rounded-sm"></div>
      <h2 class="text-base md:text-lg font-bold text-gray-900">公共布局（layout）</h2>
    </div>

    <div class="layout-slot rounded p-6 md:p-10 text-center">
      <p class="text-sm md:text-base text-gray-700 font-medium mb-2">{block name="main"}</p>
      <p class="text-xs md:text-sm text-gray-500 leading-relaxed">
        各个子页面（list.html / info.html / search.html）的正文内容会渲染在此处。<br>
        本页只用于演示头部、导航、底部三段框架，可作为开发其它页面时的骨架参考。
      </p>
    </div>

    <!-- 模块用法示意 -->
    <div class="mt-6 grid grid-cols-1 md:grid-cols-3 gap-3">
      <a href="list.html" class="block bg-white rounded shadow-sm hover:shadow-md transition-shadow p-3 md:p-4">
        <p class="text-sm font-bold text-gray-900 mb-1">List 列表页</p>
        <p class="text-xs text-gray-500 leading-relaxed">分类导航 + 多维筛选 + 影片网格 + 分页</p>
      </a>
      <a href="info.html" class="block bg-white rounded shadow-sm hover:shadow-md transition-shadow p-3 md:p-4">
        <p class="text-sm font-bold text-gray-900 mb-1">Info 简介页</p>
        <p class="text-xs text-gray-500 leading-relaxed">海报 + 信息表 + 剧情，不含播放/集数</p>
      </a>
      <a href="search.html" class="block bg-white rounded shadow-sm hover:shadow-md transition-shadow p-3 md:p-4">
        <p class="text-sm font-bold text-gray-900 mb-1">Search 搜索页</p>
        <p class="text-xs text-gray-500 leading-relaxed">关键词回显 + 结果列表 + 空态/分页</p>
      </a>
    </div>
  </main>

  <!-- ============ FOOTER 区块 ============ -->
  <footer class="bg-white border-t border-gray-200 py-4 text-center text-sm text-gray-500 mt-2">
    <p>Powered by <span class="text-gray-700 font-medium">影视资源</span></p>
    <p class="mt-1">联系邮箱：<a href="mailto:admin@admin.com" class="text-gray-600 hover:text-green-600">admin@admin.com</a></p>
  </footer>

  <script>
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
  </script>
</body>
</html>
