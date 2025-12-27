<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CR | 设计</title>
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
                        primary: '#FF6B6B', // 主红色
                        secondary: '#2A3B4C',
                        neutral: '#F5F7FA',
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                        heiti: ['SimHei', '黑体', 'Microsoft YaHei', 'sans-serif'],
                    },
                    animation: {
                        'fade-in': 'fadeIn 0.8s ease-in-out',
                        'slide-up': 'slideUp 1s ease-out',
                        'page-fade': 'pageFade 0.5s ease-in-out',
                        'text-pulse': 'textPulse 3s ease-in-out infinite',
                        'modal-fade': 'modalFade 0.3s ease-in-out',
                        'img-scale': 'imgScale 0.4s ease-out',
                        'border-pulse': 'borderPulse 2s ease-in-out infinite',
                        'shine': 'shine 1.5s ease-in-out infinite',
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
                        textPulse: {
                            '0%, 100%': { opacity: '1' },
                            '50%': { opacity: '0.85' },
                        },
                        modalFade: {
                            '0%': { opacity: '0' },
                            '100%': { opacity: '1' },
                        },
                        imgScale: {
                            '0%': { transform: 'scale(0.9)', opacity: '0' },
                            '100%': { transform: 'scale(1)', opacity: '1' },
                        },
                        borderPulse: {
                            '0%, 100%': { outlineOffset: '0px', opacity: '1' },
                            '50%': { outlineOffset: '8px', opacity: '0.8' },
                        },
                        shine: {
                            '0%': { backgroundPosition: '-100px' },
                            '100%': { backgroundPosition: '200px' },
                        },
                    },
                }
            }
        }
    </script>
    <style type="text/tailwindcss">
        @layer utilities {
            .content-auto { content-visibility: auto; }
            .text-shadow { text-shadow: 0 2px 8px rgba(0,0,0,0.12); }
            .text-shadow-lg { text-shadow: 0 4px 12px rgba(0,0,0,0.15); }
            .hover-scale { transition: transform 0.3s ease; }
            .hover-scale:hover { transform: scale(1.03); }
            .nav-active { border-bottom: 2px solid theme('colors.primary'); }
            .vertical-text {
                writing-mode: vertical-rl;
                text-orientation: upright;
            }
            /* 核心样式 */
            html, body {
                overflow: hidden;
                height: 100%;
                cursor: none;
            }
            /* 自定义光标样式 - 降低透明度修改 */
            .custom-cursor {
                position: fixed;
                width: 16px;
                height: 16px;
                background: #FF0000; /* 纯红色核心光标 */
                border-radius: 50%;
                z-index: 99999;
                pointer-events: none;
                transition: transform 0.15s ease, width 0.2s ease, height 0.2s ease, opacity 0.2s ease;
                opacity: 0.5; /* 从0.8降低到0.5，可根据需求调整 */
            }
            .cursor-follower {
                position: fixed;
                width: 40px;
                height: 40px;
                border: 1px solid #FF0000; /* 纯红色跟随圆环边框 */
                border-radius: 50%;
                z-index: 99998;
                pointer-events: none;
                transition: transform 0.25s ease, opacity 0.2s ease;
                opacity: 0.3; /* 从0.5降低到0.3，可根据需求调整 */
            }
            /* 光标hover高亮状态 - 同步降低透明度 */
            .cursor-hovered .custom-cursor {
                transform: scale(1.8);
                background: #E53935; /* 高亮深红色 */
                opacity: 0.8; /* 从1降低到0.8 */
            }
            .cursor-hovered .cursor-follower {
                transform: scale(1.2);
                border-color: #E53935; /* 高亮深红色边框 */
                opacity: 0.6; /* 从0.8降低到0.6 */
            }

            /* 作品项hover增强 */
            .portfolio-item {
                transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
            }
            .portfolio-item:hover {
                transform: translateY(-8px) scale(1.02);
                box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
            }
            .portfolio-item .absolute {
                transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
            }
            .portfolio-item:hover .absolute {
                opacity: 1;
                background: linear-gradient(to top, rgba(0,0,0,0.8), rgba(255,107,107,0.2));
            }

            /* 按钮hover增强（红色渐变） */
            .btn-ripple {
                position: relative;
                overflow: hidden;
                background: linear-gradient(135deg, theme('colors.primary') 0%, #ff8a8a 100%);
                transition: all 0.3s ease;
            }
            .btn-ripple:hover {
                background: linear-gradient(135deg, #ff5252 0%, theme('colors.primary') 100%);
                box-shadow: 0 10px 30px rgba(255, 107, 107, 0.4);
                transform: translateY(-2px);
            }
            /* 镂空按钮hover效果（红色） */
            .outline-btn {
                position: relative;
                overflow: hidden;
                transition: all 0.3s ease;
                background: transparent;
                border: 2px solid theme('colors.primary');
                color: theme('colors.primary');
            }
            .outline-btn:hover {
                background: theme('colors.primary');
                color: white;
                box-shadow: 0 8px 25px rgba(255, 107, 107, 0.3);
                transform: translateY(-2px);
            }

            /* 导航hover增强（红色下划线） */
            [data-page] {
                position: relative;
                transition: all 0.3s ease;
            }
            [data-page]:not(.nav-active):hover::after {
                content: '';
                position: absolute;
                bottom: -4px;
                left: 0;
                width: 100%;
                height: 2px;
                background: theme('colors.primary');
                transform: scaleX(1);
                transition: transform 0.3s ease;
            }
            [data-page]:not(.nav-active)::after {
                content: '';
                position: absolute;
                bottom: -4px;
                left: 0;
                width: 100%;
                height: 2px;
                background: theme('colors.primary');
                transform: scaleX(0);
                transition: transform 0.3s ease;
            }

            #pageContainer {
                position: relative;
                height: 100%;
                width: 100%;
            }
            .page-section {
                height: 100vh;
                width: 100%;
                position: absolute;
                top: 0;
                left: 0;
                overflow: hidden;
                opacity: 0;
                transform: translateY(20px);
                pointer-events: none;
                transition: 
                    opacity 0.6s cubic-bezier(0.4, 0, 0.2, 1),
                    transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            }
            .page-section.active-page {
                opacity: 1;
                transform: translateY(0);
                pointer-events: auto;
            }
            /* 自定义滚动条 */
            ::-webkit-scrollbar { display: none; }
            
            /* 按钮水波纹效果增强 */
            .btn-ripple:after {
                content: "";
                position: absolute;
                top: 50%;
                left: 50%;
                width: 0;
                height: 0;
                background: rgba(255,255,255,0.3);
                border-radius: 50%;
                transform: translate(-50%, -50%);
                transition: width 0.8s ease, height 0.8s ease;
            }
            .btn-ripple:hover:after {
                width: 400px;
                height: 400px;
            }

            /* 水面Canvas样式（红色波纹） */
            #waterCanvas {
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                z-index: 0;
                pointer-events: none;
                opacity: 0.8;
            }

            /* 图片放大模态框样式优化 */
            .modal-overlay {
                position: fixed;
                top: 0;
                left: 0;
                width: 100vw;
                height: 100vh;
                background: rgba(0, 0, 0, 0.95);
                z-index: 9999;
                display: flex;
                align-items: center;
                justify-content: center;
                opacity: 0;
                visibility: hidden;
                transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
                padding: 2rem;
                cursor: none;
            }
            .modal-overlay.active {
                opacity: 1;
                visibility: visible;
            }
            .modal-content {
                max-width: 90vw;
                max-height: 90vh;
                display: flex;
                flex-direction: column;
                gap: 1.5rem;
                position: relative;
                transform: translateY(20px);
                transition: transform 0.4s cubic-bezier(0.25, 1, 0.5, 1);
                opacity: 0;
            }
            .modal-overlay.active .modal-content {
                transform: translateY(0);
                opacity: 1;
            }
            @media (min-width: 768px) {
                .modal-content {
                    flex-direction: row;
                    max-width: 80vw;
                    gap: 2rem;
                }
            }
            .modal-img-container {
                flex: 2;
                display: flex;
                align-items: center;
                justify-content: center;
                cursor: none;
            }
            .modal-img {
                max-width: 100%;
                max-height: 80vh;
                border-radius: 12px;
                box-shadow: 0 15px 50px rgba(0,0,0,0.4);
                animation: imgScale 0.6s cubic-bezier(0.25, 1, 0.5, 1);
                transition: all 0.3s ease;
                cursor: zoom-in; /* 提示可放大 */
            }
            .modal-img:hover {
                transform: scale(1.02);
            }
            .modal-info {
                flex: 1;
                min-width: 300px;
                color: white;
                padding: 1rem;
                animation: fadeIn 0.6s cubic-bezier(0.25, 1, 0.5, 1);
            }
            .modal-close {
                position: absolute;
                top: -2rem;
                right: -1rem;
                color: white;
                font-size: 2rem;
                cursor: none;
                transition: color 0.3s ease, transform 0.3s ease;
                z-index: 10;
            }
            .modal-close:hover {
                color: theme('colors.primary');
                transform: rotate(90deg) scale(1.2);
            }
            .modal-info h3 {
                font-size: 1.8rem;
                font-weight: bold;
                color: theme('colors.primary');
                margin-bottom: 1rem;
            }
            .modal-info .category {
                font-size: 1rem;
                color: #ccc;
                margin-bottom: 1.5rem;
                display: inline-block;
                border: 1px solid #444;
                padding: 0.3rem 0.8rem;
                border-radius: 20px;
                transition: border-color 0.3s ease;
            }
            .modal-info:hover .category {
                border-color: theme('colors.primary');
            }
            .modal-info .description {
                line-height: 1.8;
                margin-bottom: 2rem;
                color: #eee;
            }
            .modal-info .detail-item {
                display: flex;
                align-items: center;
                gap: 0.8rem;
                margin-bottom: 1rem;
                color: #ddd;
                transition: color 0.3s ease;
            }
            .modal-info .detail-item:hover {
                color: white;
            }
            .modal-info .detail-item i {
                color: theme('colors.primary');
                font-size: 1.2rem;
                transition: transform 0.3s ease;
            }
            .modal-info .detail-item:hover i {
                transform: scale(1.2) rotate(5deg);
            }

            /* 新增：全屏查看图片样式 */
            .fullscreen-overlay {
                position: fixed;
                top: 0;
                left: 0;
                width: 100vw;
                height: 100vh;
                background: rgba(0, 0, 0, 0.98);
                z-index: 99999; /* 层级高于所有元素 */
                display: flex;
                align-items: center;
                justify-content: center;
                opacity: 0;
                visibility: hidden;
                transition: all 0.3s cubic-bezier(0.25, 1, 0.5, 1);
                cursor: none;
                padding: 1rem;
            }
            .fullscreen-overlay.active {
                opacity: 1;
                visibility: visible;
            }
            .fullscreen-img {
                max-width: 95vw;
                max-height: 95vh;
                object-fit: contain; /* 确保完整显示图片 */
                animation: imgScale 0.5s cubic-bezier(0.25, 1, 0.5, 1);
                cursor: zoom-out; /* 提示可缩小 */
            }
            .fullscreen-close {
                position: fixed;
                top: 2rem;
                right: 2rem;
                color: white;
                font-size: 2.5rem;
                z-index: 999999;
                transition: all 0.3s ease;
                cursor: none;
            }
            .fullscreen-close:hover {
                color: theme('colors.primary');
                transform: rotate(90deg) scale(1.2);
            }
        }
    </style>
