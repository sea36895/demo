<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>国产动漫 - 影视资源</title>
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
    .card-img { aspect-ratio: 3/4; }
    .card-img img { transition: transform 0.3s ease; }
    .movie-card:hover .card-img img { transform: scale(1.05); }
    .page-btn { transition: all 0.2s; }
    .page-btn:active { opacity: 0.75; transform: scale(0.97); }
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
      <span class="text-gray-600">动漫</span>
      <span class="mx-1.5 text-gray-400">»</span>
      <span class="text-gray-600">国产动漫</span>
    </nav>


    <!-- 列表标题 -->
    <div class="flex items-center justify-between mb-3">
      <div class="flex items-center gap-2">
        <div class="w-1 h-5 bg-[#22c55e] rounded-sm"></div>
        <h2 class="text-base md:text-lg font-bold text-gray-900">动漫</h2>
        <span class="text-xs text-gray-400">共 1284 部</span>
      </div>
      <span class="text-xs text-gray-400 hidden md:inline">当前 第 1 页</span>
    </div>

    <!-- 影片网格 -->
    <div class="grid grid-cols-2 md:grid-cols-5 gap-3 md:gap-4">
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/MiaoTu_12fc162a-44fd-4711-b2fd-4f48c970b9e3.jpg" alt="完美世界" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">完美世界</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-04 19:42:38</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_c6d68453-34c9-43a6-a803-e124021e7782.jpg" alt="茅山学宫" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">茅山学宫</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-04 19:37:52</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_a5e59a4b-c96d-47b5-8c83-b7b33737aa4b.jpg" alt="斗破苍穹" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">斗破苍穹·年番</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-04 14:21:08</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_732f234b-9902-42ae-b1f2-c2c683059052.jpg" alt="斗罗大陆" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">斗罗大陆·绝世唐门</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-04 13:55:02</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/MiaoTu_275435c9-fd25-4fba-8317-1e747a28bd3f.jpg" alt="灵笼" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">灵笼 第二季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-04 11:08:43</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_bbb0bb27-5e23-49d0-96bd-d4780b666951.jpg" alt="一人之下" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">一人之下 第五季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-03 22:14:30</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_dc8644af-db92-4247-afb5-a7b376a06ecb.jpg" alt="武庚纪" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">武庚纪 第六季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-03 20:00:12</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_611a24f0-1f9e-408b-9042-17aea4fbab39.jpg" alt="天官赐福" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">天官赐福 第二季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-03 18:42:19</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_94426016-d6f7-4ca1-b996-8843fce9c084.jpg" alt="魔道祖师" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">魔道祖师·完结篇</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-03 17:01:55</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_25618832-40fa-4a65-b0fc-8605cc6ad350.jpg" alt="眷思量" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">眷思量 第二季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-03 15:33:08</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_3aab5381-6f64-413e-b568-b8a24bc5add9.jpg" alt="时光代理人" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">时光代理人 第二季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-03 14:08:21</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_c5b4b7b5-e918-4f2a-a063-f14dcc5968ce.jpg" alt="罗小黑战记" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">罗小黑战记 番外篇</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-03 12:46:50</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_986fa0c1-3dfb-4533-892d-c726b3f7d408.jpg" alt="百妖谱" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">百妖谱 第四季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-03 10:18:09</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_a9c6a0b4-a6c4-41bb-9ee4-1b57c280d75d.jpg" alt="画江湖" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">画江湖之不良人 第七季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-02 23:50:11</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_31806cdd-eced-4db8-918e-697c10997208.jpg" alt="刺客伍六七" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">刺客伍六七·终局</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-02 22:11:43</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_df613c4c-601c-41ca-81d1-24210eee3c20.jpg" alt="雾山五行" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">雾山五行 第二季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-02 21:00:00</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_b52665b0-52ee-42a4-81b0-9ef54014571e.jpg" alt="三体动画" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">三体 第二季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-02 18:33:21</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_8790631e-6a1d-4b41-8b3f-139a013a171c.jpg" alt="刺客信条" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">秦时明月·沧海横流</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-02 16:21:08</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/MiaoTu_12fc162a-44fd-4711-b2fd-4f48c970b9e3.jpg" alt="星辰变" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">星辰变 第五季</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-02 13:09:55</p>
        </div>
      </a>
      <a href="info.html" class="movie-card block bg-white rounded shadow-sm hover:shadow-md transition-shadow">
        <div class="card-img relative overflow-hidden rounded-t">
          <img src="https://miaoda-site-img.cdn.bcebos.com/images/baidu_image_search_a5e59a4b-c96d-47b5-8c83-b7b33737aa4b.jpg" alt="斗破苍穹外传" class="w-full h-full object-cover">
          <span class="absolute bottom-1 right-1 bg-black/60 text-white text-[10px] px-1.5 py-0.5 rounded">国产动漫</span>
        </div>
        <div class="p-1.5">
          <p class="text-xs md:text-sm text-gray-800 font-medium truncate">异常生物见闻录</p>
          <p class="text-[11px] md:text-xs text-red-500 mt-0.5">2026-06-02 10:48:30</p>
        </div>
      </a>
    </div>

    <!-- 底部分页 -->
    <div class="flex justify-center items-center gap-1 md:gap-2 mt-6 mb-2 flex-nowrap whitespace-nowrap">
      <button onclick="goPage('first')" class="page-btn border border-gray-300 bg-white hover:bg-gray-50 text-gray-700 px-3 py-1.5 text-sm rounded">首页</button>
      <button onclick="goPage('prev')" class="page-btn border border-gray-300 bg-white hover:bg-gray-50 text-gray-700 px-3 py-1.5 text-sm rounded">上一页</button>
      <span class="border border-gray-300 bg-white text-gray-700 px-3 py-1.5 text-sm rounded select-none">1/65</span>
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
      const tips = { first: '已在首页', prev: '已在首页', next: '下一页加载中...', last: '跳转到尾页...' };
      if (type === 'first' || type === 'prev') return;
      alert(tips[type] || '');
    }
  </script>
</body>
</html>
