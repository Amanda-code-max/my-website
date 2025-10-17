
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CEO Noir & Co. - Executive Virtual Assistant</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .animate-fadeInUp { animation: fadeInUp 0.8s ease-out forwards; opacity: 0; }
        .animate-fadeIn { animation: fadeIn 1s ease-out forwards; }
        .service-card { position: relative; overflow: hidden; }
        .service-card img { transition: transform 0.5s ease-out; width: 100%; height: 100%; object-fit: cover; }
        .service-card:hover img { transform: scale(1.1); }
        .service-overlay {
            position: absolute;
            inset: 0;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            align-items: flex-end;
            padding: 24px;
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            transform: translateY(100%);
        }
        .service-card:hover .service-overlay { transform: translateY(0); }
        .service-overlay h3 { color: white; font-size: 1.5rem; font-weight: bold; }
    </style>
</head>
<body class="bg-white">
    <div id="app"></div>

    <script>
        let currentImageIndex = 0;
        let scrolled = false;

        const heroImages = [
            'https://images.unsplash.com/photo-1573496359142-b8d87734a5a5?w=1200&h=600&fit=crop',
            'https://images.unsplash.com/photo-1552664730-d307ca884978?w=1200&h=600&fit=crop'
        ];

        const services = [
            { title: 'Executive Admin', image: 'https://images.unsplash.com/photo-1573496359142-b8d87734a5a5?w=400&h=400&fit=crop' },
            { title: 'Digital Marketing & Sales', image: 'https://images.unsplash.com/photo-1552664730-d307ca884978?w=400&h=400&fit=crop' },
            { title: 'Financial Management', image: 'https://images.unsplash.com/photo-1454165804606-c3d57bc86b40?w=400&h=400&fit=crop' },
            { title: 'Real Estate Management', image: 'https://images.unsplash.com/photo-1552664730-d307ca884978?w=400&h=400&fit=crop' },
            { title: 'Contact Center Support', image: 'https://images.unsplash.com/photo-1573496359142-b8d87734a5a5?w=400&h=400&fit=crop' },
            { title: 'Lifestyle Services', image: 'https://images.unsplash.com/photo-1552664730-d307ca884978?w=400&h=400&fit=crop' }
        ];

        function render() {
            document.getElementById('app').innerHTML = `
                <!-- Navigation -->
                <nav class="fixed w-full top-0 z-50 transition-all duration-300 ${scrolled ? 'shadow-xl bg-white' : 'bg-black bg-opacity-50'}">
                    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                        <div class="flex justify-between items-center h-20">
                            <div>
                                <span class="text-2xl font-black">
                                    <span style="color: #9D8189">CEO</span>
                                    <span style="color: #F97316">•</span>
                                    <span style="color: #9D8189">Noir</span>
                                </span>
                            </div>
                            <div class="hidden md:flex space-x-8 items-center">
                                <a href="#home" class="text-sm font-semibold" style="color: ${scrolled ? '#9D8189' : '#FFFFFF'}">Home</a>
                                <a href="#about" class="text-sm font-semibold" style="color: ${scrolled ? '#9D8189' : '#FFFFFF'}">About Us</a>
                                <div class="relative group">
                                    <button class="text-sm font-semibold" style="color: ${scrolled ? '#9D8189' : '#FFFFFF'}">Services ▼</button>
                                    <div class="absolute left-0 mt-0 w-48 bg-white rounded-lg shadow-lg opacity-0 invisible group-hover:opacity-100 group-hover:visible transition-all duration-300 py-2">
                                        <a href="#services" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Executive Admin</a>
                                        <a href="#services" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Digital Marketing</a>
                                        <a href="#services" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Financial Mgmt</a>
                                    </div>
                                </div>
                                <a href="#contact" class="text-sm font-semibold" style="color: ${scrolled ? '#9D8189' : '#FFFFFF'}">Contact</a>
                                <a href="#blog" class="text-sm font-semibold" style="color: ${scrolled ? '#9D8189' : '#FFFFFF'}">Blog</a>
                                <a href="#faqs" class="text-sm font-semibold" style="color: ${scrolled ? '#9D8189' : '#FFFFFF'}">FAQs</a>
                            </div>
                        </div>
                    </div>
                </nav>

                <!-- Hero Section -->
                <section class="pt-20 pb-0 relative min-h-screen overflow-hidden flex items-center">
                    ${heroImages.map((img, idx) => `
                        <div class="absolute inset-0 transition-opacity duration-1000 ${idx === currentImageIndex ? 'opacity-100' : 'opacity-0'}" style="background-image: url(${img}); background-size: cover; background-position: center;">
                            <div class="absolute inset-0 bg-black bg-opacity-50"></div>
                        </div>
                    `).join('')}
                    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 w-full py-32">
                        <div class="max-w-3xl">
                            <h1 class="text-7xl md:text-8xl font-black text-white mb-4 animate-fadeInUp leading-tight">You lead.</h1>
                            <h2 class="text-6xl md:text-7xl font-black text-white mb-8 animate-fadeInUp leading-tight" style="animation-delay: 0.2s">I make it effortless.</h2>
                            <p class="text-2xl text-white mb-10 max-w-2xl animate-fadeIn leading-relaxed" style="animation-delay: 0.4s">Strategic virtual assistance that transforms how you lead. Reclaim your time, amplify your impact.</p>
                            <button class="px-10 py-5 rounded-full font-bold text-white text-lg transition-all hover:shadow-2xl hover:scale-105" style="background-color: #F97316">Get Started Today →</button>
                        </div>
                    </div>
                    <div class="absolute bottom-12 left-1/2 transform -translate-x-1/2 flex gap-3 z-20">
                        ${heroImages.map((_, idx) => `
                            <button onclick="changeImage(${idx})" class="w-4 h-4 rounded-full transition-all ${idx === currentImageIndex ? 'bg-white w-10' : 'bg-white bg-opacity-50'} hover:bg-white"></button>
                        `).join('')}
                    </div>
                </section>

                <!-- Services Section -->
                <section id="services" class="py-32 px-4" style="background-color: #D8E2DC">
                    <div class="max-w-7xl mx-auto">
                        <div class="text-center mb-24">
                            <p class="text-sm font-bold tracking-widest mb-3" style="color: #F97316">SERVICES</p>
                            <h2 class="text-6xl md:text-7xl font-black mb-6" style="color: #9D8189">What I Offer</h2>
                            <p class="text-xl text-gray-700 max-w-2xl mx-auto">Comprehensive executive support designed for ambitious leaders</p>
                        </div>
                        <div class="grid md:grid-cols-3 gap-8">
                            ${services.map(service => `
                                <div class="service-card relative h-96 rounded-2xl overflow-hidden shadow-xl hover:shadow-2xl transition-shadow">
                                    <img src="${service.image}" alt="${service.title}" />
                                    <div class="service-overlay">
                                        <h3 class="text-2xl">${service.title}</h3>
                                    </div>
                                </div>
                            `).join('')}
                        </div>
                    </div>
                </section>

                <!-- CTA Section -->
                <section class="py-40 px-4" style="background-color: #F97316">
                    <div class="max-w-5xl mx-auto text-center">
                        <h2 class="text-6xl md:text-7xl font-black text-white mb-10 leading-tight">Let's Transform Your Executive Operations</h2>
                        <p class="text-2xl text-white mb-12 max-w-2xl mx-auto">Schedule a consultation to discover how I can elevate your business.</p>
                        <button class="px-12 py-6 rounded-full font-bold text-lg text-white transition-all hover:shadow-2xl hover:scale-105" style="background-color: #9D8189">Book Your Consultation →</button>
                    </div>
                </section>

                <!-- Footer -->
                <footer class="py-20 px-4" style="background-color: #9D8189">
                    <div class="max-w-7xl mx-auto">
                        <div class="grid md:grid-cols-4 gap-12 mb-12">
                            <div>
                                <p class="text-4xl font-black text-white mb-2">CEO • Noir</p>
                                <p class="text-amber-50">Excellence in Executive Support</p>
                            </div>
                            <div>
                                <p class="font-black text-white mb-4 text-lg">Services</p>
                                <div class="space-y-2 text-amber-50">
                                    <p>Executive Admin</p>
                                    <p>Digital Marketing</p>
                                    <p>Financial Management</p>
                                </div>
                            </div>
                            <div>
                                <p class="font-black text-white mb-4 text-lg">Company</p>
                                <div class="space-y-2 text-amber-50">
                                    <p>About</p>
                                    <p>Testimonials</p>
                                    <p>Blog</p>
                                </div>
                            </div>
                            <div>
                                <p class="font-black text-white mb-4 text-lg">Contact</p>
                                <p class="text-amber-50 mb-2">hello@ceonoir.co</p>
                                <p class="text-amber-50">+1 (555) 000-0000</p>
                            </div>
                        </div>
                        <div class="border-t pt-8" style="border-color: rgba(255,255,255,0.2)">
                            <p class="text-center text-amber-50">© 2025 CEO Noir & Co. All rights reserved.</p>
                        </div>
                    </div>
                </footer>
            `;
        }

        function changeImage(idx) {
            currentImageIndex = idx;
            render();
        }

        setInterval(() => {
            currentImageIndex = (currentImageIndex + 1) % heroImages.length;
            render();
        }, 5000);

        window.addEventListener('scroll', () => {
            scrolled = window.scrollY > 50;
            render();
        });

        render();
    </script>
</body>
</html>
