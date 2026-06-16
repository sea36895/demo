<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>茅山学宫 第01集 - 影视资源</title>
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

    .episode-btn { transition: all 0.15s; }
    .episode-btn:hover { background-color: #f3f4f6; border-color: #86efac; color: #16a34a; }
    .episode-btn:active { opacity: 0.75; transform: scale(0.97); }
    .episode-btn.active { background-color: #22c55e; color: #fff; border-color: #22c55e; font-weight: 600; }
    .source-tab { transition: all 0.15s; }
    .source-tab.active { background-color: #22c55e; color: #fff; border-color: #22c55e; }
    .ctrl-btn { transition: all 0.15s; }
    .ctrl-btn:hover { background-color: #f0fdf4; color: #16a34a; border-color: #86efac; }
    /* 播放器占位 */
    .player-shell { aspect-ratio: 16/9; background: radial-gradient(ellipse at center, #1f2937 0%, #0a0d12 70%); }
    .player-shell::after {
      content: '';
      position: absolute; inset: 0;
      background-image: radial-gradient(rgba(255,255,255,0.04) 1px, transparent 1px);
      background-size: 4px 4px;
      pointer-events: none;
    }
  </style>
</head>
<body class="bg-gray-100 min-h-screen flex flex-col">

  <!-- 顶部导航栏 -->
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
          <a href="list.html?cat=动漫" class="nav-link nav-active text-white text-sm px-3 py-2.5 flex-shrink-0">动漫</a>
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

    <!-- 面包屑 -->
    <nav class="mb-3 text-xs md:text-sm">
      <a href="index.html" class="text-blue-600 hover:text-blue-800">首页</a>
      <span class="mx-1.5 text-gray-400">»</span>
      <a href="list.html?cat=动漫" class="text-blue-600 hover:text-blue-800">国产动漫</a>
      <span class="mx-1.5 text-gray-400">»</span>
      <a href="info.html" class="text-blue-600 hover:text-blue-800">茅山学宫</a>
      <span class="mx-1.5 text-gray-400">»</span>
      <span class="text-gray-600">第01集</span>
    </nav>

    <!-- 播放器 -->
    <div>

      <!-- 左：播放器壳 -->
      <div class="bg-white rounded shadow-sm overflow-hidden">
        <div class="player-shell relative w-full flex items-center justify-center">
          <!-- 中央 Play 按钮 + 文案（占位，对接真实播放器后替换） -->
          <button onclick="loadPlayer()" class="relative z-10 group flex flex-col items-center text-white/90 hover:text-white">
            <span class="flex items-center justify-center w-14 h-14 md:w-16 md:h-16 rounded-full bg-[#22c55e]/90 group-hover:bg-[#22c55e] shadow-lg shadow-black/40 transition">
              <svg viewBox="0 0 24 24" class="w-6 h-6 md:w-7 md:h-7 ml-1" fill="currentColor"><path d="M8 5v14l11-7z"/></svg>
            </span>
            <span class="mt-3 text-xs md:text-sm tracking-wide">点击播放 · 第01集 · yun 线路</span>
          </button>
          <!-- 左上角 logo -->
          <div class="absolute top-2 left-3 text-white/70 text-[11px] md:text-xs font-medium select-none">影视资源 · 在线播放</div>
        </div>

        <!-- 播放器下方控制条：标题 + 上下集 + 选集按钮 -->
        <div class="px-3 md:px-4 py-3 border-t border-gray-100">
          <div class="flex items-center justify-between gap-2 md:gap-3">
            <div class="min-w-0">
              <h1 class="text-sm md:text-base font-bold text-gray-900 truncate">茅山学宫 · 第01集</h1>
              <p class="text-[11px] md:text-xs text-gray-500 mt-0.5 truncate">国产动漫 · 中国大陆 · 2025 · 共 14 集</p>
            </div>
            <div class="flex-shrink-0 flex items-center gap-1.5">
              <button onclick="prevEpisode()" class="ctrl-btn border border-gray-300 bg-white text-gray-700 text-xs md:text-sm px-2.5 md:px-3 py-1.5 rounded">上一集</button>
              <button onclick="nextEpisode()" class="ctrl-btn border border-gray-300 bg-white text-gray-700 text-xs md:text-sm px-2.5 md:px-3 py-1.5 rounded">下一集</button>
              <button onclick="document.getElementById('episodeBlock').scrollIntoView({behavior:'smooth'})" class="ctrl-btn border border-gray-300 bg-white text-gray-700 text-xs md:text-sm px-2.5 md:px-3 py-1.5 rounded">选集</button>
            </div>
          </div>
        </div>
      </div>

    </div>

    <!-- 移动端 / 全端：完整选集区（带 anchor，供"选集"按钮锚定） -->
    <section id="episodeBlock" class="mt-5 bg-white rounded shadow-sm px-3 md:px-4 py-3 md:py-4">
      <div class="flex items-center justify-between mb-3">
        <div class="flex items-center gap-2">
          <div class="w-1 h-5 bg-[#22c55e] rounded-sm"></div>
          <h3 class="text-sm md:text-base font-bold text-gray-900">《茅山学宫》选集</h3>
        </div>
        <span class="text-[11px] md:text-xs text-gray-400">已更新 14 / 24 集</span>
      </div>
      <!-- 线路 tab（移动端） -->
      <div class="mb-3 flex items-center gap-1.5">
        <span class="text-[11px] text-gray-500 mr-1">线路：</span>
        <button class="source-tab active text-xs border border-gray-300 rounded px-2.5 py-1 text-gray-700">yun</button>
        <button class="source-tab text-xs border border-gray-300 rounded px-2.5 py-1 text-gray-700">线路2</button>
        <button class="source-tab text-xs border border-gray-300 rounded px-2.5 py-1 text-gray-700">线路3</button>
      </div>
      <!-- 集数网格（全端） -->
      <div class="grid grid-cols-4 sm:grid-cols-6 md:grid-cols-8 lg:grid-cols-10 xl:grid-cols-12 gap-2" id="episodeListAll"></div>
    </section>

    <!-- 影片信息（简版） + 剧情 -->
    <section class="mt-5 grid grid-cols-1 md:grid-cols-[120px_1fr] lg:grid-cols-[150px_1fr] gap-3 md:gap-4">
      <a href="info.html" class="flex-shrink-0 block rounded overflow-hidden shadow-sm bg-white max-w-[120px] md:max-w-none">
        <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_c6d68453-34c9-43a6-a803-e124021e7782.jpg" alt="茅山学宫" class="w-full aspect-[3/4] object-cover">
      </a>
      <div class="min-w-0">
        <div class="flex items-center gap-2 mb-2">
          <a href="info.html" class="text-base md:text-lg font-bold text-gray-900 hover:text-[#16a34a]">茅山学宫</a>
          <span class="text-[11px] md:text-xs text-gray-400">查看完整信息 →</span>
        </div>
        <p class="text-xs md:text-sm text-gray-600 leading-relaxed">
          <span class="text-gray-500">导演：</span>王畅
          <span class="mx-1.5 text-gray-300">|</span>
          <span class="text-gray-500">类型：</span>国产动漫·玄幻·修仙
          <span class="mx-1.5 text-gray-300">|</span>
          <span class="text-gray-500">地区：</span>中国大陆
        </p>
        <p class="text-xs md:text-sm text-gray-600 leading-relaxed mt-1.5">
          <span class="text-gray-500">主演：</span>魏拓晨,橙瑞,夜叉,可小幽,正经太郎,展羽,刘中正,带轮儿
        </p>
        <p class="text-xs md:text-sm text-gray-700 leading-relaxed mt-2 text-pretty line-clamp-3 md:line-clamp-none">
          蓝星人周雨肥在一场粒子对撞实验中意外跃迁到一个全民修仙的异世界大陆，为了找到这个世界的粒子加速器重返蓝星，道术小白周雨肥在猫妖黑猫和龙女林白的帮助下，结合现代思维知识逻辑，在茅山学宫开始学习茅山道术。
        </p>
      </div>
    </section>

    <!-- 观看帮助 -->
    <div class="mt-5 bg-white border border-gray-200 rounded p-3 md:p-4">
      <h3 class="text-sm font-bold text-gray-900 mb-2">观看帮助：</h3>
      <ol class="list-decimal list-inside text-xs md:text-sm text-gray-600 leading-relaxed space-y-0.5">
        <li>播放器加载需要等待几秒，请耐心。</li>
        <li>个别线路偶尔卡顿，可切换上方"线路2 / 线路3"试试。</li>
        <li>如果遇到无法播放，多刷新几次或更换浏览器。</li>
      </ol>
    </div>


  </main>

  <!-- Footer -->
  <footer class="bg-white border-t border-gray-200 py-4 text-center text-sm text-gray-500 mt-4">
    <p>Powered by <span class="text-gray-700 font-medium">影视资源</span></p>
    <p class="mt-1">联系邮箱：<a href="mailto:admin@admin.com" class="text-gray-600 hover:text-green-600">admin@admin.com</a></p>
  </footer>

  <script>
    // 渲染集数列表
    const TOTAL = 14;
    let current = 1;

    function renderEpisodes() {
      const html = [];
      for (let i = 1; i <= TOTAL; i++) {
        const label = '第' + String(i).padStart(2, '0') + '集';
        const active = i === current ? ' active' : '';
        html.push('<button class="episode-btn' + active + ' border border-gray-300 bg-white rounded px-1 py-1.5 text-xs text-gray-700 text-center" onclick="selectEpisode(' + i + ')">' + label + '</button>');
      }
      const code = html.join('');
      document.getElementById('episodeListAll').innerHTML = code;
    }
    renderEpisodes();

    function selectEpisode(ep) {
      current = ep;
      renderEpisodes();
      // 真实接入：location.href = '?id=xxx&ep=' + ep
      document.querySelector('h1').textContent = '茅山学宫 · 第' + String(ep).padStart(2, '0') + '集';
      // 滚到播放器顶部，体验更好
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function prevEpisode() {
      if (current > 1) selectEpisode(current - 1);
    }
    function nextEpisode() {
      if (current < TOTAL) selectEpisode(current + 1);
      else alert('已经是最新一集，敬请期待更新');
    }

    function loadPlayer() {
      // 真实接入：插入 <iframe src="..."> 或挂 DPlayer/Aliplayer 实例
      alert('演示页：此处接入真实播放器（iframe / DPlayer / Aliplayer 等）');
    }

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
