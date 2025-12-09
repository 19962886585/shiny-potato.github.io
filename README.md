<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CR | 设计 - 翻页模式</title>
    <!-- 引入Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- 引入Font Awesome -->
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <!-- 自定义配置 -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#FF6B6B',
                        secondary: '#2A3B4C',
                        neutral: '#F5F7FA',
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                    },
                    animation: {
                        'fade-in': 'fadeIn 0.8s ease-in-out',
                        'slide-up': 'slideUp 1s ease-out',
                        'page-fade': 'pageFade 0.5s ease-in-out',
                    },
                    keyframes: {
                        fadeIn: {
                            '0%': { opacity: '0' },
                            '100%': { opacity: '1' },
                        },
                        slideUp: {
                            '0%': { transform: 'translateY(30px)', opacity: '0' },
                            '100%': { transform: 'translateY(0)', opacity: '1' },
                        },
                        pageFade: {
                            '0%': { opacity: '0.8', transform: 'translateY(20px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        },
                    },
                }
            }
        }
    </script>
    <style type="text/tailwindcss">
        @layer utilities {
            .content-auto { content-visibility: auto; }
            .text-shadow { text-shadow: 0 2px 4px rgba(0,0,0,0.1); }
            .hover-scale { transition: transform 0.3s ease; }
            .hover-scale:hover { transform: scale(1.03); }
            .nav-active { border-bottom: 2px solid theme('colors.primary'); }
            .vertical-text {
                writing-mode: vertical-rl;
                text-orientation: upright;
            }
            /* 翻页模式核心样式 */
            html, body {
                overflow: hidden; /* 隐藏全局滚动条 */
                height: 100%;
            }
            .page-section {
                height: 100vh; /* 每个板块占满视口 */
                width: 100%;
                position: relative;
                overflow: hidden;
                transition: all 0.5s ease-in-out;
            }
        }
    </style>
