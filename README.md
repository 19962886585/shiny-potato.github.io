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
    <!-- 导航栏（固定顶部） -->
    <nav id="navbar" class="fixed w-full z-50 transition-all duration-300 bg-white/90 backdrop-blur-sm shadow-sm">
        <div class="container mx-auto px-4 md:px-8 py-4 flex justify-between items-center">
            <a href="#" class="text-2xl font-bold text-primary">CR Design</a>
            <!-- 桌面端导航 -->
            <div class="hidden md:flex space-x-8 text-lg">
                <a href="#home" class="nav-active hover:text-primary transition-colors" data-page="0">首页</a>
                <a href="#about" class="hover:text-primary transition-colors" data-page="1">关于我</a>
                <a href="#portfolio" class="hover:text-primary transition-colors" data-page="2">作品集</a>
                <a href="#skills" class="hover:text-primary transition-colors" data-page="3">技能</a>
                <a href="#contact" class="hover:text-primary transition-colors" data-page="4">联系</a>
            </div>
            <!-- 移动端菜单按钮 -->
            <button id="menuBtn" class="md:hidden text-2xl">
                <i class="fa fa-bars"></i>
            </button>
        </div>
        <!-- 移动端导航菜单 -->
        <div id="mobileMenu" class="hidden md:hidden bg-white shadow-lg absolute w-full">
            <div class="container mx-auto px-4 py-4 flex flex-col space-y-4 text-lg">
                <a href="#home" class="py-2 nav-active hover:text-primary transition-colors" data-page="0">首页</a>
                <a href="#about" class="py-2 hover:text-primary transition-colors" data-page="1">关于我</a>
                <a href="#portfolio" class="py-2 hover:text-primary transition-colors" data-page="2">作品集</a>
                <a href="#skills" class="py-2 hover:text-primary transition-colors" data-page="3">技能</a>
                <a href="#contact" class="py-2 hover:text-primary transition-colors" data-page="4">联系</a>
            </div>
        </div>
    </nav>

    <!-- 翻页容器（核心） -->
    <div id="pageContainer" class="h-full w-full">
        <!-- 首页（第0页） -->
        <section id="home" class="page-section flex items-end bg-gradient-to-r from-[#E9ECEF] to-[#F8F9FA] pb-16 md:pb-24">
            <div class="absolute inset-0 z-0">
                <div class="absolute top-20 left-10 w-32 h-32 rounded-full bg-primary/10 blur-2xl"></div>
                <div class="absolute bottom-20 right-10 w-48 h-48 rounded-full bg-secondary/10 blur-2xl"></div>
            </div>
            
            <!-- 左侧竖排文字 -->
            <div class="absolute left-4 md:left-10 top-1/2 transform -translate-y-1/2 z-10 animate-fade-in">
                <h1 class="vertical-text text-[clamp(3rem,10vw,5rem)] font-bold text-shadow text-secondary/90">
                    设计
                </h1>
            </div>

            <!-- 底部核心文案 -->
            <div class="container mx-auto px-4 md:px-16 lg:px-24 z-10 text-center w-full animate-page-fade">
                <h2 class="text-[clamp(2rem,7vw,4rem)] font-bold leading-tight text-shadow animate-fade-in">
                    <span class="text-primary">创意无限</span>
                </h2>
                <p class="mt-6 text-[clamp(1rem,3vw,1.25rem)] text-secondary/80 max-w-2xl mx-auto animate-slide-up">
                    专注平面设计、UI/UX、品牌视觉、插画创作，用设计传递价值与美感
                </p>
                <div class="mt-10 flex flex-col sm:flex-row justify-center gap-4 animate-slide-up">
                    <a href="#portfolio" class="px-8 py-3 bg-primary text-white rounded-full font-medium hover:bg-primary/90 transition-colors shadow-lg" data-page="2">
                        查看作品集
                    </a>
                    <a href="#contact" class="px-8 py-3 border-2 border-secondary text-secondary rounded-full font-medium hover:bg-secondary hover:text-white transition-colors" data-page="4">
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

        <!-- 关于我（第1页）【核心修改区域】 -->
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
                            <img src="https://picsum.photos/id/64/600/800" alt="个人照片" class="w-full h-auto rounded-lg shadow-xl object-cover">
                            <div class="absolute inset-0 bg-primary/20 rounded-lg mix-blend-overlay"></div>
                        </div>
                    </div>
                    <!-- 个人信息（修改后的内容） -->
                    <div class="w-full md:w-2/3">
                        <h3 class="text-2xl font-bold mb-4">CR | 设计专业学生</h3>
                        <p class="text-secondary/80 mb-6 leading-relaxed">
                            现就读于苏州大学视觉传达设计专业，擅长将创意理念转化为视觉作品，注重细节与作品表达。
                            目前正在系统学习各类设计知识与技能，持续打磨设计基础能力及审美素养，积极参与校内实践项目以积累经验，
                            热爱探索不同风格的设计表达形式，致力于用设计解决实际问题、传递真实情感。
                        </p>
                        <!-- 核心信息卡片（适配修改） -->
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6 mb-8">
                            <div class="bg-neutral p-6 rounded-lg shadow-sm">
                                <h4 class="font-bold text-lg mb-2 flex items-center">
                                    <i class="fa fa-graduation-cap text-primary mr-2"></i> 教育背景
                                </h4>
                                <p>苏州大学 | 视觉传达设计专业 | 在读</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm">
                                <h4 class="font-bold text-lg mb-2 flex items-center">
                                    <i class="fa fa-trophy text-primary mr-2"></i> 实践经历
                                </h4>
                                <p>参与校内设计项目 | 探索多元设计风格 | 积累实战经验</p>
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
                    <!-- 作品1 -->
                    <div class="portfolio-item hover-scale" data-category="graphic">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/20/600/400" alt="平面设计作品" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">杂志排版设计</h3>
                                <p class="text-white/80 mt-2">基于极简风格的时尚杂志内页排版</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品2 -->
                    <div class="portfolio-item hover-scale" data-category="brand">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/42/600/400" alt="品牌视觉作品" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">咖啡品牌视觉系统</h3>
                                <p class="text-white/80 mt-2">LOGO设计、包装设计、宣传物料全套</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品3 -->
                    <div class="portfolio-item hover-scale" data-category="ui">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/96/600/400" alt="UI设计作品" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">健身APP界面设计</h3>
                                <p class="text-white/80 mt-2">运动记录、课程预约功能UI/UX设计</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品4 -->
                    <div class="portfolio-item hover-scale" data-category="illustration">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/65/600/400" alt="插画作品" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">城市印象插画集</h3>
                                <p class="text-white/80 mt-2">以扁平化风格绘制的城市地标系列</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品5 -->
                    <div class="portfolio-item hover-scale" data-category="graphic">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/26/600/400" alt="平面设计作品" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">音乐节海报设计</h3>
                                <p class="text-white/80 mt-2">结合动态元素的潮流音乐节宣传海报</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 作品6 -->
                    <div class="portfolio-item hover-scale" data-category="brand">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://picsum.photos/id/48/600/400" alt="品牌视觉作品" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
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
                    <button class="px-8 py-3 border-2 border-primary text-primary rounded-full font-medium hover:bg-primary hover:text-white transition-colors">
                        加载更多作品
                    </button>
                </div>
            </div>
        </section>

        <!-- 专业技能（第3页） -->
        <section id="skills" class="page-section py-20 bg-white hidden">
            <div class="container mx-auto px-4 md:px-8 h-full flex flex-col justify-center animate-page-fade">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.8rem,5vw,2.5rem)] font-bold">专业技能</h2>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                    <p class="mt-4 text-secondary/80 max-w-2xl mx-auto">
                        熟练掌握设计工具与专业技能，为创意落地提供技术支撑
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
                    <!-- 软件技能 -->
                    <div>
                        <h3 class="text-2xl font-bold mb-8 flex items-center">
                            <i class="fa fa-desktop text-primary mr-3"></i> 软件技能
                        </h3>
                        <div class="space-y-6">
                            <div>
                                <div class="flex justify-between mb-2">
                                    <span class="font-medium">Photoshop</span>
                                    <span>95%</span>
                                </div>
                                <div class="w-full h-3 bg-neutral rounded-full overflow-hidden">
                                    <div class="h-full bg-primary rounded-full" style="width: 95%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between mb-2">
                                    <span class="font-medium">Illustrator</span>
                                    <span>90%</span>
                                </div>
                                <div class="w-full h-3 bg-neutral rounded-full overflow-hidden">
                                    <div class="h-full bg-primary rounded-full" style="width: 90%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between mb-2">
                                    <span class="font-medium">Figma（UI/UX）</span>
                                    <span>85%</span>
                                </div>
                                <div class="w-full h-3 bg-neutral rounded-full overflow-hidden">
                                    <div class="h-full bg-primary rounded-full" style="width: 85%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between mb-2">
                                    <span class="font-medium">InDesign（排版）</span>
                                    <span>88%</span>
                                </div>
                                <div class="w-full h-3 bg-neutral rounded-full overflow-hidden">
                                    <div class="h-full bg-primary rounded-full" style="width: 88%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between mb-2">
                                    <span class="font-medium">Procreate</span>
                                    <span>82%</span>
                                </div>
                                <div class="w-full h-3 bg-neutral rounded-full overflow-hidden">
                                    <div class="h-full bg-primary rounded-full" style="width: 82%"></div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- 专业能力 -->
                    <div>
                        <h3 class="text-2xl font-bold mb-8 flex items-center">
                            <i class="fa fa-puzzle-piece text-primary mr-3"></i> 专业能力
                        </h3>
                        <div class="grid grid-cols-2 gap-4">
                            <div class="bg-neutral p-6 rounded-lg shadow-sm hover:shadow-md transition-shadow">
                                <div class="text-primary text-3xl mb-4">
                                    <i class="fa fa-file-image-o"></i>
                                </div>
                                <h4 class="font-bold text-lg mb-2">平面设计</h4>
                                <p class="text-secondary/80">海报、宣传单、画册、包装设计等</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm hover:shadow-md transition-shadow">
                                <div class="text-primary text-3xl mb-4">
                                    <i class="fa fa-star"></i>
                                </div>
                                <h4 class="font-bold text-lg mb-2">品牌视觉</h4>
                                <p class="text-secondary/80">LOGO设计、VI系统、品牌推广物料</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm hover:shadow-md transition-shadow">
                                <div class="text-primary text-3xl mb-4">
                                    <i class="fa fa-mobile"></i>
                                </div>
                                <h4 class="font-bold text-lg mb-2">UI/UX设计</h4>
                                <p class="text-secondary/80">APP界面、网页设计、用户体验优化</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm hover:shadow-md transition-shadow">
                                <div class="text-primary text-3xl mb-4">
                                    <i class="fa fa-paint-brush"></i>
                                </div>
                                <h4 class="font-bold text-lg mb-2">插画创作</h4>
                                <p class="text-secondary/80">扁平化、肌理风、商业插画等</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm hover:shadow-md transition-shadow">
                                <div class="text-primary text-3xl mb-4">
                                    <i class="fa fa-font"></i>
                                </div>
                                <h4 class="font-bold text-lg mb-2">排版设计</h4>
                                <p class="text-secondary/80">杂志、书籍、海报排版，字体设计</p>
                            </div>
                            <div class="bg-neutral p-6 rounded-lg shadow-sm hover:shadow-md transition-shadow">
                                <div class="text-primary text-3xl mb-4">
                                    <i class="fa fa-lightbulb-o"></i>
                                </div>
                                <h4 class="font-bold text-lg mb-2">创意策划</h4>
                                <p class="text-secondary/80">设计概念构思、主题策划、落地执行</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 联系方式（第4页） -->
        <section id="contact" class="page-section py-20 bg-secondary text-white hidden">
            <div class="container mx-auto px-4 md:px-8 h-full flex flex-col justify-center animate-page-fade">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.8rem,5vw,2.5rem)] font-bold">联系我</h2>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                    <p class="mt-4 text-white/80 max-w-2xl mx-auto">
                        欢迎合作、交流或咨询，期待与你一起创造更多可能
                    </p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-12">
                    <!-- 联系信息 -->
                    <div>
                        <div class="space-y-8">
                            <div class="flex items-start">
                                <div class="bg-primary/20 p-4 rounded-full mr-4">
                                    <i class="fa fa-envelope text-primary text-xl"></i>
                                </div>
                                <div>
                                    <h4 class="text-xl font-bold mb-2">邮箱</h4>
                                    <p class="text-white/80">xxx@xxx.com（替换为你的邮箱）</p>
                                </div>
                            </div>
                            <div class="flex items-start">
                                <div class="bg-primary/20 p-4 rounded-full mr-4">
                                    <i class="fa fa-phone text-primary text-xl"></i>
                                </div>
                                <div>
                                    <h4 class="text-xl font-bold mb-2">电话</h4>
                                    <p class="text-white/80">138xxxx8888（替换为你的电话）</p>
                                </div>
                            </div>
                            <div class="flex items-start">
                                <div class="bg-primary/20 p-4 rounded-full mr-4">
                                    <i class="fa fa-map-marker text-primary text-xl"></i>
                                </div>
                                <div>
                                    <h4 class="text-xl font-bold mb-2">所在地</h4>
                                    <p class="text-white/80">苏州（替换为你的所在地）</p>
                                </div>
                            </div>
                            <div class="flex items-start">
                                <div class="bg-primary/20 p-4 rounded-full mr-4">
                                    <i class="fa fa-globe text-primary text-xl"></i>
                                </div>
                                <div>
                                    <h4 class="text-xl font-bold mb-2">社交平台</h4>
                                    <div class="flex space-x-4 mt-2">
                                        <a href="#" target="_blank" class="text-white/80 hover:text-primary transition-colors">
                                            <i class="fa fa-behance text-xl"></i>
                                        </a>
                                        <a href="#" target="_blank" class="text-white/80 hover:text-primary transition-colors">
                                            <i class="fa fa-weibo text-xl"></i>
                                        </a>
                                        <a href="#" target="_blank" class="text-white/80 hover:text-primary transition-colors">
                                            <i class="fa fa-github text-xl"></i>
                                        </a>
                                        <a href="#" target="_blank" class="text-white/80 hover:text-primary transition-colors">
                                            <i class="fa fa-weixin text-xl"></i>
                                        </a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- 联系表单 -->
                    <div>
                        <form class="bg-white/10 backdrop-blur-sm p-8 rounded-lg">
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-6 mb-6">
                                <div>
                                    <label for="name" class="block text-white/80 mb-2">姓名</label>
                                    <input type="text" id="name" class="w-full px-4 py-3 rounded-lg bg-white/20 border border-white/30 text-white placeholder-white/50 focus:outline-none focus:border-primary" placeholder="请输入你的姓名">
                                </div>
                                <div>
                                    <label for="email" class="block text-white/80 mb-2">邮箱</label>
                                    <input type="email" id="email" class="w-full px-4 py-3 rounded-lg bg-white/20 border border-white/30 text-white placeholder-white/50 focus:outline-none focus:border-primary" placeholder="请输入你的邮箱">
                                </div>
                            </div>
                            <div class="mb-6">
                                <label for="subject" class="block text-white/80 mb-2">主题</label>
                                <input type="text" id="subject" class="w-full px-4 py-3 rounded-lg bg-white/20 border border-white/30 text-white placeholder-white/50 focus:outline-none focus:border-primary" placeholder="请输入咨询主题">
                            </div>
                            <div class="mb-8">
                                <label for="message" class="block text-white/80 mb-2">留言</label>
                                <textarea id="message" rows="4" class="w-full px-4 py-3 rounded-lg bg-white/20 border border-white/30 text-white placeholder-white/50 focus:outline-none focus:border-primary" placeholder="请输入你的留言内容"></textarea>
                            </div>
                            <button type="submit" class="w-full py-3 bg-primary text-white rounded-lg font-medium hover:bg-primary/90 transition-colors">
                                发送留言
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- 页脚（翻页模式下固定在底部） -->
    <footer class="fixed bottom-0 w-full py-4 bg-secondary/90 text-white z-40">
        <div class="container mx-auto px-4 md:px-8">
            <div class="flex flex-col md:flex-row justify-between items-center">
                <div class="mb-2 md:mb-0">
                    <p class="text-white/60 text-sm">&copy; 2024 CR Design. 保留所有权利。</p>
                </div>
                <div class="flex space-x-4 text-sm">
                    <a href="#home" class="text-white/60 hover:text-primary transition-colors" data-page="0">首页</a>
                    <a href="#about" class="text-white/60 hover:text-primary transition-colors" data-page="1">关于我</a>
                    <a href="#portfolio" class="text-white/60 hover:text-primary transition-colors" data-page="2">作品集</a>
                    <a href="#skills" class="text-white/60 hover:text-primary transition-colors" data-page="3">技能</a>
                    <a href="#contact" class="text-white/60 hover:text-primary transition-colors" data-page="4">联系</a>
                </div>
            </div>
        </div>
    </footer>

    <!-- 翻页模式核心JS -->
    <script>
        // 全局变量
        const pageContainer = document.getElementById('pageContainer');
        const sections = document.querySelectorAll('.page-section');
        const navLinks = document.querySelectorAll('[data-page]');
        const nextPageBtn = document.getElementById('nextPageBtn');
        let currentPage = 0; // 当前页码（从0开始）
        const totalPages = sections.length;
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

        // 8. 作品集筛选功能（保留原有逻辑）
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
