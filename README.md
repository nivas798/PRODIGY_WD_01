<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NaviX | Ultra Interactive Navigation by Nivas Alugubelli</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    animation: {
                        'float': 'float 6s ease-in-out infinite',
                        'float-reverse': 'float 6s ease-in-out infinite reverse',
                        'pulse-slow': 'pulse 4s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                        'spin-slow': 'spin 8s linear infinite',
                        'blob': 'blob 12s ease-in-out infinite',
                        'gradient': 'gradient 8s ease infinite',
                        'text-gradient': 'text-gradient 4s ease infinite',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0)' },
                            '50%': { transform: 'translateY(-20px)' },
                        },
                        blob: {
                            '0%, 100%': { borderRadius: '60% 40% 30% 70%/60% 30% 70% 40%' },
                            '50%': { borderRadius: '30% 60% 70% 40%/50% 60% 30% 60%' },
                        },
                        gradient: {
                            '0%, 100%': { 'background-position': '0% 50%' },
                            '50%': { 'background-position': '100% 50%' },
                        },
                        'text-gradient': {
                            '0%, 100%': { 'background-position': 'left center' },
                            '50%': { 'background-position': 'right center' },
                        }
                    },
                    backdropBlur: {
                        'xl': '24px',
                    }
                }
            }
        }
    </script>
    <style>
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .animate-fade-in {
            animation: fadeIn 1s ease-out forwards;
        }
        
        .animation-delay-100 { animation-delay: 100ms; }
        .animation-delay-200 { animation-delay: 200ms; }
        .animation-delay-300 { animation-delay: 300ms; }
        .animation-delay-400 { animation-delay: 400ms; }
        .animation-delay-500 { animation-delay: 500ms; }
        .animation-delay-600 { animation-delay: 600ms; }
        .animation-delay-700 { animation-delay: 700ms; }
        .animation-delay-800 { animation-delay: 800ms; }
        .animation-delay-900 { animation-delay: 900ms; }
        .animation-delay-1000 { animation-delay: 1000ms; }
        
        .text-gradient-animated {
            background-size: 200% auto;
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: text-gradient 4s ease infinite;
        }
        
        .gradient-border {
            position: relative;
            border-radius: 1rem;
        }
        
        .gradient-border::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            border-radius: 1rem;
            padding: 2px;
            background: linear-gradient(45deg, #6366f1, #8b5cf6, #ec4899);
            -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
            -webkit-mask-composite: xor;
            mask-composite: exclude;
            animation: gradient 8s ease infinite;
            background-size: 200% 200%;
            z-index: -1;
        }
        
        .parallax-bg {
            background-attachment: fixed;
            background-position: center;
            background-repeat: no-repeat;
            background-size: cover;
        }
        
        .glass-card {
            backdrop-filter: blur(16px) saturate(180%);
            -webkit-backdrop-filter: blur(16px) saturate(180%);
            background-color: rgba(255, 255, 255, 0.75);
            border: 1px solid rgba(255, 255, 255, 0.125);
        }
        
        .hover-scale {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .hover-scale:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        }
        
        .nav-link-underline::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 0;
            height: 2px;
            background: currentColor;
            transition: width 0.3s ease;
        }
        
        .nav-link-underline:hover::after {
            width: 100%;
        }
        
        .page-transition {
            transition: opacity 0.5s ease, transform 0.5s ease;
        }
        
        .page-hidden {
            opacity: 0;
            transform: translateY(20px);
            pointer-events: none;
        }
        
        .page-visible {
            opacity: 1;
            transform: translateY(0);
            pointer-events: all;
        }
        
        .magnetic-effect {
            transition: transform 0.2s ease;
        }
        
        .magnetic-effect:hover {
            transform: scale(1.05);
        }
    </style>
