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
                        // 新增：定义黑体字体家族
                        heiti: ['SimHei', '黑体', 'Microsoft YaHei', 'sans-serif'],
                    },
                    animation: {
                        'fade-in': 'fadeIn 0.8s ease-in-out',
                        'slide-up': 'slideUp 1s ease-out',
                        'page-fade': 'pageFade 0.5s ease-in-out',
                        'text-pulse': 'textPulse 3s ease-in-out infinite',
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
            /* 自定义滚动条（参考站风格） */
            ::-webkit-scrollbar { display: none; }
            /* 按钮水波纹效果 */
            .btn-ripple {
                position: relative;
                overflow: hidden;
            }
            .btn-ripple:after {
                content: "";
                position: absolute;
                top: 50%;
                left: 50%;
                width: 0;
                height: 0;
                background: rgba(255,255,255,0.2);
                border-radius: 50%;
                transform: translate(-50%, -50%);
                transition: width 0.6s ease, height 0.6s ease;
            }
            .btn-ripple:hover:after {
                width: 300px;
                height: 300px;
            }
            /* 水面Canvas样式 */
            #waterCanvas {
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                z-index: 0;
                pointer-events: none; /* 不阻挡鼠标事件 */
                opacity: 0.8;
            }
        }
    </style>
</head>
<body class="bg-white text-secondary font-sans antialiased">
    <!-- 导航栏（优化透明度，贴近参考站极简风格） -->
    <nav id="navbar" class="fixed w-full z-50 transition-all duration-500 bg-white/80 backdrop-blur-md shadow-none">
        <div class="container mx-auto px-4 md:px-8 py-5 flex justify-between items-center">
            <a href="#" class="text-2xl font-bold text-primary tracking-tight">CR Design</a>
            <!-- 桌面端导航（简化间距和样式）- 新增font-heiti类应用黑体 -->
            <div class="hidden md:flex space-x-10 text-lg font-medium font-heiti">
                <a href="#home" class="nav-active hover:text-primary transition-colors duration-300" data-page="0">首页</a>
                <a href="#about" class="hover:text-primary transition-colors duration-300" data-page="1">关于我</a>
                <a href="#portfolio" class="hover:text-primary transition-colors duration-300" data-page="2">作品集</a>
                <a href="#contact" class="hover:text-primary transition-colors duration-300" data-page="3">联系</a>
            </div>
            <!-- 移动端菜单按钮（简化样式） -->
            <button id="menuBtn" class="md:hidden text-xl text-secondary">
                <i class="fa fa-bars"></i>
            </button>
        </div>
        <!-- 移动端导航菜单（优化样式）- 新增font-heiti类应用黑体 -->
        <div id="mobileMenu" class="hidden md:hidden bg-white/95 backdrop-blur-md shadow-lg absolute w-full">
            <div class="container mx-auto px-4 py-4 flex flex-col space-y-4 text-lg font-medium font-heiti">
                <a href="#home" class="py-3 nav-active hover:text-primary transition-colors duration-300" data-page="0">首页</a>
                <a href="#about" class="py-3 hover:text-primary transition-colors duration-300" data-page="1">关于我</a>
                <a href="#portfolio" class="py-3 hover:text-primary transition-colors duration-300" data-page="2">作品集</a>
                <a href="#contact" class="py-3 hover:text-primary transition-colors duration-300" data-page="3">联系</a>
            </div>
        </div>
    </nav>

    <!-- 翻页容器 -->
    <div id="pageContainer" class="h-full w-full">
        <!-- 首页（核心优化：水面波纹背景） -->
        <section id="home" class="page-section flex items-center justify-center bg-gradient-to-br from-[#fafbfc] to-[#eef2f5]">
            <!-- 水面波纹Canvas（核心新增） -->
            <canvas id="waterCanvas"></canvas>
            
            <!-- 核心视觉内容（居中布局，参考站层级感） -->
            <div class="container mx-auto px-4 md:px-12 lg:px-20 z-10 text-center">
                <!-- 顶部小字标签（参考站引导文案） -->
                <p class="text-primary font-medium text-sm md:text-base tracking-widest uppercase mb-6 animate-fade-in">
                    Visual Design & Creative Thinking
                </p>
                
                <!-- 主标题（超大字号+精简文案，参考站视觉焦点） -->
                <h1 class="text-[clamp(3.5rem,10vw,6.5rem)] font-bold leading-none text-secondary text-shadow-lg mb-8 animate-slide-up">
                    创意<br class="md:hidden">
                    <span class="text-primary animate-text-pulse">设计</span>
                    <span class="text-secondary/90">无界</span>
                </h1>
                
                <!-- 副标题（精简+高质感） -->
                <p class="text-secondary/70 text-lg md:text-xl max-w-2xl mx-auto mb-12 leading-relaxed animate-slide-up" style="animation-delay: 0.2s;">
                    以视觉语言传递价值，用创意思维解决问题<br class="md:hidden">
                    专注平面设计、品牌视觉、UI/UX 与插画创作
                </p>
                
                <!-- 按钮组（参考站精致按钮风格） -->
                <div class="flex flex-col sm:flex-row justify-center gap-4 md:gap-6 animate-slide-up" style="animation-delay: 0.4s;">
                    <a href="#portfolio" class="btn-ripple px-8 py-4 bg-primary text-white rounded-lg font-medium shadow-lg hover:bg-primary/95 transition-all duration-300 hover:shadow-xl transform hover:-translate-y-1" data-page="2">
                        浏览作品集 <i class="fa fa-arrow-right ml-2"></i>
                    </a>
                    <a href="#about" class="btn-ripple px-8 py-4 bg-white/60 backdrop-blur-sm text-secondary border border-secondary/10 rounded-lg font-medium hover:bg-white/80 transition-all duration-300 hover:shadow-md transform hover:-translate-y-1" data-page="1">
                        了解我的故事
                    </a>
                </div>
            </div>

            <!-- 翻页提示（简化样式，参考站低调引导） -->
            <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 z-10 animate-bounce">
                <button class="text-secondary/40 hover:text-primary transition-colors duration-300" id="nextPageBtn">
                    <i class="fa fa-chevron-down text-xl"></i>
                </button>
            </div>
        </section>

        <!-- 关于我（保持原有优化后的并列布局） -->
        <section id="about" class="page-section py-20 bg-white hidden">
            <div class="container mx-auto px-4 md:px-8 h-full flex flex-col justify-center animate-page-fade">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.8rem,5vw,2.5rem)] font-bold">关于我</h2>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                </div>
                <div class="flex flex-col md:flex-row items-start gap-8 md:gap-12 w-full max-w-6xl mx-auto">
                    <div class="w-full md:w-[35%] flex-shrink-0">
                        <div class="relative hover-scale w-full h-auto">
                            <img src="https://i.postimg.cc/cLyW5WZ9/wei-xin-tu-pian-20251209201428-80-100.jpg" alt="个人照片" class="w-full h-auto rounded-lg shadow-xl object-cover">
                            <div class="absolute inset-0 bg-primary/20 rounded-lg mix-blend-overlay"></div>
                        </div>
                    </div>
                    <div class="w-full md:w-[65%] flex flex-col justify-start">
                        <h3 class="text-2xl font-bold mb-4">CR | 设计专业</h3>
                        <p class="text-secondary/80 mb-6 leading-relaxed">
                            现就读于苏州大学视觉传达设计专业，擅长将创意理念转化为视觉作品，注重细节与作品表达。
                            目前正在系统学习各类设计知识与技能，持续打磨设计基础能力及审美素养，积极参与校内实践项目以积累经验，
                            热爱探索不同风格的设计表达形式，致力于用设计解决实际问题、传递真实情感。
                        </p>
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
                        <a href="你的简历链接" target="_blank" class="inline-flex items-center px-6 py-3 bg-secondary text-white rounded-lg hover:bg-secondary/90 transition-colors">
                            <i class="fa fa-download mr-2"></i> 下载简历
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- 作品集（核心修改：替换图片链接） -->
        <section id="portfolio" class="page-section py-20 bg-neutral hidden">
            <div class="container mx-auto px-4 md:px-8 h-full flex flex-col justify-center animate-page-fade">
                <div class="text-center mb-16">
                    <h2 class="text-[clamp(1.8rem,5vw,2.5rem)] font-bold">作品集</h2>
                    <div class="w-20 h-1 bg-primary mx-auto mt-4"></div>
                    <p class="mt-4 text-secondary/80 max-w-2xl mx-auto">
                        精选近期设计作品，涵盖平面、品牌、UI等多个领域，记录我的设计成长
                    </p>
                </div>
                <div class="flex flex-wrap justify-center gap-4 mb-12">
                    <button class="filter-btn active px-6 py-2 rounded-full bg-primary text-white" data-filter="all">全部</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors" data-filter="graphic">平面设计</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors" data-filter="brand">品牌视觉</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors" data-filter="ui">UI设计</button>
                    <button class="filter-btn px-6 py-2 rounded-full bg-white text-secondary hover:bg-primary hover:text-white transition-colors" data-filter="illustration">插画</button>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- 替换第1张图片 -->
                    <div class="portfolio-item hover-scale" data-category="graphic">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://i.postimg.cc/63vdMBYx/wei-xin-tu-pian-20251124200021-49-2.jpg" alt="设计作品1" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">设计作品1</h3>
                                <p class="text-white/80 mt-2">基于极简风格的设计创作</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 替换第2张图片 -->
                    <div class="portfolio-item hover-scale" data-category="brand">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://i.postimg.cc/pVC8MKZz/wei-xin-tu-pian-20251124200020-48-2.jpg" alt="设计作品2" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">设计作品2</h3>
                                <p class="text-white/80 mt-2">品牌视觉系统设计</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 替换第3张图片 -->
                    <div class="portfolio-item hover-scale" data-category="ui">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://i.postimg.cc/W11cfc4f/wei-xin-tu-pian-20251209221622-81-100.jpg" alt="设计作品3" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">设计作品3</h3>
                                <p class="text-white/80 mt-2">UI/UX界面设计</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 替换第4张图片 -->
                    <div class="portfolio-item hover-scale" data-category="illustration">
                        <div class="relative overflow-hidden rounded-lg shadow-lg">
                            <img src="https://i.postimg.cc/ZRZcV4T7/wei-xin-tu-pian-20251209221717-82-100.jpg" alt="设计作品4" class="w-full h-64 object-cover transition-transform duration-500 hover:scale-110">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent opacity-0 hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                                <h3 class="text-white text-xl font-bold">设计作品4</h3>
                                <p class="text-white/80 mt-2">创意插画设计</p>
                                <a href="#" class="mt-4 inline-block text-primary hover:text-white transition-colors">查看详情 <i class="fa fa-arrow-right ml-1"></i></a>
                            </div>
                        </div>
                    </div>
                    <!-- 保留原有2个占位项（可根据需要替换/删除） -->
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
                <div class="text-center mt-16">
                    <button class="px-8 py-3 border-2 border-primary text-primary rounded-lg font-medium hover:bg-primary hover:text-white transition-colors">
                        加载更多作品
                    </button>
                </div>
            </div>
        </section>

        <!-- 联系方式（保持原有） -->
        <section id="contact" class="page-section py-20 bg-neutral text-secondary hidden">
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
                            <div class="flex items-center justify-center">
                                <div class="bg-primary/10 p-4 rounded-full mr-4">
                                    <i class="fa fa-envelope text-primary text-xl"></i>
                                </div>
                                <div class="text-left">
                                    <h4 class="text-xl font-bold mb-1">邮箱</h4>
                                    <p class="text-secondary/80">2622558252@qq.com</p>
                                </div>
                            </div>
                            <div class="flex items-center justify-center">
                                <div class="bg-primary/10 p-4 rounded-full mr-4">
                                    <i class="fa fa-phone text-primary text-xl"></i>
                                </div>
                                <div class="text-left">
                                    <h4 class="text-xl font-bold mb-1">电话</h4>
                                    <p class="text-secondary/80">19962886585</p>
                                </div>
                            </div>
                            <div class="flex items-center justify-center">
                                <div class="bg-primary/10 p-4 rounded-full mr-4">
                                    <i class="fa fa-map-marker text-primary text-xl"></i>
                                </div>
                                <div class="text-left">
                                    <h4 class="text-xl font-bold mb-1">所在地</h4>
                                    <p class="text-secondary/80">苏州大学</p>
                                </div>
                            </div>
                        </div>
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

    <!-- JS部分（新增水面波纹动画 + 原有逻辑 + 导航栏隐藏逻辑） -->
    <script>
        // ===================== 水面波纹效果核心代码 =====================
        class WaterRipple {
            constructor(canvas) {
                this.canvas = canvas;
                this.ctx = canvas.getContext('2d');
                this.width = window.innerWidth;
                this.height = window.innerHeight;
                this.canvas.width = this.width;
                this.canvas.height = this.height;
                this.ripples = []; // 存储波纹
                this.lastTime = 0;
                this.isRunning = false;

                // 初始化
                this.init();
            }

            // 初始化
            init() {
                // 监听鼠标移动
                window.addEventListener('mousemove', (e) => {
                    this.createRipple(e.clientX, e.clientY);
                });
                // 监听窗口大小变化
                window.addEventListener('resize', () => {
                    this.width = window.innerWidth;
                    this.height = window.innerHeight;
                    this.canvas.width = this.width;
                    this.canvas.height = this.height;
                });
                // 启动动画
                this.animate();
            }

            // 创建波纹
            createRipple(x, y) {
                this.ripples.push({
                    x: x,
                    y: y,
                    radius: 5,
                    maxRadius: Math.max(this.width, this.height) / 2,
                    opacity: 0.5,
                    speed: 3,
                    decay: 0.005,
                    color: 'rgba(255, 107, 107, {opacity})' // 主色波纹
                });
            }

            // 绘制波纹
            drawRipples(timestamp) {
                // 清空画布（保留透明度）
                this.ctx.clearRect(0, 0, this.width, this.height);
                
                // 绘制渐变背景（和页面背景融合）
                const bgGradient = this.ctx.createLinearGradient(0, 0, this.width, this.height);
                bgGradient.addColorStop(0, 'rgba(250, 251, 252, 0)');
                bgGradient.addColorStop(1, 'rgba(238, 242, 245, 0)');
                this.ctx.fillStyle = bgGradient;
                this.ctx.fillRect(0, 0, this.width, this.height);

                // 绘制所有波纹
                for (let i = this.ripples.length - 1; i >= 0; i--) {
                    const ripple = this.ripples[i];
                    
                    // 更新波纹属性
                    ripple.radius += ripple.speed;
                    ripple.opacity -= ripple.decay;
                    
                    // 超出范围或透明度为0则移除
                    if (ripple.radius > ripple.maxRadius || ripple.opacity <= 0) {
                        this.ripples.splice(i, 1);
                        continue;
                    }

                    // 绘制波纹
                    this.ctx.beginPath();
                    this.ctx.arc(ripple.x, ripple.y, ripple.radius, 0, Math.PI * 2);
                    this.ctx.strokeStyle = ripple.color.replace('{opacity}', ripple.opacity);
                    this.ctx.lineWidth = 1.5;
                    this.ctx.stroke();

                    // 内层细波纹（增加层次感）
                    this.ctx.beginPath();
                    this.ctx.arc(ripple.x, ripple.y, ripple.radius / 2, 0, Math.PI * 2);
                    this.ctx.strokeStyle = `rgba(42, 59, 76, ${ripple.opacity * 0.6})`;
                    this.ctx.lineWidth = 0.8;
                    this.ctx.stroke();
                }
            }

            // 动画循环
            animate(timestamp = 0) {
                const deltaTime = timestamp - this.lastTime;
                this.lastTime = timestamp;

                if (deltaTime > 16) { // 约60fps
                    this.drawRipples(timestamp);
                }

                requestAnimationFrame((time) => this.animate(time));
            }
        }

        // 初始化水面波纹（仅在首页加载）
        window.addEventListener('DOMContentLoaded', () => {
            const waterCanvas = document.getElementById('waterCanvas');
            if (waterCanvas) {
                new WaterRipple(waterCanvas);
            }

            // ===================== 原有翻页逻辑 + 导航栏隐藏逻辑 =====================
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

            // 导航栏滚动效果（优化透明度）
            const navbar = document.getElementById('navbar');
            navbar.classList.add('py-2');

            // 翻页核心函数（修改：关于我(pageNum=1)和作品集(pageNum=2)都隐藏导航栏）
            function goToPage(pageNum) {
                if (pageNum < 0 || pageNum >= totalPages || isAnimating) return;
                isAnimating = true;

                sections.forEach((section, index) => {
                    section.classList.add('hidden');
                    if (index === pageNum) {
                        section.classList.remove('hidden');
                    }
                });

                navLinks.forEach(link => {
                    link.classList.remove('nav-active');
                    if (Number(link.dataset.page) === pageNum) {
                        link.classList.add('nav-active');
                    }
                });

                currentPage = pageNum;

                // ========== 核心修改：关于我(pageNum=1) + 作品集(pageNum=2) 隐藏导航栏 ==========
                if (pageNum === 1 || pageNum === 2) {
                    // 隐藏导航栏（平滑过渡）
                    navbar.classList.add('opacity-0', 'pointer-events-none');
                    navbar.classList.remove('bg-white/80', 'bg-white/95', 'shadow-md', 'shadow-none');
                } else {
                    // 显示导航栏并恢复对应样式
                    navbar.classList.remove('opacity-0', 'pointer-events-none');
                    if (pageNum === 0) { // 首页
                        navbar.classList.remove('bg-white/95', 'shadow-md');
                        navbar.classList.add('bg-white/80', 'shadow-none');
                    } else { // 联系页(pageNum=3)
                        navbar.classList.remove('bg-white/80', 'shadow-none');
                        navbar.classList.add('bg-white/95', 'shadow-md');
                    }
                }

                setTimeout(() => {
                    isAnimating = false;
                }, 600);
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

            // 初始化
            goToPage(0);
        });
    </script>
</body>
</html>