</head>
<body class="bg-white text-secondary font-sans antialiased">
    <!-- 导航栏（固定顶部）- 移除技能导航项，调整联系页页码为3 -->
    <nav id="navbar" class="fixed w-full z-50 transition-all duration-300 bg-white/90 backdrop-blur-sm shadow-sm">
        <div class="container mx-auto px-4 md:px-8 py-4 flex justify-between items-center">
            <a href="#" class="text-2xl font-bold text-primary">CR Design</a>
            <!-- 桌面端导航 -->
            <div class="hidden md:flex space-x-8 text-lg">
                <a href="#home" class="nav-active hover:text-primary transition-colors" data-page="0">首页</a>
                <a href="#about" class="hover:text-primary transition-colors" data-page="1">关于我</a>
                <a href="#portfolio" class="hover:text-primary transition-colors" data-page="2">作品集</a>
                <a href="#contact" class="hover:text-primary transition-colors" data-page="3">联系</a>
            </div>
            <!-- 移动端菜单按钮 -->
            <button id="menuBtn" class="md:hidden text-2xl">
                <i class="fa fa-bars"></i>
            </button>
        </div>
        <!-- 移动端导航菜单 - 移除技能导航项，调整联系页页码为3 -->
        <div id="mobileMenu" class="hidden md:hidden bg-white shadow-lg absolute w-full">
            <div class="container mx-auto px-4 py-4 flex flex-col space-y-4 text-lg">
                <a href="#home" class="py-2 nav-active hover:text-primary transition-colors" data-page="0">首页</a>
                <a href="#about" class="py-2 hover:text-primary transition-colors" data-page="1">关于我</a>
                <a href="#portfolio" class="py-2 hover:text-primary transition-colors" data-page="2">作品集</a>
                <a href="#contact" class="py-2 hover:text-primary transition-colors" data-page="3">联系</a>
            </div>
        </div>
    </nav>

    <!-- 翻页容器（核心）- 移除skills板块 -->
    <div id="pageContainer" class="h-full w-full">
        <!-- 首页（第0页） -->
        <section id="home" class="page-section flex items-end bg-gradient-to-r from-[#E9ECEF] to-[#F8F9FA] pb-16 md:pb-24">
            <div class="absolute inset-0 z-0">
                <div class="absolute top-20 left-10 w-32 h-32 rounded-full bg-primary/10 blur-2xl"></div>
                <div class="absolute bottom-20 right-10 w-48 h-48 rounded-full bg-secondary/10 blur-2xl"></div>
            </div>
            
            <!-- 左侧竖排文字 -->
            <div class="absolute left-4 md:left-10 top-1/2 transform -translate-y-1/2 z-10 animate-fade-in">
                <h1 class="vertical-text text-[clamp(4rem,12vw,6rem)] font-bold text-shadow text-secondary/90">
                    设计
                </h1>
            </div>

            <!-- 底部核心文案 -->
            <div class="container mx-auto px-4 md:px-16 lg:px-24 z-10 text-center w-full animate-page-fade">
                <h2 class="text-[clamp(2.5rem,8vw,5rem)] font-bold leading-tight text-shadow animate-fade-in">
                    <span class="text-primary">创意无限</span>
                </h2>
                <p class="mt-6 text-[clamp(1.2rem,4vw,1.5rem)] text-secondary/80 max-w-2xl mx-auto animate-slide-up">
                    专注平面设计、UI/UX、品牌视觉、插画创作，用设计传递价值与美感
                </p>
                <div class="mt-10 flex flex-col sm:flex-row justify-center gap-4 animate-slide-up">
                    <a href="#portfolio" class="px-8 py-3 bg-primary text-white rounded-lg font-medium hover:bg-primary/90 transition-colors shadow-lg" data-page="2">
                        查看作品集
                    </a>
                    <a href="#contact" class="px-8 py-3 border-2 border-secondary text-secondary rounded-lg font-medium hover:bg-secondary hover:text-white transition-colors" data-page="3">
                        联系我
                    </a>
                </div>
            </div>

            <!-- 翻页提示（下一页） -->
            <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 animate-bounce z-10">
                <button class="text-secondary/60 hover:text-primary transition-colors" id="nextPageBtn">
                    <i class="fa fa-chevron-down text-2xl"></i>
                </button>
            </div>
        </section>

        <!-- 关于我（第1页）- 保留核心技能卡片（非独立技能模块） -->
        <section id="about" class="page-section py-20 bg-white hidden">
            <div class="container mx-auto px-4 md:px-8 h-full flex flex-col justify-center animate-page-fade">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.8rem,5vw,2.5rem)] font-bold">关于我</h2>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                </div>
                <div class="flex flex-col md:flex-row items-center gap-12">
                    <!-- 个人照片 -->
                    <div class="w-full md:w-1/3">
                        <div class="relative hover-scale">
                            <img src="https://picsum.photos/id/177/600/800" alt="个人照片" class="w-full h-auto rounded-lg shadow-xl object-cover">
                            <div class="absolute inset-0 bg-primary/20 rounded-lg mix-blend-overlay"></div>
                        </div>
                    </div>
                    <!-- 个人信息 -->
                    <div class="w-full md:w-2/3">
                        <h3 class="text-2xl font-bold mb-4">CR | 设计专业学生</h3>
                        <p class="text-secondary/80 mb-6 leading-relaxed">
                            现就读于苏州大学视觉传达设计专业，擅长将创意理念转化为视觉作品，注重细节与作品表达。
                            目前正在系统学习各类设计知识与技能，持续打磨设计基础能力及审美素养，积极参与校内实践项目以积累经验，
                            热爱探索不同风格的设计表达形式，致力于用设计解决实际问题、传递真实情感。
                        </p>
                        <!-- 核心信息卡片 -->
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6 mb-8">
                            <div class="bg-neutral p-6 rounded-lg shadow-sm">
                                <h4 class="font-bold text-lg mb-2 flex items-center">
                                    <i class="fa fa-graduation-cap text-primary mr-2"></i> 教育背景
                                </h4>
                                <p>苏州大学 | 视觉传达设计专业 | 在读</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm">
                                <h4 class="font-bold text-lg mb-2 flex items-center">
                                    <i class="fa fa-puzzle-piece text-primary mr-2"></i> 核心技能
                                </h4>
                                <p>PS/AI/Figma/InDesign/Procreate | 平面/品牌/UI/插画设计</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm">
                                <h4 class="font-bold text-lg mb-2 flex items-center">
                                    <i class="fa fa-lightbulb-o text-primary mr-2"></i> 设计理念
                                </h4>
                                <p>以细节见真章，以表达传情感，用设计语言解决问题、传递温度。</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm">
                                <h4 class="font-bold text-lg mb-2 flex items-center">
                                    <i class="fa fa-paint-brush text-primary mr-2"></i> 学习方向
                                </h4>
                                <p>视觉传达 | 平面设计 | 品牌视觉 | 设计基础 | 审美培养</p>
                            </div>
                        </div>
                        <!-- 下载简历按钮 -->
                        <a href="你的简历链接" target="_blank" class="inline-flex items-center px-6 py-3 bg-secondary text-white rounded-lg hover:bg-secondary/90 transition-colors">
                            <i class="fa fa-download mr-2"></i> 下载简历
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- 作品集（第2页） -->
        <section id="portfolio" class="page-section py-20 bg-neutral hidden">
            <div class="container mx-auto px-4 md:px-8 h-full flex flex-col justify-center animate-page-fade">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.8rem,5vw,2.5rem)] font-bold">作品集</h2>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                    <p class="mt-4 text-secondary/80 max-w-2xl mx-auto">
                        精选近期设计作品，涵盖平面、品牌、UI等多个领域，记录我的设计成长
                    </p>
                </div>

                <!-- 作品分类筛选 -->
                <div class="flex flex-wrap justify-center gap-4 mb-12">
                    <button class="filter-btn active px-6 py-2 rounded-full bg-primary text-white" data-filter="all">全部</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors" data-filter="graphic">平面设计</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors" data-filter="brand">品牌视觉</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors" data-filter="ui">UI设计</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors" data-filter="illustration">插画</button>
                </div>

                <!-- 作品网格 -->
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- 作品1-平面设计（杂志排版） -->
                    <div class="portfolio-item hover-scale" data-category="graphic">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/30/600/400" alt="杂志排版设计" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">杂志排版设计</h3>
                                <p class="text-white/80 mt-2">基于极简风格的时尚杂志内页排版</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品2-品牌视觉（咖啡品牌） -->
                    <div class="portfolio-item hover-scale" data-category="brand">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/431/600/400" alt="咖啡品牌视觉系统" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">咖啡品牌视觉系统</h3>
                                <p class="text-white/80 mt-2">LOGO设计、包装设计、宣传物料全套</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品3-UI设计（健身APP） -->
                    <div class="portfolio-item hover-scale" data-category="ui">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/180/600/400" alt="健身APP界面设计" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">健身APP界面设计</h3>
                                <p class="text-white/80 mt-2">运动记录、课程预约功能UI/UX设计</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品4-插画（城市印象） -->
                    <div class="portfolio-item hover-scale" data-category="illustration">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/76/600/400" alt="城市印象插画集" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">城市印象插画集</h3>
                                <p class="text-white/80 mt-2">以扁平化风格绘制的城市地标系列</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品5-平面设计（音乐节海报） -->
                    <div class="portfolio-item hover-scale" data-category="graphic">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/91/600/400" alt="音乐节海报设计" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">音乐节海报设计</h3>
                                <p class="text-white/80 mt-2">结合动态元素的潮流音乐节宣传海报</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品6-品牌视觉（文创产品） -->
                    <div class="portfolio-item hover-scale" data-category="brand">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/239/600/400" alt="文创产品品牌设计" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">文创产品品牌设计</h3>
                                <p class="text-white/80 mt-2">基于传统文化元素的文创品牌视觉</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- 加载更多按钮 -->
                <div class="text-center mt-16">
                    <button class="px-8 py-3 border-2 border-primary text-primary rounded-lg font-medium hover:bg-primary hover:text-white transition-colors">
                        加载更多作品
                    </button>
                </div>
            </div>
        </section>

        <!-- 联系方式（第3页）- 浅色风格+表单横向居中调整 -->
        <section id="contact" class="page-section py-20 bg-neutral text-secondary hidden">
            <div class="container mx-auto px-4 md:px-8 h-full flex flex-col justify-center animate-page-fade">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.8rem,5vw,2.5rem)] font-bold">联系我</h2>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                    <p class="mt-4 text-secondary/80 max-w-2xl mx-auto">
                        欢迎合作、交流或咨询，期待与你一起创造更多可能
                    </p>
                </div>

                <!-- 统一居中布局 -->
                <div class="max-w-4xl mx-auto">
                    <!-- 联系信息 - 整体居中 -->
                    <div class="text-center mb-8">
                        <div class="inline-flex flex-col md:flex-row items-start md:items-center gap-8 justify-center">
                            <!-- 邮箱 -->
                            <div class="flex items-center justify-center">
                                <div class="bg-primary/10 p-4 rounded-full mr-4">
                                    <i class="fa fa-envelope text-primary text-xl"></i>
                                </div>
                                <div class="text-left">
                                    <h4 class="text-xl font-bold mb-1">邮箱</h4>
                                    <p class="text-secondary/80">xxx@xxx.com（替换为你的邮箱）</p>
                                </div>
                            </div>
                            <!-- 电话 -->
                            <div class="flex items-center justify-center">
                                <div class="bg-primary/10 p-4 rounded-full mr-4">
                                    <i class="fa fa-phone text-primary text-xl"></i>
                                </div>
                                <div class="text-left">
                                    <h4 class="text-xl font-bold mb-1">电话</h4>
                                    <p class="text-secondary/80">138xxxx8888（替换为你的电话）</p>
                                </div>
                            </div>
                            <!-- 所在地 -->
                            <div class="flex items-center justify-center">
                                <div class="bg-primary/10 p-4 rounded-full mr-4">
                                    <i class="fa fa-map-marker text-primary text-xl"></i>
                                </div>
                                <div class="text-left">
                                    <h4 class="text-xl font-bold mb-1">所在地</h4>
                                    <p class="text-secondary/80">苏州（替换为你的所在地）</p>
                                </div>
                            </div>
                        </div>

                        <!-- 社交平台 -->
                        <div class="mt-8">
                            <h4 class="text-xl font-bold mb-4">社交平台</h4>
                            <div class="flex justify-center space-x-6 mt-2">
                                <a href="#" target="_blank" class="text-secondary/80 hover:text-primary transition-colors text-2xl">
                                    <i class="fa fa-behance"></i>
                                </a>
                                <a href="#" target="_blank" class="text-secondary/80 hover:text-primary transition-colors text-2xl">
                                    <i class="fa fa-weibo"></i>
                                </a>
                                <a href="#" target="_blank" class="text-secondary/80 hover:text-primary transition-colors text-2xl">
                                    <i class="fa fa-github"></i>
                                </a>
                                <a href="#" target="_blank" class="text-secondary/80 hover:text-primary transition-colors text-2xl">
                                    <i class="fa fa-weixin"></i>
                                </a>
                            </div>
                        </div>
                    </div>

                    <!-- 横向缩小的留言表单 - 社交平台下方 + 居中 -->
                    <div class="bg-white p-6 rounded-lg shadow-sm max-w-5xl mx-auto">
                        <form class="flex flex-wrap justify-center items-end gap-4">
                            <div class="w-full sm:w-auto">
                                <label for="name" class="block text-secondary/80 mb-2 text-sm">姓名</label>
                                <input type="text" id="name" class="w-full sm:w-48 px-3 py-2 rounded-lg bg-neutral border border-secondary/20 text-secondary placeholder-secondary/50 focus:outline-none focus:border-primary text-sm" placeholder="你的姓名">
                            </div>
                            <div class="w-full sm:w-auto">
                                <label for="email" class="block text-secondary/80 mb-2 text-sm">邮箱</label>
                                <input type="email" id="email" class="w-full sm:w-48 px-3 py-2 rounded-lg bg-neutral border border-secondary/20 text-secondary placeholder-secondary/50 focus:outline-none focus:border-primary text-sm" placeholder="你的邮箱">
                            </div>
                            <div class="w-full sm:w-auto">
                                <label for="message" class="block text-secondary/80 mb-2 text-sm">留言</label>
                                <input type="text" id="message" class="w-full sm:w-64 px-3 py-2 rounded-lg bg-neutral border border-secondary/20 text-secondary placeholder-secondary/50 focus:outline-none focus:border-primary text-sm" placeholder="简短留言">
                            </div>
                            <div class="w-full sm:w-auto">
                                <button type="submit" class="w-full sm:w-28 py-2 bg-primary text-white rounded-lg font-medium hover:bg-primary/90 transition-colors shadow-sm text-sm">
                                    发送留言
                                </button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- 翻页模式核心JS - 移除技能模块相关逻辑，调整页码为4页（0-3） -->
    <script>
        // 全局变量
        const pageContainer = document.getElementById('pageContainer');
        const sections = document.querySelectorAll('.page-section');
        const navLinks = document.querySelectorAll('[data-page]');
        const nextPageBtn = document.getElementById('nextPageBtn');
        let currentPage = 0; // 当前页码（从0开始）
        const totalPages = sections.length; // 现在是4页（0:首页,1:关于我,2:作品集,3:联系）
        let isAnimating = false; // 防止快速翻页

        // 1. 移动端菜单切换
        const menuBtn = document.getElementById('menuBtn');
        const mobileMenu = document.getElementById('mobileMenu');
        menuBtn.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
            menuBtn.innerHTML = mobileMenu.classList.contains('hidden') ? '<i class="fa fa-bars"></i>' : '<i class="fa fa-times"></i>';
        });

        // 2. 导航栏滚动效果（翻页模式下简化）
        const navbar = document.getElementById('navbar');
        navbar.classList.add('py-2', 'shadow-md');

        // 3. 翻页核心函数
        function goToPage(pageNum) {
            // 边界判断
            if (pageNum < 0 || pageNum >= totalPages || isAnimating) return;
            isAnimating = true;

            // 隐藏当前页，显示目标页
            sections.forEach((section, index) => {
                section.classList.add('hidden');
                if (index === pageNum) {
                    section.classList.remove('hidden');
                }
            });

            // 更新导航激活状态
            navLinks.forEach(link => {
                link.classList.remove('nav-active');
                if (Number(link.dataset.page) === pageNum) {
                    link.classList.add('nav-active');
                }
            });

            // 更新当前页码
            currentPage = pageNum;

            // 解锁动画状态
            setTimeout(() => {
                isAnimating = false;
            }, 600);
        }

        // 4. 导航点击翻页
        navLinks.forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const targetPage = Number(link.dataset.page);
                goToPage(targetPage);
                // 关闭移动端菜单
                if (!mobileMenu.classList.contains('hidden')) {
                    mobileMenu.classList.add('hidden');
                    menuBtn.innerHTML = '<i class="fa fa-bars"></i>';
                }
            });
        });

        // 5. 鼠标滚轮翻页
        window.addEventListener('wheel', (e) => {
            if (isAnimating) return;
            // 向下滚动 = 下一页，向上滚动 = 上一页
            const direction = e.deltaY > 0 ? 1 : -1;
            goToPage(currentPage + direction);
        });

        // 6. 键盘上下键翻页
        window.addEventListener('keydown', (e) => {
            if (isAnimating) return;
            if (e.key === 'ArrowDown' || e.key === 'PageDown') {
                goToPage(currentPage + 1);
            } else if (e.key === 'ArrowUp' || e.key === 'PageUp') {
                goToPage(currentPage - 1);
            }
        });

        // 7. 下一页按钮点击
        nextPageBtn.addEventListener('click', () => {
            goToPage(currentPage + 1);
        });

        // 8. 作品集筛选功能
        const filterBtns = document.querySelectorAll('.filter-btn');
        const portfolioItems = document.querySelectorAll('.portfolio-item');
        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                filterBtns.forEach(b => {
                    b.classList.remove('active', 'bg-primary', 'text-white');
                    b.classList.add('bg-white', 'text-secondary');
                });
                btn.classList.add('active', 'bg-primary', 'text-white');
                btn.classList.remove('bg-white', 'text-secondary');

                const filter = btn.getAttribute('data-filter');
                portfolioItems.forEach(item => {
                    if (filter === 'all' || item.getAttribute('data-category') === filter) {
                        item.style.display = 'block';
                    } else {
                        item.style.display = 'none';
                    }
                });
            });
        });

        // 初始化：显示第一页
        goToPage(0);
    </script>
</body>
</html>