</head>
<body class="bg-white text-gray-900 font-sans antialiased overflow-x-hidden">
    <!-- Preloader -->
    <div id="preloader" class="fixed inset-0 z-50 flex items-center justify-center bg-white transition-opacity duration-500">
        <div class="relative w-24 h-24">
            <div class="absolute inset-0 rounded-full border-4 border-transparent border-t-indigo-500 border-r-purple-500 animate-spin-slow"></div>
            <div class="absolute inset-2 rounded-full border-4 border-transparent border-b-pink-500 border-l-blue-500 animate-spin-slow reverse"></div>
            <div class="absolute inset-4 rounded-full border-4 border-transparent border-t-indigo-300 border-r-purple-300 animate-spin-slow"></div>
        </div>
    </div>

    <!-- Cursor Effects -->
    <div id="cursor" class="fixed w-8 h-8 rounded-full bg-indigo-500/20 pointer-events-none transform -translate-x-1/2 -translate-y-1/2 z-50 mix-blend-multiply backdrop-blur-sm transition-transform duration-100 ease-out"></div>
    <div id="cursor-follower" class="fixed w-4 h-4 rounded-full bg-indigo-500 pointer-events-none transform -translate-x-1/2 -translate-y-1/2 z-50 transition-all duration-300 ease-out"></div>

    <!-- Navigation -->
    <nav id="navigation" class="fixed top-0 left-0 right-0 z-40 transition-all duration-500 ease-in-out bg-transparent">
        <div class="max-w-7xl mx-auto px-6">
            <div class="flex justify-between items-center h-20">
                <!-- Logo -->
                <a href="#" onclick="showPage('home')" class="text-2xl font-bold text-gradient-animated bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500 hover:scale-105 transition-transform duration-300">
                    NaviX
                </a>

                <!-- Desktop Menu -->
                <div class="hidden lg:flex items-center space-x-1">
                    <a href="#" onclick="showPage('home')" class="nav-link relative px-5 py-2 rounded-full text-sm font-medium transition-all duration-300 group text-gray-700 hover:text-indigo-600">
                        <span class="relative z-10 flex items-center">
                            <span class="mr-2">🏠</span>
                            <span class="nav-link-underline">Home</span>
                        </span>
                        <span class="absolute inset-0 rounded-full bg-indigo-500/10 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></span>
                    </a>
                    <a href="#" onclick="showPage('about')" class="nav-link relative px-5 py-2 rounded-full text-sm font-medium transition-all duration-300 group text-gray-700 hover:text-purple-600">
                        <span class="relative z-10 flex items-center">
                            <span class="mr-2">👋</span>
                            <span class="nav-link-underline">About</span>
                        </span>
                        <span class="absolute inset-0 rounded-full bg-purple-500/10 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></span>
                    </a>
                    <a href="#" onclick="showPage('services')" class="nav-link relative px-5 py-2 rounded-full text-sm font-medium transition-all duration-300 group text-gray-700 hover:text-pink-600">
                        <span class="relative z-10 flex items-center">
                            <span class="mr-2">✨</span>
                            <span class="nav-link-underline">Services</span>
                        </span>
                        <span class="absolute inset-0 rounded-full bg-pink-500/10 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></span>
                    </a>
                    <a href="#" onclick="showPage('work')" class="nav-link relative px-5 py-2 rounded-full text-sm font-medium transition-all duration-300 group text-gray-700 hover:text-blue-600">
                        <span class="relative z-10 flex items-center">
                            <span class="mr-2">💼</span>
                            <span class="nav-link-underline">Work</span>
                        </span>
                        <span class="absolute inset-0 rounded-full bg-blue-500/10 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></span>
                    </a>
                    <a href="#" onclick="showPage('contact')" class="nav-link relative px-5 py-2 rounded-full text-sm font-medium transition-all duration-300 group text-white bg-gradient-to-r from-indigo-500 to-purple-600 hover:from-indigo-600 hover:to-purple-700 hover:shadow-lg">
                        <span class="relative z-10 flex items-center">
                            <span class="mr-2">📩</span>
                            <span>Contact</span>
                        </span>
                        <span class="absolute inset-0 rounded-full bg-white/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></span>
                    </a>
                </div>

                <!-- Mobile Menu Button -->
                <button onclick="toggleMobileMenu()" class="lg:hidden p-2 rounded-lg transition-all duration-300 text-gray-700 hover:bg-gray-100 focus:outline-none magnetic-effect">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
                    </svg>
                </button>
            </div>

            <!-- Mobile Menu -->
            <div id="mobileMenu" class="lg:hidden transition-all duration-300 ease-in-out overflow-hidden max-h-0 opacity-0">
                <div class="px-4 pt-2 pb-4 space-y-2 bg-white/95 backdrop-blur-xl rounded-xl mt-2 border border-gray-100 shadow-xl">
                    <a href="#" onclick="showPage('home'); toggleMobileMenu()" class="block px-4 py-3 rounded-lg text-base font-medium transition-all duration-300 text-gray-700 hover:text-indigo-600 hover:bg-indigo-50 flex items-center">
                        <span class="mr-3">🏠</span> Home
                    </a>
                    <a href="#" onclick="showPage('about'); toggleMobileMenu()" class="block px-4 py-3 rounded-lg text-base font-medium transition-all duration-300 text-gray-700 hover:text-purple-600 hover:bg-purple-50 flex items-center">
                        <span class="mr-3">👋</span> About
                    </a>
                    <a href="#" onclick="showPage('services'); toggleMobileMenu()" class="block px-4 py-3 rounded-lg text-base font-medium transition-all duration-300 text-gray-700 hover:text-pink-600 hover:bg-pink-50 flex items-center">
                        <span class="mr-3">✨</span> Services
                    </a>
                    <a href="#" onclick="showPage('work'); toggleMobileMenu()" class="block px-4 py-3 rounded-lg text-base font-medium transition-all duration-300 text-gray-700 hover:text-blue-600 hover:bg-blue-50 flex items-center">
                        <span class="mr-3">💼</span> Work
                    </a>
                    <a href="#" onclick="showPage('contact'); toggleMobileMenu()" class="block px-4 py-3 rounded-lg text-base font-medium transition-all duration-300 text-white bg-gradient-to-r from-indigo-500 to-purple-600 hover:from-indigo-600 hover:to-purple-700">
                        <span class="mr-3">📩</span> Contact
                    </a>
                </div>
            </div>
        </div>
    </nav>

    <!-- Home Page -->
    <div id="home" class="page-transition page-visible">
        <!-- Hero Section -->
        <section class="relative min-h-screen flex items-center justify-center overflow-hidden bg-gradient-to-br from-indigo-900 via-purple-900 to-gray-900">
            <!-- Animated background elements -->
            <div class="absolute inset-0 opacity-20">
                <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-indigo-500 rounded-full mix-blend-overlay filter blur-3xl opacity-70 animate-blob"></div>
                <div class="absolute top-1/3 right-1/4 w-96 h-96 bg-purple-500 rounded-full mix-blend-overlay filter blur-3xl opacity-70 animate-blob animation-delay-4000"></div>
                <div class="absolute bottom-1/4 left-1/3 w-96 h-96 bg-pink-500 rounded-full mix-blend-overlay filter blur-3xl opacity-70 animate-blob animation-delay-8000"></div>
            </div>
            
            <div class="relative z-10 text-center px-6 max-w-6xl mx-auto">
                <h1 class="text-5xl md:text-7xl font-bold text-white mb-8 leading-tight animate-fade-in">
                    <span class="inline-block">Ultra</span>
                    <span class="inline-block bg-gradient-to-r from-indigo-400 via-purple-400 to-pink-400 bg-clip-text text-transparent animate-text-gradient">
                        Interactive
                    </span>
                    <span class="inline-block">Navigation</span>
                </h1>
                <p class="text-xl md:text-2xl text-indigo-100 mb-10 leading-relaxed max-w-3xl mx-auto animate-fade-in animation-delay-300">
                    Experience the future of web navigation with fluid animations, intelligent hover effects, and seamless transitions that respond to your every interaction.
                </p>
                <div class="flex flex-col sm:flex-row gap-4 justify-center animate-fade-in animation-delay-500">
                    <button onclick="showPage('services')" class="px-8 py-4 bg-gradient-to-r from-indigo-500 to-purple-600 text-white font-semibold rounded-full hover:scale-105 hover:shadow-xl transition-all duration-300 hover:from-indigo-600 hover:to-purple-700 magnetic-effect">
                        Explore Features
                    </button>
                    <button onclick="showPage('about')" class="px-8 py-4 border-2 border-white/30 text-white font-semibold rounded-full hover:bg-white/10 hover:scale-105 transition-all duration-300 backdrop-blur-sm magnetic-effect">
                        Learn More
                    </button>
                </div>
            </div>

            <!-- Scroll indicator -->
            <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce animate-fade-in animation-delay-700">
                <div class="w-6 h-10 border-2 border-white/50 rounded-full flex justify-center">
                    <div class="w-1 h-3 bg-white/70 rounded-full mt-2 animate-pulse"></div>
                </div>
            </div>
            
            <!-- Floating shapes -->
            <div class="absolute top-1/4 right-1/4 w-16 h-16 rounded-lg bg-indigo-400/20 backdrop-blur-sm rotate-12 animate-float animation-delay-2000"></div>
            <div class="absolute bottom-1/3 left-1/4 w-12 h-12 rounded-full bg-pink-400/20 backdrop-blur-sm animate-float animation-delay-3000"></div>
            <div class="absolute top-1/3 left-1/2 w-20 h-20 rounded-lg bg-purple-400/20 backdrop-blur-sm -rotate-12 animate-float-reverse animation-delay-4000"></div>
        </section>

        <!-- Features Section -->
        <section class="py-24 bg-white">
            <div class="max-w-7xl mx-auto px-6">
                <div class="text-center mb-20">
                    <h2 class="text-4xl font-bold text-gray-900 mb-6 animate-fade-in">
                        Next-Level Navigation
                    </h2>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto animate-fade-in animation-delay-200">
                        Revolutionary features that redefine user experience and interaction design.
                    </p>
                </div>

                <div class="grid md:grid-cols-3 gap-8">
                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale gradient-border animate-fade-in">
                        <div class="w-20 h-20 bg-gradient-to-r from-indigo-100 to-purple-100 rounded-2xl flex items-center justify-center mb-6 mx-auto">
                            <div class="w-12 h-12 bg-gradient-to-r from-indigo-500 to-purple-500 rounded-lg flex items-center justify-center text-white">
                                ✨
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-gray-900 mb-4 text-center">Micro-Interactions</h3>
                        <p class="text-gray-600 leading-relaxed text-center">
                            Subtle animations that respond to user actions, creating a delightful and intuitive experience.
                        </p>
                    </div>

                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale gradient-border animate-fade-in animation-delay-200">
                        <div class="w-20 h-20 bg-gradient-to-r from-blue-100 to-indigo-100 rounded-2xl flex items-center justify-center mb-6 mx-auto">
                            <div class="w-12 h-12 bg-gradient-to-r from-blue-500 to-indigo-500 rounded-lg flex items-center justify-center text-white">
                                📱
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-gray-900 mb-4 text-center">Adaptive Design</h3>
                        <p class="text-gray-600 leading-relaxed text-center">
                            Seamless experience across all devices with intelligent layout adjustments.
                        </p>
                    </div>

                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale gradient-border animate-fade-in animation-delay-400">
                        <div class="w-20 h-20 bg-gradient-to-r from-pink-100 to-rose-100 rounded-2xl flex items-center justify-center mb-6 mx-auto">
                            <div class="w-12 h-12 bg-gradient-to-r from-pink-500 to-rose-500 rounded-lg flex items-center justify-center text-white">
                                ⚡
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-gray-900 mb-4 text-center">Performance</h3>
                        <p class="text-gray-600 leading-relaxed text-center">
                            Optimized animations that maintain 60fps while being lightweight and efficient.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Demo Section -->
        <section class="py-24 bg-gradient-to-br from-gray-50 to-indigo-50">
            <div class="max-w-7xl mx-auto px-6">
                <div class="grid lg:grid-cols-2 gap-12 items-center">
                    <div class="animate-fade-in">
                        <h2 class="text-4xl font-bold text-gray-900 mb-6">
                            Interactive Showcase
                        </h2>
                        <p class="text-lg text-gray-600 mb-8 leading-relaxed">
                            Experience our navigation system in action with this interactive demo. Hover over elements to see the fluid animations and responsive design.
                        </p>
                        <button onclick="showPage('services')" class="px-8 py-3 bg-gradient-to-r from-indigo-500 to-purple-600 text-white font-semibold rounded-lg hover:scale-105 hover:shadow-lg transition-all duration-300 magnetic-effect">
                            See All Features
                        </button>
                    </div>
                    <div class="relative h-96 bg-white rounded-2xl shadow-xl overflow-hidden animate-fade-in animation-delay-300">
                        <div class="absolute inset-0 flex items-center justify-center p-6">
                            <div class="w-full max-w-sm mx-auto">
                                <div class="bg-gray-100 rounded-xl p-4 mb-4">
                                    <div class="flex space-x-2">
                                        <div class="w-3 h-3 rounded-full bg-red-500"></div>
                                        <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
                                        <div class="w-3 h-3 rounded-full bg-green-500"></div>
                                    </div>
                                </div>
                                <div class="bg-gradient-to-r from-indigo-500 to-purple-600 rounded-xl p-6 text-white">
                                    <h3 class="text-xl font-bold mb-2">NaviX Demo</h3>
                                    <p class="text-indigo-100 mb-4">Hover over the navigation items below</p>
                                    <div class="flex space-x-2">
                                        <a href="#" class="px-4 py-2 bg-white/20 rounded-lg hover:bg-white/30 transition-all duration-300">Home</a>
                                        <a href="#" class="px-4 py-2 bg-white/20 rounded-lg hover:bg-white/30 transition-all duration-300">About</a>
                                        <a href="#" class="px-4 py-2 bg-white/20 rounded-lg hover:bg-white/30 transition-all duration-300">Services</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/10 to-transparent pointer-events-none"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Developer Profile Section -->
        <section class="py-24 bg-indigo-900 text-white">
            <div class="max-w-7xl mx-auto px-6">
                <div class="text-center mb-16 animate-fade-in">
                    <h2 class="text-4xl font-bold mb-6">Meet the Developer</h2>
                    <p class="text-xl text-indigo-200 max-w-3xl mx-auto">The creative mind behind this interactive navigation experience</p>
                </div>
                
                <div class="flex flex-col items-center animate-fade-in animation-delay-200">
                    <div class="w-48 h-48 rounded-full border-4 border-white/20 mb-6 overflow-hidden">
                        <img src="https://media.licdn.com/dms/image/D5603AQF4H5e7Yb4QbQ/profile-displayphoto-shrink_800_800/0/1694613382563?e=1721260800&v=beta&t=4J4Q4Kc5HnY8NQn5f9Z9Q9Q9Q9Q9Q9Q9Q9Q9Q9Q9Q9Q" 
                             alt="Nivas Alugubelli" 
                             class="w-full h-full object-cover">
                    </div>
                    <h3 class="text-3xl font-bold mb-2">Nivas Alugubelli</h3>
                    <p class="text-indigo-300 mb-4">Frontend Developer & UI/UX Designer</p>
                    <div class="max-w-2xl text-center text-indigo-100 mb-6">
                        <p class="mb-4">Specializing in creating immersive web experiences with cutting-edge animations and intuitive interactions.</p>
                        <p>With expertise in modern JavaScript frameworks and a passion for design systems, Nivas crafts digital experiences that delight users and drive engagement.</p>
                    </div>
                    <div class="flex space-x-4">
                        <a href="#" class="px-6 py-2 bg-white text-indigo-600 font-medium rounded-full hover:bg-indigo-100 transition-colors duration-300">
                            View Portfolio
                        </a>
                        <a href="#" class="px-6 py-2 border-2 border-white text-white font-medium rounded-full hover:bg-white/10 transition-colors duration-300">
                            Contact
                        </a>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- About Page -->
    <div id="about" class="page-transition page-hidden">
        <!-- Hero Section -->
        <section class="relative min-h-[60vh] flex items-center justify-center overflow-hidden bg-gradient-to-br from-blue-900 via-indigo-900 to-purple-900">
            <div class="absolute inset-0 opacity-20">
                <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-blue-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow"></div>
                <div class="absolute top-1/3 right-1/4 w-96 h-96 bg-indigo-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow animation-delay-2000"></div>
                <div class="absolute bottom-1/4 left-1/3 w-96 h-96 bg-purple-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow animation-delay-4000"></div>
            </div>
            
            <div class="relative z-10 text-center px-6 max-w-4xl mx-auto py-24">
                <h1 class="text-4xl md:text-6xl font-bold text-white mb-6 animate-fade-in">
                    About NaviX
                </h1>
                <p class="text-xl text-blue-100 leading-relaxed animate-fade-in animation-delay-200">
                    Pioneering the future of interactive web navigation since 2023.
                </p>
            </div>
        </section>

        <!-- Content Section -->
        <section class="py-24 bg-white">
            <div class="max-w-7xl mx-auto px-6">
                <div class="grid lg:grid-cols-2 gap-16 items-center">
                    <div class="animate-fade-in">
                        <h2 class="text-4xl font-bold text-gray-900 mb-6">
                            Our Vision
                        </h2>
                        <p class="text-lg text-gray-600 mb-6 leading-relaxed">
                            At NaviX, we believe that navigation should be more than functional—it should be an experience that delights users and enhances their journey through digital spaces.
                        </p>
                        <p class="text-lg text-gray-600 leading-relaxed">
                            Our team of designers and developers combine aesthetic sensibility with technical expertise to create navigation systems that are intuitive, beautiful, and performant across all devices.
                        </p>
                    </div>
                    <div class="relative h-96 rounded-2xl overflow-hidden animate-fade-in animation-delay-300">
                        <div class="absolute inset-0 bg-gradient-to-r from-blue-500 to-indigo-600 flex items-center justify-center">
                            <div class="text-white text-6xl font-bold opacity-20">NaviX</div>
                        </div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/30 to-transparent"></div>
                        <div class="absolute bottom-0 left-0 right-0 p-6 text-white">
                            <h3 class="text-xl font-semibold">Innovation in Motion</h3>
                            <p class="text-blue-100">Creating seamless digital experiences</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Team Section -->
        <section class="py-24 bg-gray-50">
            <div class="max-w-7xl mx-auto px-6">
                <div class="text-center mb-20 animate-fade-in">
                    <h2 class="text-4xl font-bold text-gray-900 mb-6">
                        Meet The Team
                    </h2>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                        The creative minds behind our innovative navigation solutions.
                    </p>
                </div>
                <div class="grid md:grid-cols-3 gap-8">
                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale animate-fade-in">
                        <div class="w-32 h-32 mx-auto mb-6 rounded-full bg-gradient-to-r from-blue-100 to-indigo-100 flex items-center justify-center overflow-hidden">
                            <div class="w-28 h-28 rounded-full bg-blue-500 flex items-center justify-center text-white text-4xl">
                                👨‍💻
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-center text-gray-900 mb-2">Alex Chen</h3>
                        <p class="text-blue-600 text-center mb-4">Lead Designer</p>
                        <p class="text-gray-600 text-center">
                            Creates intuitive user flows with pixel-perfect animations.
                        </p>
                    </div>
                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale animate-fade-in animation-delay-200">
                        <div class="w-32 h-32 mx-auto mb-6 rounded-full bg-gradient-to-r from-purple-100 to-pink-100 flex items-center justify-center overflow-hidden">
                            <div class="w-28 h-28 rounded-full bg-purple-500 flex items-center justify-center text-white text-4xl">
                                👩‍💻
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-center text-gray-900 mb-2">Samira Khan</h3>
                        <p class="text-purple-600 text-center mb-4">Frontend Developer</p>
                        <p class="text-gray-600 text-center">
                            Implements smooth, performant interactions.
                        </p>
                    </div>
                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale animate-fade-in animation-delay-400">
                        <div class="w-32 h-32 mx-auto mb-6 rounded-full bg-gradient-to-r from-green-100 to-teal-100 flex items-center justify-center overflow-hidden">
                            <img src="https://media.licdn.com/dms/image/D5603AQF4H5e7Yb4QbQ/profile-displayphoto-shrink_800_800/0/1694613382563?e=1721260800&v=beta&t=4J4Q4Kc5HnY8NQn5f9Z9Q9Q9Q9Q9Q9Q9Q9Q9Q9Q9Q9Q" 
                                 alt="Nivas Alugubelli" 
                                 class="w-full h-full object-cover">
                        </div>
                        <h3 class="text-2xl font-semibold text-center text-gray-900 mb-2">Nivas Alugubelli</h3>
                        <p class="text-green-600 text-center mb-4">Lead Developer</p>
                        <p class="text-gray-600 text-center">
                            Architect of interactive experiences and animation systems.
                        </p>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- Services Page -->
    <div id="services" class="page-transition page-hidden">
        <!-- Hero Section -->
        <section class="relative min-h-[60vh] flex items-center justify-center overflow-hidden bg-gradient-to-br from-purple-900 via-indigo-900 to-blue-900">
            <div class="absolute inset-0 opacity-20">
                <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-purple-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow"></div>
                <div class="absolute top-1/3 right-1/4 w-96 h-96 bg-indigo-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow animation-delay-2000"></div>
                <div class="absolute bottom-1/4 left-1/3 w-96 h-96 bg-blue-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow animation-delay-4000"></div>
            </div>
            
            <div class="relative z-10 text-center px-6 max-w-4xl mx-auto py-24">
                <h1 class="text-4xl md:text-6xl font-bold text-white mb-6 animate-fade-in">
                    Our Services
                </h1>
                <p class="text-xl text-purple-100 leading-relaxed animate-fade-in animation-delay-200">
                    Comprehensive solutions for modern interactive navigation.
                </p>
            </div>
        </section>

        <!-- Services Grid -->
        <section class="py-24 bg-white">
            <div class="max-w-7xl mx-auto px-6">
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale gradient-border animate-fade-in">
                        <div class="w-16 h-16 bg-gradient-to-r from-indigo-100 to-purple-100 rounded-xl flex items-center justify-center mb-6">
                            <div class="w-12 h-12 bg-gradient-to-r from-indigo-500 to-purple-500 rounded-lg flex items-center justify-center text-white text-xl">
                                🎨
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-gray-900 mb-4">
                            UI/UX Design
                        </h3>
                        <p class="text-gray-600 leading-relaxed">
                            Beautiful, intuitive interfaces with purposeful animations and micro-interactions.
                        </p>
                    </div>

                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale gradient-border animate-fade-in animation-delay-200">
                        <div class="w-16 h-16 bg-gradient-to-r from-blue-100 to-indigo-100 rounded-xl flex items-center justify-center mb-6">
                            <div class="w-12 h-12 bg-gradient-to-r from-blue-500 to-indigo-500 rounded-lg flex items-center justify-center text-white text-xl">
                                💻
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-gray-900 mb-4">
                            Frontend Development
                        </h3>
                        <p class="text-gray-600 leading-relaxed">
                            High-performance implementations using modern web technologies.
                        </p>
                    </div>

                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale gradient-border animate-fade-in animation-delay-400">
                        <div class="w-16 h-16 bg-gradient-to-r from-pink-100 to-rose-100 rounded-xl flex items-center justify-center mb-6">
                            <div class="w-12 h-12 bg-gradient-to-r from-pink-500 to-rose-500 rounded-lg flex items-center justify-center text-white text-xl">
                                📱
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-gray-900 mb-4">
                            Mobile Navigation
                        </h3>
                        <p class="text-gray-600 leading-relaxed">
                            Responsive designs with touch-optimized interactions.
                        </p>
                    </div>

                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale gradient-border animate-fade-in animation-delay-600">
                        <div class="w-16 h-16 bg-gradient-to-r from-green-100 to-teal-100 rounded-xl flex items-center justify-center mb-6">
                            <div class="w-12 h-12 bg-gradient-to-r from-green-500 to-teal-500 rounded-lg flex items-center justify-center text-white text-xl">
                                🔍
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-gray-900 mb-4">
                            UX Research
                        </h3>
                        <p class="text-gray-600 leading-relaxed">
                            Data-driven insights to optimize user flows and interactions.
                        </p>
                    </div>

                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale gradient-border animate-fade-in animation-delay-800">
                        <div class="w-16 h-16 bg-gradient-to-r from-yellow-100 to-amber-100 rounded-xl flex items-center justify-center mb-6">
                            <div class="w-12 h-12 bg-gradient-to-r from-yellow-500 to-amber-500 rounded-lg flex items-center justify-center text-white text-xl">
                                ⚡
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-gray-900 mb-4">
                            Performance Optimization
                        </h3>
                        <p class="text-gray-600 leading-relaxed">
                            Ensuring smooth animations without compromising speed.
                        </p>
                    </div>

                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale gradient-border animate-fade-in animation-delay-1000">
                        <div class="w-16 h-16 bg-gradient-to-r from-purple-100 to-pink-100 rounded-xl flex items-center justify-center mb-6">
                            <div class="w-12 h-12 bg-gradient-to-r from-purple-500 to-pink-500 rounded-lg flex items-center justify-center text-white text-xl">
                                🛠️
                            </div>
                        </div>
                        <h3 class="text-2xl font-semibold text-gray-900 mb-4">
                            Custom Solutions
                        </h3>
                        <p class="text-gray-600 leading-relaxed">
                            Tailored navigation systems for your specific needs.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Process Section -->
        <section class="py-24 bg-gradient-to-br from-indigo-50 to-purple-50">
            <div class="max-w-7xl mx-auto px-6">
                <div class="text-center mb-20 animate-fade-in">
                    <h2 class="text-4xl font-bold text-gray-900 mb-6">
                        Our Process
                    </h2>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                        A structured approach to creating exceptional navigation experiences.
                    </p>
                </div>
                <div class="relative">
                    <div class="hidden lg:block absolute left-1/2 top-0 bottom-0 w-1 bg-gradient-to-b from-indigo-200 to-purple-200 transform -translate-x-1/2"></div>
                    
                    <div class="grid lg:grid-cols-2 gap-8 lg:gap-16">
                        <!-- Step 1 -->
                        <div class="lg:text-right animate-fade-in">
                            <div class="lg:mr-8">
                                <div class="w-16 h-16 bg-indigo-500 rounded-full flex items-center justify-center text-white text-xl font-bold mb-4 ml-auto lg:mr-0 mx-auto">1</div>
                                <h3 class="text-2xl font-semibold text-gray-900 mb-3">Discovery</h3>
                                <p class="text-gray-600">
                                    We analyze your users' needs and business objectives to define the perfect navigation structure.
                                </p>
                            </div>
                        </div>
                        <div class="lg:col-start-2 animate-fade-in animation-delay-200">
                            <!-- Empty on purpose for layout -->
                        </div>
                        
                        <!-- Step 2 -->
                        <div class="lg:col-start-1 animate-fade-in animation-delay-400">
                            <!-- Empty on purpose for layout -->
                        </div>
                        <div class="lg:text-left animate-fade-in animation-delay-400">
                            <div class="lg:ml-8">
                                <div class="w-16 h-16 bg-purple-500 rounded-full flex items-center justify-center text-white text-xl font-bold mb-4 mr-auto lg:ml-0 mx-auto">2</div>
                                <h3 class="text-2xl font-semibold text-gray-900 mb-3">Wireframing</h3>
                                <p class="text-gray-600">
                                    Creating low-fidelity prototypes to test navigation flows and user journeys.
                                </p>
                            </div>
                        </div>
                        
                        <!-- Step 3 -->
                        <div class="lg:text-right animate-fade-in animation-delay-600">
                            <div class="lg:mr-8">
                                <div class="w-16 h-16 bg-blue-500 rounded-full flex items-center justify-center text-white text-xl font-bold mb-4 ml-auto lg:mr-0 mx-auto">3</div>
                                <h3 class="text-2xl font-semibold text-gray-900 mb-3">Design</h3>
                                <p class="text-gray-600">
                                    High-fidelity designs with interactive prototypes showcasing animations and transitions.
                                </p>
                            </div>
                        </div>
                        <div class="lg:col-start-2 animate-fade-in animation-delay-600">
                            <!-- Empty on purpose for layout -->
                        </div>
                        
                        <!-- Step 4 -->
                        <div class="lg:col-start-1 animate-fade-in animation-delay-800">
                            <!-- Empty on purpose for layout -->
                        </div>
                        <div class="lg:text-left animate-fade-in animation-delay-800">
                            <div class="lg:ml-8">
                                <div class="w-16 h-16 bg-pink-500 rounded-full flex items-center justify-center text-white text-xl font-bold mb-4 mr-auto lg:ml-0 mx-auto">4</div>
                                <h3 class="text-2xl font-semibold text-gray-900 mb-3">Development</h3>
                                <p class="text-gray-600">
                                    Implementing the design with clean, performant code that works across all devices.
                                </p>
                            </div>
                        </div>
                        
                        <!-- Step 5 -->
                        <div class="lg:text-right animate-fade-in animation-delay-1000">
                            <div class="lg:mr-8">
                                <div class="w-16 h-16 bg-green-500 rounded-full flex items-center justify-center text-white text-xl font-bold mb-4 ml-auto lg:mr-0 mx-auto">5</div>
                                <h3 class="text-2xl font-semibold text-gray-900 mb-3">Testing</h3>
                                <p class="text-gray-600">
                                    Rigorous testing across devices and user groups to ensure flawless performance.
                                </p>
                            </div>
                        </div>
                        <div class="lg:col-start-2 animate-fade-in animation-delay-1000">
                            <!-- Empty on purpose for layout -->
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- Work Page -->
    <div id="work" class="page-transition page-hidden">
        <!-- Hero Section -->
        <section class="relative min-h-[60vh] flex items-center justify-center overflow-hidden bg-gradient-to-br from-blue-900 via-purple-900 to-pink-900">
            <div class="absolute inset-0 opacity-20">
                <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-blue-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow"></div>
                <div class="absolute top-1/3 right-1/4 w-96 h-96 bg-purple-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow animation-delay-2000"></div>
                <div class="absolute bottom-1/4 left-1/3 w-96 h-96 bg-pink-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow animation-delay-4000"></div>
            </div>
            
            <div class="relative z-10 text-center px-6 max-w-4xl mx-auto py-24">
                <h1 class="text-4xl md:text-6xl font-bold text-white mb-6 animate-fade-in">
                    Our Work
                </h1>
                <p class="text-xl text-blue-100 leading-relaxed animate-fade-in animation-delay-200">
                    Showcase of our interactive navigation projects.
                </p>
            </div>
        </section>

        <!-- Portfolio Grid -->
        <section class="py-24 bg-white">
            <div class="max-w-7xl mx-auto px-6">
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div class="relative group rounded-2xl overflow-hidden shadow-lg hover-scale animate-fade-in">
                        <div class="aspect-w-16 aspect-h-9 bg-gradient-to-r from-indigo-500 to-purple-600">
                            <div class="absolute inset-0 flex items-center justify-center text-white text-4xl opacity-80">
                                🛒
                            </div>
                        </div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                            <h3 class="text-xl font-semibold text-white mb-2">E-Commerce Platform</h3>
                            <p class="text-indigo-200">Streamlined product navigation</p>
                        </div>
                    </div>

                    <div class="relative group rounded-2xl overflow-hidden shadow-lg hover-scale animate-fade-in animation-delay-200">
                        <div class="aspect-w-16 aspect-h-9 bg-gradient-to-r from-blue-500 to-indigo-600">
                            <div class="absolute inset-0 flex items-center justify-center text-white text-4xl opacity-80">
                                📱
                            </div>
                        </div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                            <h3 class="text-xl font-semibold text-white mb-2">Mobile App</h3>
                            <p class="text-blue-200">Gesture-based navigation</p>
                        </div>
                    </div>

                    <div class="relative group rounded-2xl overflow-hidden shadow-lg hover-scale animate-fade-in animation-delay-400">
                        <div class="aspect-w-16 aspect-h-9 bg-gradient-to-r from-purple-500 to-pink-600">
                            <div class="absolute inset-0 flex items-center justify-center text-white text-4xl opacity-80">
                                🏥
                            </div>
                        </div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                            <h3 class="text-xl font-semibold text-white mb-2">Healthcare Portal</h3>
                            <p class="text-purple-200">Accessible navigation system</p>
                        </div>
                    </div>

                    <div class="relative group rounded-2xl overflow-hidden shadow-lg hover-scale animate-fade-in animation-delay-600">
                        <div class="aspect-w-16 aspect-h-9 bg-gradient-to-r from-green-500 to-teal-600">
                            <div class="absolute inset-0 flex items-center justify-center text-white text-4xl opacity-80">
                                🎓
                            </div>
                        </div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                            <h3 class="text-xl font-semibold text-white mb-2">Learning Platform</h3>
                            <p class="text-green-200">Course navigation hierarchy</p>
                        </div>
                    </div>

                    <div class="relative group rounded-2xl overflow-hidden shadow-lg hover-scale animate-fade-in animation-delay-800">
                        <div class="aspect-w-16 aspect-h-9 bg-gradient-to-r from-pink-500 to-rose-600">
                            <div class="absolute inset-0 flex items-center justify-center text-white text-4xl opacity-80">
                                ✈️
                            </div>
                        </div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                            <h3 class="text-xl font-semibold text-white mb-2">Travel Site</h3>
                            <p class="text-pink-200">Dynamic filtering navigation</p>
                        </div>
                    </div>

                    <div class="relative group rounded-2xl overflow-hidden shadow-lg hover-scale animate-fade-in animation-delay-1000">
                        <div class="aspect-w-16 aspect-h-9 bg-gradient-to-r from-yellow-500 to-amber-600">
                            <div class="absolute inset-0 flex items-center justify-center text-white text-4xl opacity-80">
                                🏛️
                            </div>
                        </div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/70 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                            <h3 class="text-xl font-semibold text-white mb-2">Government Portal</h3>
                            <p class="text-yellow-200">Multi-level navigation system</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Testimonials -->
        <section class="py-24 bg-gray-50">
            <div class="max-w-7xl mx-auto px-6">
                <div class="text-center mb-20 animate-fade-in">
                    <h2 class="text-4xl font-bold text-gray-900 mb-6">
                        Client Testimonials
                    </h2>
                    <p class="text-xl text-gray-600 max-w-3xl mx-auto">
                        What our clients say about our navigation solutions.
                    </p>
                </div>
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale animate-fade-in">
                        <div class="flex items-center mb-4">
                            <div class="w-12 h-12 rounded-full bg-indigo-100 flex items-center justify-center text-indigo-500 mr-4">
                                👤
                            </div>
                            <div>
                                <h4 class="font-semibold text-gray-900">Sarah Johnson</h4>
                                <p class="text-sm text-gray-600">CEO, RetailCorp</p>
                            </div>
                        </div>
                        <p class="text-gray-600 italic">
                            "NaviX transformed our e-commerce navigation, resulting in a 30% increase in conversions. The animations are smooth and the user experience is flawless."
                        </p>
                        <div class="mt-4 flex text-yellow-400">
                            ★ ★ ★ ★ ★
                        </div>
                    </div>
                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale animate-fade-in animation-delay-200">
                        <div class="flex items-center mb-4">
                            <div class="w-12 h-12 rounded-full bg-blue-100 flex items-center justify-center text-blue-500 mr-4">
                                👤
                            </div>
                            <div>
                                <h4 class="font-semibold text-gray-900">Michael Chen</h4>
                                <p class="text-sm text-gray-600">CTO, TechStart</p>
                            </div>
                        </div>
                        <p class="text-gray-600 italic">
                            "The mobile navigation system NaviX created for our app is intuitive and beautiful. Our user retention has never been higher."
                        </p>
                        <div class="mt-4 flex text-yellow-400">
                            ★ ★ ★ ★ ★
                        </div>
                    </div>
                    <div class="bg-white p-8 rounded-2xl shadow-lg hover-scale animate-fade-in animation-delay-400">
                        <div class="flex items-center mb-4">
                            <div class="w-12 h-12 rounded-full bg-purple-100 flex items-center justify-center text-purple-500 mr-4">
                                👤
                            </div>
                            <div>
                                <h4 class="font-semibold text-gray-900">Emma Rodriguez</h4>
                                <p class="text-sm text-gray-600">Director, HealthOrg</p>
                            </div>
                        </div>
                        <p class="text-gray-600 italic">
                            "Accessibility was crucial for our healthcare portal. NaviX delivered a navigation system that works perfectly for all our users."
                        </p>
                        <div class="mt-4 flex text-yellow-400">
                            ★ ★ ★ ★ ★
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- Contact Page -->
    <div id="contact" class="page-transition page-hidden">
        <!-- Hero Section -->
        <section class="relative min-h-[60vh] flex items-center justify-center overflow-hidden bg-gradient-to-br from-indigo-900 via-blue-900 to-cyan-900">
            <div class="absolute inset-0 opacity-20">
                <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-indigo-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow"></div>
                <div class="absolute top-1/3 right-1/4 w-96 h-96 bg-blue-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow animation-delay-2000"></div>
                <div class="absolute bottom-1/4 left-1/3 w-96 h-96 bg-cyan-500 rounded-full mix-blend-overlay filter blur-3xl animate-pulse-slow animation-delay-4000"></div>
            </div>
            
            <div class="relative z-10 text-center px-6 max-w-4xl mx-auto py-24">
                <h1 class="text-4xl md:text-6xl font-bold text-white mb-6 animate-fade-in">
                    Get In Touch
                </h1>
                <p class="text-xl text-indigo-100 leading-relaxed animate-fade-in animation-delay-200">
                    Ready to elevate your navigation experience? Let's talk.
                </p>
            </div>
        </section>

        <!-- Contact Form Section -->
        <section class="py-24 bg-white">
            <div class="max-w-7xl mx-auto px-6">
                <div class="grid lg:grid-cols-2 gap-16">
                    <!-- Contact Info -->
                    <div class="animate-fade-in">
                        <h2 class="text-4xl font-bold text-gray-900 mb-8">
                            Contact Us
                        </h2>
                        <p class="text-lg text-gray-600 mb-8 leading-relaxed">
                            Whether you're looking to improve your existing navigation or build something entirely new, we'd love to hear about your project.
                        </p>
                        
                        <div class="space-y-6">
                            <div class="flex items-start">
                                <div class="w-12 h-12 bg-indigo-100 rounded-lg flex items-center justify-center mr-4 mt-1">
                                    <div class="w-6 h-6 bg-indigo-500 rounded-full"></div>
                                </div>
                                <div>
                                    <h3 class="font-semibold text-gray-900">Email</h3>
                                    <p class="text-gray-600">hello@navix.design</p>
                                </div>
                            </div>
                            
                            <div class="flex items-start">
                                <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center mr-4 mt-1">
                                    <div class="w-6 h-6 bg-blue-500 rounded-full"></div>
                                </div>
                                <div>
                                    <h3 class="font-semibold text-gray-900">Phone</h3>
                                    <p class="text-gray-600">+1 (555) 123-4567</p>
                                </div>
                            </div>
                            
                            <div class="flex items-start">
                                <div class="w-12 h-12 bg-cyan-100 rounded-lg flex items-center justify-center mr-4 mt-1">
                                    <div class="w-6 h-6 bg-cyan-500 rounded-full"></div>
                                </div>
                                <div>
                                    <h3 class="font-semibold text-gray-900">Location</h3>
                                    <p class="text-gray-600">San Francisco, CA</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="mt-12">
                            <h3 class="text-xl font-semibold text-gray-900 mb-4">Follow Us</h3>
                            <div class="flex space-x-4">
                                <a href="#" class="w-10 h-10 bg-gray-100 rounded-full flex items-center justify-center text-gray-700 hover:bg-indigo-100 hover:text-indigo-600 transition-colors duration-300">
                                    <span class="sr-only">Twitter</span>
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                                        <path d="M8.29 20.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0022 5.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.072 4.072 0 012.8 9.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 012 18.407a11.616 11.616 0 006.29 1.84"></path>
                                    </svg>
                                </a>
                                <a href="#" class="w-10 h-10 bg-gray-100 rounded-full flex items-center justify-center text-gray-700 hover:bg-blue-100 hover:text-blue-600 transition-colors duration-300">
                                    <span class="sr-only">LinkedIn</span>
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                                        <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"></path>
                                    </svg>
                                </a>
                                <a href="#" class="w-10 h-10 bg-gray-100 rounded-full flex items-center justify-center text-gray-700 hover:bg-pink-100 hover:text-pink-600 transition-colors duration-300">
                                    <span class="sr-only">Dribbble</span>
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                                        <path d="M12 24c6.627 0 12-5.373 12-12s-5.373-12-12-12-12 5.373-12 12 5.373 12 12 12zm10-12c0 1.091-.154 2.14-.436 3.137-1.729-1.037-3.744-1.824-5.961-2.251.761-1.793 1.362-3.671 1.764-5.589 2.666.972 4.633 3.458 4.633 6.703zm-6.5-8.5c1.102 0 2 .898 2 2s-.898 2-2 2-2-.898-2-2 .898-2 2-2zm-7.5 1.5c1.235 0 2.755.24 4.322.709-.462 1.753-.997 3.515-1.6 5.246-1.896-.602-3.54-1.608-4.847-2.876.069-1.636.671-3.12 1.525-4.079h1.6zm-3.5 1.5c.243 1.566.749 3.092 1.496 4.523-1.372.968-2.519 2.213-3.382 3.676-1.08-1.817-1.714-3.971-1.714-6.199 0-2.245.848-4.293 2.242-5.832.522.91 1.153 1.751 1.886 2.539-.437.86-.738 1.776-.928 2.733-.034.192-.061.385-.081.581-.015.133-.025.266-.031.399h-.008zm3.5-5c-1.032 0-2 .397-2.729 1.118-.75.746-1.171 1.747-1.171 2.882h3.9v-4zm2 4h4c0-2.208-1.792-4-4-4v4zm-7.5 7.5c.586-1.237 1.29-2.385 2.1-3.424.444.947.912 1.887 1.4 2.803-1.813.6-3.283 1.51-4.303 2.621h.803zm9.5 2.5c-.888-.912-2.047-1.634-3.4-2.157.488-1.913.832-3.843 1.029-5.757 2.208.439 4.254 1.253 6 2.416-.279.982-.662 1.918-1.137 2.793-1.035-.4-2.059-.669-3.063-.812.041.28.071.562.071.857 0 1.1-.3 2.126-.816 3.009.272.034.547.051.826.051 1.366 0 2.651-.355 3.766-.972-.28.51-.6.993-.956 1.442-.818-.246-1.666-.41-2.53-.487h-.02z"></path>
                                    </svg>
                                </a>
                            </div>
                        </div>
                    </div>

                    <!-- Contact Form -->
                    <div class="bg-gradient-to-br from-indigo-50 to-blue-50 p-8 rounded-2xl shadow-lg animate-fade-in animation-delay-200">
                        <form class="space-y-6" onsubmit="handleFormSubmit(event)">
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-2">
                                    Name
                                </label>
                                <input
                                    type="text"
                                    class="w-full px-4 py-3 bg-white border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-transparent transition-all duration-300 hover:border-indigo-300"
                                    placeholder="Your name"
                                    required
                                />
                            </div>
                            
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-2">
                                    Email
                                </label>
                                <input
                                    type="email"
                                    class="w-full px-4 py-3 bg-white border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-transparent transition-all duration-300 hover:border-indigo-300"
                                    placeholder="your@email.com"
                                    required
                                />
                            </div>
                            
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-2">
                                    Project Type
                                </label>
                                <select class="w-full px-4 py-3 bg-white border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-transparent transition-all duration-300 hover:border-indigo-300">
                                    <option>Website Navigation</option>
                                    <option>Mobile App Navigation</option>
                                    <option>UI/UX Design</option>
                                    <option>Other</option>
                                </select>
                            </div>
                            
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-2">
                                    Message
                                </label>
                                <textarea
                                    rows="5"
                                    class="w-full px-4 py-3 bg-white border border-gray-200 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-transparent transition-all duration-300 hover:border-indigo-300 resize-none"
                                    placeholder="Tell us about your project..."
                                    required
                                ></textarea>
                            </div>
                            
                            <button
                                type="submit"
                                class="w-full px-6 py-4 bg-gradient-to-r from-indigo-500 to-blue-600 text-white font-semibold rounded-lg hover:scale-105 hover:shadow-lg transition-all duration-300 magnetic-effect"
                            >
                                Send Message
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white py-16">
        <div class="max-w-7xl mx-auto px-6">
            <div class="grid md:grid-cols-4 gap-12">
                <div class="animate-fade-in">
                    <a href="#" class="text-2xl font-bold bg-gradient-to-r from-indigo-400 to-purple-400 bg-clip-text text-transparent mb-6 inline-block">
                        NaviX
                    </a>
                    <p class="text-gray-400 mb-6">
                        Creating exceptional digital navigation experiences since 2023.
                    </p>
                    <div class="flex space-x-4">
                        <a href="#" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">
                            <span class="sr-only">Twitter</span>
                            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M8.29 20.251c7.547 0 11.675-6.253 11.675-11.675 0-.178 0-.355-.012-.53A8.348 8.348 0 0022 5.92a8.19 8.19 0 01-2.357.646 4.118 4.118 0 001.804-2.27 8.224 8.224 0 01-2.605.996 4.107 4.107 0 00-6.993 3.743 11.65 11.65 0 01-8.457-4.287 4.106 4.106 0 001.27 5.477A4.072 4.072 0 012.8 9.713v.052a4.105 4.105 0 003.292 4.022 4.095 4.095 0 01-1.853.07 4.108 4.108 0 003.834 2.85A8.233 8.233 0 012 18.407a11.616 11.616 0 006.29 1.84"></path>
                            </svg>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-blue-400 transition-colors duration-300">
                            <span class="sr-only">LinkedIn</span>
                            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"></path>
                            </svg>
                        </a>
                        <a href="#" class="text-gray-400 hover:text-pink-400 transition-colors duration-300">
                            <span class="sr-only">Dribbble</span>
                            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M12 24c6.627 0 12-5.373 12-12s-5.373-12-12-12-12 5.373-12 12 5.373 12 12 12zm10-12c0 1.091-.154 2.14-.436 3.137-1.729-1.037-3.744-1.824-5.961-2.251.761-1.793 1.362-3.671 1.764-5.589 2.666.972 4.633 3.458 4.633 6.703zm-6.5-8.5c1.102 0 2 .898 2 2s-.898 2-2 2-2-.898-2-2 .898-2 2-2zm-7.5 1.5c1.235 0 2.755.24 4.322.709-.462 1.753-.997 3.515-1.6 5.246-1.896-.602-3.54-1.608-4.847-2.876.069-1.636.671-3.12 1.525-4.079h1.6zm-3.5 1.5c.243 1.566.749 3.092 1.496 4.523-1.372.968-2.519 2.213-3.382 3.676-1.08-1.817-1.714-3.971-1.714-6.199 0-2.245.848-4.293 2.242-5.832.522.91 1.153 1.751 1.886 2.539-.437.86-.738 1.776-.928 2.733-.034.192-.061.385-.081.581-.015.133-.025.266-.031.399h-.008zm3.5-5c-1.032 0-2 .397-2.729 1.118-.75.746-1.171 1.747-1.171 2.882h3.9v-4zm2 4h4c0-2.208-1.792-4-4-4v4zm-7.5 7.5c.586-1.237 1.29-2.385 2.1-3.424.444.947.912 1.887 1.4 2.803-1.813.6-3.283 1.51-4.303 2.621h.803zm9.5 2.5c-.888-.912-2.047-1.634-3.4-2.157.488-1.913.832-3.843 1.029-5.757 2.208.439 4.254 1.253 6 2.416-.279.982-.662 1.918-1.137 2.793-1.035-.4-2.059-.669-3.063-.812.041.28.071.562.071.857 0 1.1-.3 2.126-.816 3.009.272.034.547.051.826.051 1.366 0 2.651-.355 3.766-.972-.28.51-.6.993-.956 1.442-.818-.246-1.666-.41-2.53-.487h-.02z"></path>
                            </svg>
                        </a>
                    </div>
                </div>
                <div class="animate-fade-in animation-delay-200">
                    <h3 class="text-lg font-semibold mb-6">Quick Links</h3>
                    <ul class="space-y-3">
                        <li><a href="#" onclick="showPage('home')" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">Home</a></li>
                        <li><a href="#" onclick="showPage('about')" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">About</a></li>
                        <li><a href="#" onclick="showPage('services')" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">Services</a></li>
                        <li><a href="#" onclick="showPage('work')" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">Work</a></li>
                        <li><a href="#" onclick="showPage('contact')" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">Contact</a></li>
                    </ul>
                </div>
                <div class="animate-fade-in animation-delay-400">
                    <h3 class="text-lg font-semibold mb-6">Services</h3>
                    <ul class="space-y-3">
                        <li><a href="#" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">UI/UX Design</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">Frontend Development</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">Mobile Navigation</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">UX Research</a></li>
                        <li><a href="#" class="text-gray-400 hover:text-indigo-400 transition-colors duration-300">Performance Optimization</a></li>
                    </ul>
                </div>
                <div class="animate-fade-in animation-delay-600">
                    <h3 class="text-lg font-semibold mb-6">Developer</h3>
                    <div class="flex items-center mb-4">
                        <div class="w-12 h-12 rounded-full overflow-hidden mr-4">
                            <img src="https://media.licdn.com/dms/image/D5603AQF4H5e7Yb4QbQ/profile-displayphoto-shrink_800_800/0/1694613382563?e=1721260800&v=beta&t=4J4Q4Kc5HnY8NQn5f9Z9Q9Q9Q9Q9Q9Q9Q9Q9Q9Q9Q9Q" 
                                 alt="Nivas Alugubelli" 
                                 class="w-full h-full object-cover">
                        </div>
                        <div>
                            <h4 class="font-semibold text-white">Nivas Alugubelli</h4>
                            <p class="text-sm text-gray-400">Frontend Developer</p>
                        </div>
                    </div>
                    <p class="text-gray-400 mb-4">
                        Specializing in interactive web experiences and animation design.
                    </p>
                    <a href="#" class="text-indigo-400 hover:text-indigo-300 transition-colors duration-300 text-sm">View Portfolio →</a>
                </div>
            </div>
            <div class="border-t border-gray-800 mt-16 pt-8 flex flex-col md:flex-row justify-between items-center animate-fade-in animation-delay-800">
                <p class="text-gray-500 text-sm">
                    © 2023 NaviX. All rights reserved. Designed and developed by Nivas Alugubelli.
                </p>
                <div class="flex space-x-6 mt-4 md:mt-0">
                    <a href="#" class="text-gray-500 hover:text-indigo-400 transition-colors duration-300 text-sm">Privacy Policy</a>
                    <a href="#" class="text-gray-500 hover:text-indigo-400 transition-colors duration-300 text-sm">Terms of Service</a>
                    <a href="#" class="text-gray-500 hover:text-indigo-400 transition-colors duration-300 text-sm">Cookies</a>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // Preloader
        window.addEventListener('load', function() {
            const preloader = document.getElementById('preloader');
            preloader.style.opacity = '0';
            setTimeout(() => {
                preloader.style.display = 'none';
            }, 500);
            
            // Initialize animations for home page
            animatePageElements('home');
        });

        // Cursor effects
        const cursor = document.getElementById('cursor');
        const cursorFollower = document.getElementById('cursor-follower');
        
        document.addEventListener('mousemove', (e) => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
            
            setTimeout(() => {
                cursorFollower.style.left = e.clientX + 'px';
                cursorFollower.style.top = e.clientY + 'px';
            }, 100);
        });
        
        // Magnetic effect for elements
        document.querySelectorAll('.magnetic-effect').forEach(el => {
            el.addEventListener('mousemove', (e) => {
                const rect = el.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                
                const centerX = rect.width / 2;
                const centerY = rect.height / 2;
                
                const distanceX = x - centerX;
                const distanceY = y - centerY;
                
                el.style.transform = `translate(${distanceX * 0.1}px, ${distanceY * 0.1}px)`;
            });
            
            el.addEventListener('mouseleave', () => {
                el.style.transform = '';
            });
        });

        // Navigation state
        let isScrolled = false;
        let isMobileMenuOpen = false;
        let currentPage = 'home';

        // Handle scroll effects
        window.addEventListener('scroll', () => {
            const scrollTop = window.scrollY;
            const shouldBeScrolled = scrollTop > 50;
            
            if (shouldBeScrolled !== isScrolled) {
                isScrolled = shouldBeScrolled;
                updateNavigation();
            }
        });

        // Update navigation appearance
        function updateNavigation() {
            const nav = document.getElementById('navigation');
            const navLinks = document.querySelectorAll('.nav-link');
            
            if (isScrolled) {
                nav.classList.add('bg-white/90', 'backdrop-blur-md', 'shadow-lg', 'border-b', 'border-white/20');
                nav.classList.remove('bg-transparent');
                
                navLinks.forEach(link => {
                    link.classList.replace('text-white/90', 'text-gray-700');
                    link.classList.replace('hover:text-white', 'hover:text-indigo-600');
                    link.classList.replace('hover:bg-white/20', 'hover:bg-indigo-50');
                });
            } else {
                nav.classList.remove('bg-white/90', 'backdrop-blur-md', 'shadow-lg', 'border-b', 'border-white/20');
                nav.classList.add('bg-transparent');
                
                navLinks.forEach(link => {
                    link.classList.replace('text-gray-700', 'text-white/90');
                    link.classList.replace('hover:text-indigo-600', 'hover:text-white');
                    link.classList.replace('hover:bg-indigo-50', 'hover:bg-white/20');
                });
            }
        }

        // Toggle mobile menu
        function toggleMobileMenu() {
            isMobileMenuOpen = !isMobileMenuOpen;
            const mobileMenu = document.getElementById('mobileMenu');
            
            if (isMobileMenuOpen) {
                mobileMenu.classList.remove('max-h-0', 'opacity-0');
                mobileMenu.classList.add('max-h-[500px]', 'opacity-100', 'py-4');
            } else {
                mobileMenu.classList.remove('max-h-[500px]', 'opacity-100', 'py-4');
                mobileMenu.classList.add('max-h-0', 'opacity-0');
            }
        }

        // Show page function
        function showPage(pageName) {
            if (pageName === currentPage) return;
            
            // Hide current page
            const currentPageEl = document.getElementById(currentPage);
            currentPageEl.classList.remove('page-visible');
            currentPageEl.classList.add('page-hidden');
            
            // Show new page
            const newPageEl = document.getElementById(pageName);
            newPageEl.classList.remove('page-hidden');
            newPageEl.classList.add('page-visible');
            
            // Update current page
            currentPage = pageName;
            
            // Close mobile menu if open
            if (isMobileMenuOpen) {
                toggleMobileMenu();
            }
            
            // Reset scroll position
            window.scrollTo(0, 0);
            
            // Update navigation state
            setTimeout(() => {
                isScrolled = false;
                updateNavigation();
            }, 100);

            // Trigger animations for new page
            animatePageElements(pageName);
        }

        // Animate elements on page
        function animatePageElements(pageName) {
            const fadeElements = document.querySelectorAll(`#${pageName} .animate-fade-in`);
            fadeElements.forEach((el, index) => {
                setTimeout(() => {
                    el.style.animation = 'fadeIn 0.8s ease-out forwards';
                }, index * 100);
            });
        }

        // Handle form submission
        function handleFormSubmit(event) {
            event.preventDefault();
            
            // Show success message
            const form = event.target;
            const submitBtn = form.querySelector('button[type="submit"]');
            const originalText = submitBtn.textContent;
            
            submitBtn.textContent = 'Sending...';
            submitBtn.disabled = true;
            
            setTimeout(() => {
                submitBtn.textContent = 'Sent!';
                submitBtn.classList.remove('from-indigo-500', 'to-blue-600');
                submitBtn.classList.add('from-green-500', 'to-teal-600');
                
                setTimeout(() => {
                    submitBtn.textContent = originalText;
                    submitBtn.disabled = false;
                    submitBtn.classList.remove('from-green-500', 'to-teal-600');
                    submitBtn.classList.add('from-indigo-500', 'to-blue-600');
                    form.reset();
                }, 2000);
            }, 1500);
        }

        // Initialize navigation
        updateNavigation();
    </script>
</body>
</html>