</head>
<body class="bg-white text-secondary font-sans antialiased">
    <!-- 自定义光标元素 -->
    <div class="custom-cursor"></div>
    <div class="cursor-follower"></div>

    <!-- 导航栏 -->
    <nav id="navbar" class="fixed w-full z-50 transition-all duration-500 bg-white/80 backdrop-blur-md shadow-none">
        <div class="container mx-auto px-4 md:px-8 py-5 flex justify-between items-center">
            <a href="#" class="text-2xl font-bold text-primary tracking-tight cursor-pointer hover:cursor-none">CR Design</a>
            <!-- 桌面端导航 -->
            <div class="hidden md:flex space-x-10 text-lg font-medium font-heiti">
                <a href="#home" class="nav-active hover:text-primary transition-colors duration-300 cursor-pointer hover:cursor-none" data-page="0">首页</a>
                <a href="#about" class="hover:text-primary transition-colors duration-300 cursor-pointer hover:cursor-none" data-page="1">关于我</a>
                <a href="#portfolio" class="hover:text-primary transition-colors duration-300 cursor-pointer hover:cursor-none" data-page="2">作品集</a>
                <a href="#contact" class="hover:text-primary transition-colors duration-300 cursor-pointer hover:cursor-none" data-page="3">联系</a>
            </div>
            <!-- 移动端菜单按钮 -->
            <button id="menuBtn" class="md:hidden text-xl text-secondary cursor-pointer hover:cursor-none">
                <i class="fa fa-bars"></i>
            </button>
        </div>
        <!-- 移动端导航菜单 -->
        <div id="mobileMenu" class="hidden md:hidden bg-white/95 backdrop-blur-md shadow-lg absolute w-full">
            <div class="container mx-auto px-4 py-4 flex flex-col space-y-4 text-lg font-medium font-heiti">
                <a href="#home" class="py-3 nav-active hover:text-primary transition-colors duration-300 cursor-pointer hover:cursor-none" data-page="0">首页</a>
                <a href="#about" class="py-3 hover:text-primary transition-colors duration-300 cursor-pointer hover:cursor-none" data-page="1">关于我</a>
                <a href="#portfolio" class="py-3 hover:text-primary transition-colors duration-300 cursor-pointer hover:cursor-none" data-page="2">作品集</a>
                <a href="#contact" class="py-3 hover:text-primary transition-colors duration-300 cursor-pointer hover:cursor-none" data-page="3">联系</a>
            </div>
        </div>
    </nav>

    <!-- 翻页容器（保留功能，仅移除文字描述） -->
    <div id="pageContainer" class="h-full w-full">
        <!-- 首页 -->
        <section id="home" class="page-section flex items-center justify-center bg-gradient-to-br from-[#fafbfc] to-[#eef2f5]">
            <!-- 水面波纹Canvas -->
            <canvas id="waterCanvas"></canvas>
            
            <!-- 核心视觉内容 -->
            <div class="container mx-auto px-4 md:px-12 lg:px-20 z-10 text-center">
                <p class="text-primary font-medium text-sm md:text-base tracking-widest uppercase mb-6 animate-fade-in">
                    Visual Design & Creative Thinking
                </p>
                <h1 class="text-[clamp(3.5rem,10vw,6.5rem)] font-bold leading-none text-secondary text-shadow-lg mb-8 animate-slide-up">
                    创意<br class="md:hidden">
                    <span class="text-primary animate-text-pulse">设计</span>
                    <span class="text-secondary/90">无界</span>
                </h1>
                <p class="text-secondary/70 text-lg md:text-xl max-w-2xl mx-auto mb-12 leading-relaxed animate-slide-up" style="animation-delay: 0.2s;">
                    以视觉语言传递价值，用创意思维解决问题<br class="md:hidden">
                    专注平面设计、品牌视觉、UI/UX 与插画创作
                </p>
                <div class="flex flex-col sm:flex-row justify-center gap-4 md:gap-6 animate-slide-up" style="animation-delay: 0.4s;">
                    <a href="#portfolio" class="btn-ripple px-8 py-4 text-white rounded-lg font-medium shadow-lg hover:shadow-xl transform hover:-translate-y-1 cursor-pointer hover:cursor-none" data-page="2">
                        浏览作品集 <i class="fa fa-arrow-right ml-2"></i>
                    </a>
                    <a href="#about" class="outline-btn px-8 py-4 bg-white/60 backdrop-blur-sm text-secondary border border-secondary/10 rounded-lg font-medium hover:bg-white/80 transition-all duration-300 hover:shadow-md transform hover:-translate-y-1 cursor-pointer hover:cursor-none" data-page="1">
                        了解我的故事
                    </a>
                </div>
            </div>

            <!-- 翻页提示（保留功能，仅移除文字描述） -->
            <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 z-10 animate-bounce">
                <button class="text-secondary/40 hover:text-primary transition-colors duration-300 cursor-pointer hover:cursor-none" id="nextPageBtn">
                    <i class="fa fa-chevron-down text-xl"></i>
                </button>
            </div>
        </section>

        <!-- 关于我 -->
        <section id="about" class="page-section py-20 bg-white">
            <div class="container mx-auto px-4 md:px-8 h-full flex flex-col justify-center animate-page-fade">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.8rem,5vw,2.5rem)] font-bold">关于我</h2>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                </div>
                <div class="flex flex-col md:flex-row items-start gap-8 md:gap-12 w-full max-w-6xl mx-auto">
                    <div class="w-full md:w-[35%] flex-shrink-0">
                        <div class="relative hover-scale w-full h-auto cursor-pointer hover:cursor-none">
                            <!-- 替换的图片位置：个人照片 -->
                            <img src="https://i.postimg.cc/65459gSL/wei-xin-tu-pian-20251215212031-97-100.jpg" alt="个人照片" class="w-full h-auto rounded-lg shadow-xl object-cover">
                            <div class="absolute inset-0 bg-primary/20 rounded-lg mix-blend-overlay"></div>
                        </div>
                    </div>
                    <div class="w-full md:w-[65%] flex flex-col justify-start">
                        <!-- 关键修改处：删除了「学生」二字 -->
                        <h3 class="text-2xl font-bold mb-4">CR | 设计专业</h3>
                        <p class="text-secondary/80 mb-6 leading-relaxed">
                            现就读于苏州大学视觉传达设计专业，擅长将创意理念转化为视觉作品，注重细节与作品表达。
                            目前正在系统学习各类设计知识与技能，持续打磨设计基础能力及审美素养，积极参与校内实践项目以积累经验，
                            热爱探索不同风格的设计表达形式，致力于用设计解决实际问题、传递真实情感。
                        </p>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6 mb-8">
                            <div class="bg-neutral p-6 rounded-lg shadow-sm hover:shadow-lg transition-all duration-300 cursor-pointer hover:cursor-none">
                                <h4 class="font-bold text-lg mb-2 flex items-center">
                                    <i class="fa fa-graduation-cap text-primary mr-2"></i> 教育背景
                                </h4>
                                <p>苏州大学 | 视觉传达设计专业 | 在读</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm hover:shadow-lg transition-all duration-300 cursor-pointer hover:cursor-none">
                                <h4 class="font-bold text-lg mb-2 flex items-center">
                                    <i class="fa fa-puzzle-piece text-primary mr-2"></i> 核心技能
                                </h4>
                                <p>PS/AI/Figma/InDesign/Procreate | 平面/品牌/UI/插画设计</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm hover:shadow-lg transition-all duration-300 cursor-pointer hover:cursor-none">
                                <h4 class="font-bold text-lg mb-2 flex items-center">
                                    <i class="fa fa-lightbulb-o text-primary mr-2"></i> 设计理念
                                </h4>
                                <p>以细节见真章，以表达传情感，用设计语言解决问题、传递温度。</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm hover:shadow-lg transition-all duration-300 cursor-pointer hover:cursor-none">
                                <h4 class="font-bold text-lg mb-2 flex items-center">
                                    <i class="fa fa-paint-brush text-primary mr-2"></i> 学习方向
                                </h4>
                                <p>视觉传达 | 平面设计 | 品牌视觉 | 设计基础 | 审美培养</p>
                            </div>
                        </div>
                        <a href="你的简历链接" target="_blank" class="inline-flex items-center px-6 py-3 bg-secondary text-white rounded-lg hover:bg-secondary/90 transition-colors cursor-pointer hover:cursor-none">
                            <i class="fa fa-download mr-2"></i> 下载简历
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- 作品集 - 优化工具名称后的核心内容 -->
        <section id="portfolio" class="page-section py-20 bg-neutral">
            <div class="container mx-auto px-4 md:px-8 h-full flex flex-col justify-center animate-page-fade">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.8rem,5vw,2.5rem)] font-bold">作品集</h2>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                    <p class="mt-4 text-secondary/80 max-w-2xl mx-auto">
                        精选近期设计作品，涵盖平面、品牌、UI等多个领域，记录我的设计成长
                    </p>
                </div>
                <div class="flex flex-wrap justify-center gap-4 mb-12">
                    <button class="filter-btn active px-6 py-2 rounded-full bg-primary text-white cursor-pointer hover:cursor-none" data-filter="all">全部</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors cursor-pointer hover:cursor-none" data-filter="graphic">平面设计</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors cursor-pointer hover:cursor-none" data-filter="brand">品牌视觉</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors cursor-pointer hover:cursor-none" data-filter="ui">UI设计</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors cursor-pointer hover:cursor-none" data-filter="illustration">插画</button>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- 作品1 - 桂花特写 | 自然摄影（优化工具） -->
                    <div class="portfolio-item hover-scale cursor-pointer hover:cursor-none" 
                         data-category="graphic"
                         data-title="桂花特写 | 自然摄影"
                         data-img="https://i.postimg.cc/8ccK8q1y/wei-xin-tu-pian-20251124200020-48-2.jpg"
                         data-desc="这组桂花特写摄影作品聚焦于生活中的自然景致，通过精准的对焦与光影捕捉，展现桂花花瓣的细腻纹理与自然姿态。摒弃繁杂构图，以极简的视觉语言突出自然本身的美感，记录日常中易被忽略的自然之美，让平凡的生活瞬间成为视觉焦点。"
                         data-tools="全画幅单反相机（50mm F1.8定焦镜头）、三脚架、Adobe Lightroom Classic、Adobe Photoshop（细节精修）"
                         data-type="自然摄影">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://i.postimg.cc/8ccK8q1y/wei-xin-tu-pian-20251124200020-48-2.jpg" alt="桂花特写 | 自然摄影" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">桂花特写 | 自然摄影</h3>
                                <p class="text-white/80 mt-2">生活中的自然景致特写</p>
                                <a href="javascript:void(0)" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品2 - 一树桂花 | 自然摄影（优化工具） -->
                    <div class="portfolio-item hover-scale cursor-pointer hover:cursor-none" 
                         data-category="graphic"
                         data-title="一树桂花 | 自然摄影"
                         data-img="https://i.postimg.cc/nhGPDKwz/wei-xin-tu-pian-20251124200021-49-2.jpg"
                         data-desc="这组一树桂花的摄影作品以整体视角记录生活中的自然景致，捕捉桂花满树的繁茂姿态与光影层次。通过自然光线的运用，展现桂花树的整体轮廓与枝叶间桂花的错落美感，用镜头留存日常中桂花盛放的美好瞬间，还原自然本真的视觉体验。"
                         data-tools="全画幅单反相机（24-70mm F2.8变焦镜头）、遮光罩（防眩光）、Adobe Lightroom Classic（光影调色）、Adobe Camera Raw"
                         data-type="自然摄影">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://i.postimg.cc/nhGPDKwz/wei-xin-tu-pian-20251124200021-49-2.jpg" alt="一树桂花 | 自然摄影" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">一树桂花 | 自然摄影</h3>
                                <p class="text-white/80 mt-2">生活中的自然景致记录</p>
                                <a href="javascript:void(0)" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品3 - 夕阳景致 | 生活摄影（优化工具） -->
                    <div class="portfolio-item hover-scale cursor-pointer hover:cursor-none" 
                         data-category="graphic"
                         data-title="夕阳景致 | 生活摄影"
                         data-img="https://i.postimg.cc/zfPpCxwH/wei-xin-tu-pian-20251209221622-81-100.jpg"
                         data-desc="这组夕阳景色摄影作品聚焦于生活中的傍晚风景，捕捉日落时分天空与自然环境交织的唯美瞬间。通过对光线、色彩与构图的精准把控，记录日常中易被忽略的傍晚景致，用镜头留存夕阳的温暖与治愈，展现平凡生活中的自然之美。"
                         data-tools="微单相机（16-55mm F2.8镜头）、渐变灰滤镜（平衡光比）、Adobe Lightroom Classic（色温校准）、Adobe Photoshop（暗部细节提升）"
                         data-type="生活摄影">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://i.postimg.cc/zfPpCxwH/wei-xin-tu-pian-20251209221622-81-100.jpg" alt="夕阳景致 | 生活摄影" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">夕阳景致 | 生活摄影</h3>
                                <p class="text-white/80 mt-2">生活中的傍晚风景记录</p>
                                <a href="javascript:void(0)" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品4 - 空中的云 | 自然摄影（优化工具） -->
                    <div class="portfolio-item hover-scale cursor-pointer hover:cursor-none" 
                         data-category="graphic"
                         data-title="空中的云 | 自然摄影"
                         data-img="https://i.postimg.cc/R03wB4f9/wei-xin-tu-pian-20251209221831-83-100.jpg"
                         data-desc="这组空中的云摄影作品聚焦于生活中易被忽略的自然景色特写，捕捉云层在不同光线、不同时段下的形态与色彩变化。通过极简的构图与精准的曝光控制，展现云朵的轻盈质感与自然韵律，用镜头定格天空中瞬息万变的自然之美，记录日常里的诗意瞬间。"
                         data-tools="微单相机（24-105mm F4镜头）、快门线（减少抖动）、Adobe Lightroom Classic（曝光微调）、Adobe Photoshop（杂色去除）"
                         data-type="自然摄影">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://i.postimg.cc/R03wB4f9/wei-xin-tu-pian-20251209221831-83-100.jpg" alt="空中的云 | 自然摄影" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">空中的云 | 自然摄影</h3>
                                <p class="text-white/80 mt-2">生活中的自然景色特写</p>
                                <a href="javascript:void(0)" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品5 - 路边的树 | 自然摄影（优化工具） -->
                    <div class="portfolio-item hover-scale cursor-pointer hover:cursor-none" 
                         data-category="graphic"
                         data-title="路边的树 | 自然摄影"
                         data-img="https://i.postimg.cc/ZKT3qr3j/wei-xin-tu-pian-20251215212107-98-100.jpg"
                         data-desc="这组路边的树摄影作品是对生活中自然景色的随拍记录，捕捉树木在日常环境中的自然姿态与光影变化。以简约的构图展现树木的原生美感，记录平凡生活中易被忽略的自然景致，传递自然与日常交融的视觉温度。"
                         data-tools="便携微单相机（35mm F1.4定焦镜头）、便携摄影包、Adobe Lightroom Classic（快速调色）、Snapseed（移动端初修）"
                         data-type="自然摄影">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://i.postimg.cc/ZKT3qr3j/wei-xin-tu-pian-20251215212107-98-100.jpg" alt="路边的树 | 自然摄影" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">路边的树 | 自然摄影</h3>
                                <p class="text-white/80 mt-2">生活中的自然景色随拍</p>
                                <a href="javascript:void(0)" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品6 - 质感表达 | 设计基础练习（优化手绘工具） -->
                    <div class="portfolio-item hover-scale cursor-pointer hover:cursor-none" 
                         data-category="graphic"
                         data-title="质感表达 | 设计基础练习"
                         data-img="https://i.postimg.cc/4NnR60Tk/wei-xin-tu-pian-20251210132449-84-100.jpg"
                         data-desc="本次设计基础练习作业聚焦于手绘质感表达，以彩铅、马克笔、素描纸为核心创作工具，通过不同手绘技法探索各类材质的视觉与触觉特征。从基础的线条轻重、叠色层次、笔触肌理入手，练习如何通过手绘方式还原金属、布料、木质等不同材质的质感表现，重点打磨手绘控笔能力、光影层次感与材质细节刻画能力，夯实设计手绘基础。"
                         data-tools="水溶性彩铅（辉柏嘉48色）、酒精性马克笔（Touch mark 60色）、80g细纹素描纸、2B/4B铅笔（起稿）、橡皮（樱花软橡皮）、高光笔（三菱）、纸笔（揉擦质感）"
                         data-type="手绘质感练习">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://i.postimg.cc/4NnR60Tk/wei-xin-tu-pian-20251210132449-84-100.jpg" alt="质感表达 | 设计基础练习" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">质感表达 | 设计基础练习</h3>
                                <p class="text-white/80 mt-2">设计基础 - 手绘质感表现练习</p>
                                <a href="javascript:void(0)" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="text-center mt-16">
                    <button class="outline-btn px-8 py-3 border-2 border-primary text-primary rounded-lg font-medium hover:bg-primary hover:text-white transition-colors cursor-pointer hover:cursor-none">
                        加载更多作品
                    </button>
                </div>
            </div>
        </section>

        <!-- 联系方式（已修改邮箱） -->
        <section id="contact" class="page-section py-20 bg-neutral text-secondary">
            <div class="container mx-auto px-4 md:px-8 h-full flex flex-col justify-center animate-page-fade">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.8rem,5vw,2.5rem)] font-bold">联系我</h2>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                    <p class="mt-4 text-secondary/80 max-w-2xl mx-auto">
                        欢迎合作、交流或咨询，期待与你一起创造更多可能
                    </p>
                </div>
                <div class="max-w-4xl mx-auto">
                    <div class="text-center mb-8">
                        <div class="inline-flex flex-col md:flex-row items-start md:items-center gap-8 justify-center">
                            <!-- 👇 此处为修改后的邮箱地址 -->
                            <div class="flex items-center justify-center cursor-pointer hover:cursor-none">
                                <div class="bg-primary/10 p-4 rounded-full mr-4 transition-all duration-300 hover:bg-primary/20 hover:scale-110">
                                    <i class="fa fa-envelope text-primary text-xl"></i>
                                </div>
                                <div class="text-left">
                                    <h4 class="text-xl font-bold mb-1">邮箱</h4>
                                    <p class="text-secondary/80">cr19962886585@163.com</p>
                                </div>
                            </div>
                            <div class="flex items-center justify-center cursor-pointer hover:cursor-none">
                                <div class="bg-primary/10 p-4 rounded-full mr-4 transition-all duration-300 hover:bg-primary/20 hover:scale-110">
                                    <i class="fa fa-phone text-primary text-xl"></i>
                                </div>
                                <div class="text-left">
                                    <h4 class="text-xl font-bold mb-1">电话</h4>
                                    <p class="text-secondary/80">19962886666</p>
                                </div>
                            </div>
                            <div class="flex items-center justify-center cursor-pointer hover:cursor-none">
                                <div class="bg-primary/10 p-4 rounded-full mr-4 transition-all duration-300 hover:bg-primary/20 hover:scale-110">
                                    <i class="fa fa-map-marker text-primary text-xl"></i>
                                </div>
                                <div class="text-left">
                                    <h4 class="text-xl font-bold mb-1">所在地</h4>
                                    <p class="text-secondary/80">苏州</p>
                                </div>
                            </div>
                        </div>
                        <div class="mt-8">
                            <h4 class="text-xl font-bold mb-4">社交平台</h4>
                            <div class="flex justify-center space-x-6 mt-2">
                                <a href="#" target="_blank" class="text-secondary/80 hover:text-primary transition-colors text-2xl cursor-pointer hover:cursor-none hover:scale-125">
                                    <i class="fa fa-behance"></i>
                                </a>
                                <a href="#" target="_blank" class="text-secondary/80 hover:text-primary transition-colors text-2xl cursor-pointer hover:cursor-none hover:scale-125">
                                    <i class="fa fa-weibo"></i>
                                </a>
                                <a href="#" target="_blank" class="text-secondary/80 hover:text-primary transition-colors text-2xl cursor-pointer hover:cursor-none hover:scale-125">
                                    <i class="fa fa-github"></i>
                                </a>
                                <a href="#" target="_blank" class="text-secondary/80 hover:text-primary transition-colors text-2xl cursor-pointer hover:cursor-none hover:scale-125">
                                    <i class="fa fa-weixin"></i>
                                </a>
                            </div>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-sm max-w-5xl mx-auto">
                        <form class="flex flex-wrap justify-center items-end gap-4">
                            <div class="w-full sm:w-auto">
                                <label for="name" class="block text-secondary/80 mb-2 text-sm">姓名</label>
                                <input type="text" id="name" class="w-full sm:w-48 px-3 py-2 rounded-lg bg-neutral border border-secondary/20 text-secondary placeholder-secondary/50 focus:outline-none focus:border-primary text-sm transition-all duration-300 hover:border-primary/50" placeholder="你的姓名">
                            </div>
                            <div class="w-full sm:w-auto">
                                <label for="email" class="block text-secondary/80 mb-2 text-sm">邮箱</label>
                                <input type="email" id="email" class="w-full sm:w-48 px-3 py-2 rounded-lg bg-neutral border border-secondary/20 text-secondary placeholder-secondary/50 focus:outline-none focus:border-primary text-sm transition-all duration-300 hover:border-primary/50" placeholder="你的邮箱">
                            </div>
                            <div class="w-full sm:w-auto">
                                <label for="message" class="block text-secondary/80 mb-2 text-sm">留言</label>
                                <input type="text" id="message" class="w-full sm:w-64 px-3 py-2 rounded-lg bg-neutral border border-secondary/20 text-secondary placeholder-secondary/50 focus:outline-none focus:border-primary text-sm transition-all duration-300 hover:border-primary/50" placeholder="简短留言">
                            </div>
                            <div class="w-full sm:w-auto">
                                <button type="submit" class="w-full sm:w-28 py-2 bg-primary text-white rounded-lg font-medium hover:bg-primary/90 transition-colors shadow-sm text-sm cursor-pointer hover:cursor-none hover:shadow-md">
                                    发送留言
                                </button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- 图片放大模态框 -->
    <div class="modal-overlay" id="portfolioModal">
        <div class="modal-content">
            <span class="modal-close" id="modalClose"><i class="fa fa-times"></i></span>
            <div class="modal-img-container">
                <img src="" alt="作品详情图" class="modal-img" id="modalImg">
            </div>
            <div class="modal-info" id="modalInfo">
                <h3 id="modalTitle"></h3>
                <span class="category" id="modalCategory"></span>
                <p class="description" id="modalDesc"></p>
                <div class="detail-item">
                    <i class="fa fa-pencil"></i>
                    <span>使用工具：<span id="modalTools"></span></span>
                </div>
                <div class="detail-item">
                    <i class="fa fa-tag"></i>
                    <span>作品类型：<span id="modalType"></span></span>
                </div>
            </div>
        </div>
    </div>

    <!-- 新增：全屏查看图片容器 -->
    <div class="fullscreen-overlay" id="fullscreenOverlay">
        <img src="" alt="全屏作品图" class="fullscreen-img" id="fullscreenImg">
        <span class="fullscreen-close" id="fullscreenClose"><i class="fa fa-times"></i></span>
    </div>

    <!-- JS部分 -->
    <script>
        // 水面波纹效果核心代码
        class WaterRipple {
            constructor(canvas) {
                this.canvas = canvas;
                this.ctx = canvas.getContext('2d');
                this.width = window.innerWidth;
                this.height = window.innerHeight;
                this.canvas.width = this.width;
                this.canvas.height = this.height;
                this.ripples = [];
                this.lastTime = 0;
                this.isRunning = false;

                this.init();
            }

            init() {
                window.addEventListener('mousemove', (e) => {
                    this.createRipple(e.clientX, e.clientY);
                });
                window.addEventListener('resize', () => {
                    this.width = window.innerWidth;
                    this.height = window.innerHeight;
                    this.canvas.width = this.width;
                    this.canvas.height = this.height;
                });
                this.animate();
            }

            createRipple(x, y) {
                this.ripples.push({
                    x: x,
                    y: y,
                    radius: 5,
                    maxRadius: Math.max(this.width, this.height) / 2,
                    opacity: 0.5,
                    speed: 3,
                    decay: 0.005,
                    color: 'rgba(255, 107, 107, {opacity})'
                });
            }

            drawRipples(timestamp) {
                this.ctx.clearRect(0, 0, this.width, this.height);
                
                const bgGradient = this.ctx.createLinearGradient(0, 0, this.width, this.height);
                bgGradient.addColorStop(0, 'rgba(250, 251, 252, 0)');
                bgGradient.addColorStop(1, 'rgba(238, 242, 245, 0)');
                this.ctx.fillStyle = bgGradient;
                this.ctx.fillRect(0, 0, this.width, this.height);

                for (let i = this.ripples.length - 1; i >= 0; i--) {
                    const ripple = this.ripples[i];
                    
                    ripple.radius += ripple.speed;
                    ripple.opacity -= ripple.decay;
                    
                    if (ripple.radius > ripple.maxRadius || ripple.opacity <= 0) {
                        this.ripples.splice(i, 1);
                        continue;
                    }

                    this.ctx.beginPath();
                    this.ctx.arc(ripple.x, ripple.y, ripple.radius, 0, Math.PI * 2);
                    this.ctx.strokeStyle = ripple.color.replace('{opacity}', ripple.opacity);
                    this.ctx.lineWidth = 1.5;
                    this.ctx.stroke();

                    this.ctx.beginPath();
                    this.ctx.arc(ripple.x, ripple.y, ripple.radius / 2, 0, Math.PI * 2);
                    this.ctx.strokeStyle = `rgba(42, 59, 76, ${ripple.opacity * 0.6})`;
                    this.ctx.lineWidth = 0.8;
                    this.ctx.stroke();
                }
            }

            animate(timestamp = 0) {
                const deltaTime = timestamp - this.lastTime;
                this.lastTime = timestamp;

                if (deltaTime > 16) {
                    this.drawRipples(timestamp);
                }

                requestAnimationFrame((time) => this.animate(time));
            }
        }

        // 自定义光标跟随逻辑
        function initCustomCursor() {
            const cursor = document.querySelector('.custom-cursor');
            const follower = document.querySelector('.cursor-follower');
            const hoverElements = document.querySelectorAll('.portfolio-item, .btn-ripple, .outline-btn, [data-page], .filter-btn, .modal-close, #menuBtn, #nextPageBtn, .detail-item, a, button, input, .modal-img, .fullscreen-close, .fullscreen-img');
            
            window.addEventListener('mousemove', (e) => {
                const moveCursor = () => {
                    cursor.style.left = `${e.clientX - cursor.offsetWidth / 2}px`;
                    cursor.style.top = `${e.clientY - cursor.offsetHeight / 2}px`;
                    
                    follower.style.left = `${e.clientX - follower.offsetWidth / 2}px`;
                    follower.style.top = `${e.clientY - follower.offsetHeight / 2}px`;
                };
                requestAnimationFrame(moveCursor);
            });

            hoverElements.forEach(el => {
                el.addEventListener('mouseenter', () => {
                    document.body.classList.add('cursor-hovered');
                });
                el.addEventListener('mouseleave', () => {
                    document.body.classList.remove('cursor-hovered');
                });
            });

            window.addEventListener('mouseleave', () => {
                cursor.style.opacity = '0';
                follower.style.opacity = '0';
            });
            window.addEventListener('mouseenter', () => {
                cursor.style.opacity = '0.5'; // 同步修改为0.5
                follower.style.opacity = '0.3'; // 同步修改为0.3
            });
        }

        // 初始化页面
        window.addEventListener('DOMContentLoaded', () => {
            // 初始化水面波纹
            const waterCanvas = document.getElementById('waterCanvas');
            if (waterCanvas) {
                new WaterRipple(waterCanvas);
            }

            // 初始化自定义光标
            initCustomCursor();

            // 翻页逻辑（保留功能，仅移除文字描述）
            const pageContainer = document.getElementById('pageContainer');
            const sections = document.querySelectorAll('.page-section');
            const navLinks = document.querySelectorAll('[data-page]');
            const nextPageBtn = document.getElementById('nextPageBtn');
            let currentPage = 0;
            const totalPages = sections.length;
            let isAnimating = false;

            // 移动端菜单
            const menuBtn = document.getElementById('menuBtn');
            const mobileMenu = document.getElementById('mobileMenu');
            menuBtn.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
                menuBtn.innerHTML = mobileMenu.classList.contains('hidden') ? '<i class="fa fa-bars"></i>' : '<i class="fa fa-times"></i>';
            });

            // 导航栏样式初始化
            const navbar = document.getElementById('navbar');
            navbar.classList.add('py-2');

            // 翻页核心函数（保留功能，仅移除文字描述）
            function goToPage(pageNum) {
                if (pageNum < 0 || pageNum >= totalPages || isAnimating) return;
                isAnimating = true;

                sections[currentPage].classList.remove('active-page');
                
                setTimeout(() => {
                    sections[pageNum].classList.add('active-page');
                    
                    navLinks.forEach(link => {
                        link.classList.remove('nav-active');
                        if (Number(link.dataset.page) === pageNum) {
                            link.classList.add('nav-active');
                        }
                    });

                    currentPage = pageNum;

                    if (pageNum === 1 || pageNum === 2) {
                        navbar.classList.add('opacity-0', 'pointer-events-none');
                        navbar.classList.remove('bg-white/80', 'bg-white/95', 'shadow-md', 'shadow-none');
                    } else {
                        navbar.classList.remove('opacity-0', 'pointer-events-none');
                        if (pageNum === 0) {
                            navbar.classList.remove('bg-white/95', 'shadow-md');
                            navbar.classList.add('bg-white/80', 'shadow-none');
                        } else {
                            navbar.classList.remove('bg-white/80', 'shadow-none');
                            navbar.classList.add('bg-white/95', 'shadow-md');
                        }
                    }

                    setTimeout(() => {
                        isAnimating = false;
                    }, 600);
                }, 300);
            }

            // 导航点击
            navLinks.forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    const targetPage = Number(link.dataset.page);
                    goToPage(targetPage);
                    if (!mobileMenu.classList.contains('hidden')) {
                        mobileMenu.classList.add('hidden');
                        menuBtn.innerHTML = '<i class="fa fa-bars"></i>';
                    }
                });
            });

            // 滚轮翻页
            window.addEventListener('wheel', (e) => {
                if (isAnimating) return;
                const direction = e.deltaY > 0 ? 1 : -1;
                goToPage(currentPage + direction);
            });

            // 键盘翻页
            window.addEventListener('keydown', (e) => {
                if (isAnimating) return;
                if (e.key === 'ArrowDown' || e.key === 'PageDown') {
                    goToPage(currentPage + 1);
                } else if (e.key === 'ArrowUp' || e.key === 'PageUp') {
                    goToPage(currentPage - 1);
                }
            });

            // 下一页按钮
            nextPageBtn.addEventListener('click', () => {
                goToPage(currentPage + 1);
            });

            // 作品集筛选
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

            // 作品集图片放大模态框逻辑 + 新增全屏查看逻辑
            const portfolioModal = document.getElementById('portfolioModal');
            const modalClose = document.getElementById('modalClose');
            const modalImg = document.getElementById('modalImg');
            const modalTitle = document.getElementById('modalTitle');
            const modalCategory = document.getElementById('modalCategory');
            const modalDesc = document.getElementById('modalDesc');
            const modalTools = document.getElementById('modalTools');
            const modalType = document.getElementById('modalType');

            // 全屏相关元素
            const fullscreenOverlay = document.getElementById('fullscreenOverlay');
            const fullscreenImg = document.getElementById('fullscreenImg');
            const fullscreenClose = document.getElementById('fullscreenClose');
            let currentImgSrc = ''; // 存储当前图片地址

            // 打开普通模态框
            function openModal(item) {
                currentImgSrc = item.dataset.img; // 保存原图地址
                modalImg.src = currentImgSrc;
                modalImg.alt = item.dataset.title;
                modalTitle.textContent = item.dataset.title;
                modalCategory.textContent = item.dataset.category === 'graphic' ? '平面设计' : 
                                            item.dataset.category === 'brand' ? '品牌视觉' :
                                            item.dataset.category === 'ui' ? 'UI设计' : '插画设计';
                modalDesc.textContent = item.dataset.desc;
                modalTools.textContent = item.dataset.tools;
                modalType.textContent = item.dataset.type;
                
                portfolioModal.classList.add('active');
                document.body.style.overflow = 'hidden';
            }

            // 关闭普通模态框
            function closeModal() {
                portfolioModal.classList.remove('active');
                document.body.style.overflow = 'auto';
            }

            // 打开全屏查看
            function openFullscreen() {
                fullscreenImg.src = currentImgSrc; // 加载原图
                fullscreenImg.alt = modalTitle.textContent;
                fullscreenOverlay.classList.add('active');
            }

            // 关闭全屏查看
            function closeFullscreen() {
                fullscreenOverlay.classList.remove('active');
            }

            // 作品项点击打开普通模态框
            portfolioItems.forEach(item => {
                item.addEventListener('click', () => {
                    openModal(item);
                });
            });

            // 模态框内图片点击打开全屏
            modalImg.addEventListener('click', (e) => {
                e.stopPropagation(); // 防止触发模态框关闭
                openFullscreen();
            });

            // 全屏图片点击关闭全屏
            fullscreenImg.addEventListener('click', (e) => {
                e.stopPropagation();
                closeFullscreen();
            });

            // 关闭按钮事件
            modalClose.addEventListener('click', closeModal);
            fullscreenClose.addEventListener('click', closeFullscreen);

            // 点击空白处关闭
            portfolioModal.addEventListener('click', (e) => {
                if (e.target === portfolioModal) {
                    closeModal();
                }
            });
            fullscreenOverlay.addEventListener('click', (e) => {
                if (e.target === fullscreenOverlay) {
                    closeFullscreen();
                }
            });

            // ESC键关闭
            window.addEventListener('keydown', (e) => {
                if (e.key === 'Escape') {
                    if (fullscreenOverlay.classList.contains('active')) {
                        closeFullscreen();
                    } else if (portfolioModal.classList.contains('active')) {
                        closeModal();
                    }
                }
            });

            // 初始化页面
            sections[0].classList.add('active-page');
            navLinks.forEach(link => {
                if (Number(link.dataset.page) === 0) {
                    link.classList.add('nav-active');
                }
            });
            navbar.classList.remove('opacity-0', 'pointer-events-none');
            navbar.classList.add('bg-white/80', 'shadow-none', 'py-2');
        });
    </script>
</body>
</html>
