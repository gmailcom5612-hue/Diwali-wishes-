# Diwali-wishes-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shubh Deepavali - Respected Bua Ji & Fufa Ji 🪔✨</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts for Traditional & Royal Indian Typography -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@600;700;800;900&family=Great+Vibes&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&family=Rozha+One&display=swap" rel="stylesheet">

    <style>
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background: #14050a;
            color: #fff7ed;
            overflow-x: hidden;
            touch-action: manipulation;
        }

        .font-royal {
            font-family: 'Cinzel', serif;
        }

        .font-traditional {
            font-family: 'Rozha One', serif;
        }

        .font-handwritten {
            font-family: 'Great Vibes', cursive;
        }

        /* Interactive Canvas Overlay */
        #fireworksCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: auto;
            z-index: 10;
        }

        /* Diya Flame Flickering Animation */
        .flame-outer {
            transform-origin: center bottom;
            animation: diyaFlicker 1.3s infinite ease-in-out alternate;
        }

        .flame-inner {
            transform-origin: center bottom;
            animation: diyaInnerFlicker 0.9s infinite ease-in-out alternate;
        }

        @keyframes diyaFlicker {
            0% { transform: scale(1) rotate(-1.5deg); filter: drop-shadow(0 0 12px #f59e0b); }
            50% { transform: scale(1.09, 1.14) rotate(2deg); filter: drop-shadow(0 0 22px #d97706); }
            100% { transform: scale(0.97, 1.03) rotate(-2deg); filter: drop-shadow(0 0 15px #f59e0b); }
        }

        @keyframes diyaInnerFlicker {
            0% { transform: scale(0.98); }
            100% { transform: scale(1.15, 1.12); }
        }

        /* Rotating Sacred Rangoli Mandala */
        .rangoli-spin {
            animation: spinMandala 85s linear infinite;
        }

        @keyframes spinMandala {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        /* Royal Traditional Glassmorphic Card */
        .royal-card {
            background: linear-gradient(145deg, rgba(38, 12, 21, 0.88), rgba(20, 5, 12, 0.94));
            backdrop-filter: blur(18px);
            -webkit-backdrop-filter: blur(18px);
            border: 1.5px solid rgba(245, 158, 11, 0.35);
            box-shadow: 0 25px 60px rgba(0, 0, 0, 0.75), 0 0 35px rgba(245, 158, 11, 0.2);
        }

        /* Gold Gradient Text & Effects */
        .glow-gold-text {
            text-shadow: 0 0 15px rgba(251, 191, 36, 0.5), 0 0 30px rgba(217, 119, 6, 0.4);
        }

        /* Golden Shimmer Button */
        .btn-gold-shimmer {
            background: linear-gradient(110deg, #92400e 0%, #d97706 25%, #fbbf24 50%, #d97706 75%, #92400e 100%);
            background-size: 200% 100%;
            animation: goldShimmer 3.5s infinite;
        }

        @keyframes goldShimmer {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }

        /* Floating Marigold Petals / Sparkles */
        @keyframes floatPetal {
            0% {
                transform: translateY(0) rotate(0deg) scale(0.6);
                opacity: 1;
            }
            100% {
                transform: translateY(-130px) rotate(180deg) scale(1.1);
                opacity: 0;
            }
        }

        .floating-petal {
            position: absolute;
            pointer-events: none;
            animation: floatPetal 3s ease-out forwards;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between items-center relative select-none">

    <!-- Deep Red/Royal Purple Background Gradient -->
    <div class="fixed inset-0 z-0 bg-gradient-to-b from-[#240713] via-[#14040a] to-[#0a0205] transition-colors duration-1000"></div>

    <!-- Interactive Canvas for Festive Sky Fireworks -->
    <canvas id="fireworksCanvas"></canvas>

    <!-- Top Navigation Bar & Customization -->
    <header class="w-full max-w-4xl mx-auto p-4 flex justify-between items-center z-20 relative">
        <div class="flex items-center gap-2">
            <span class="inline-block w-2.5 h-2.5 rounded-full bg-amber-400 animate-ping"></span>
            <span class="text-xs uppercase tracking-widest text-amber-200/90 font-semibold font-royal">Traditional Diwali Wish</span>
        </div>

        <div class="flex items-center gap-2 sm:gap-3">
            <!-- Share/Copy Link Button -->
            <button id="shareLinkBtn" class="px-3 py-1.5 rounded-full text-xs bg-amber-500/20 hover:bg-amber-500/30 border border-amber-400/40 text-amber-200 transition flex items-center gap-1.5 shadow-md">
                <i class="fa-solid fa-share-nodes text-amber-400"></i>
                <span class="hidden sm:inline">Share Wish</span>
            </button>

            <!-- Edit Name/Message Button -->
            <button id="openModalBtn" class="px-3 py-1.5 rounded-full text-xs bg-amber-950/40 hover:bg-amber-900/60 border border-amber-500/40 text-amber-200 transition flex items-center gap-1.5 shadow-md">
                <i class="fa-solid fa-pen-nib text-amber-400"></i>
                <span id="nameTagDisplay">Bua Ji & Fufa Ji</span>
            </button>

            <!-- Audio Controller Button -->
            <button id="audioToggle" class="w-9 h-9 sm:w-10 sm:h-10 rounded-full bg-amber-950/40 hover:bg-amber-900/60 border border-amber-500/40 text-amber-300 flex items-center justify-center transition shadow-md">
                <i id="audioIcon" class="fa-solid fa-music"></i>
            </button>
        </div>
    </header>

    <!-- Timeline Progress Indicator (8-Second Automated Sequence) -->
    <div class="w-full max-w-md px-4 z-20 my-1">
        <div class="flex justify-between text-[11px] text-amber-300/70 font-mono mb-1">
            <span id="stageLabel">Phase 1: Lighting the Sacred Diya</span>
            <span id="timerLabel">0.0s / 8.0s</span>
        </div>
        <div class="w-full h-1.5 bg-black/40 rounded-full overflow-hidden border border-amber-500/20">
            <div id="progressBar" class="h-full bg-gradient-to-r from-amber-600 via-yellow-400 to-amber-300 w-0 transition-all duration-100"></div>
        </div>
    </div>

    <!-- MAIN INTERACTIVE CONTENT CONTAINER -->
    <main class="w-full max-w-2xl px-4 flex-1 flex flex-col justify-center items-center z-20 my-auto relative">

        <!-- STAGE 1 & 2: Diya & Traditional Rangoli Mandala -->
        <div id="diyaSection" class="relative flex flex-col items-center justify-center transition-all duration-1000 transform scale-100 my-4">
            
            <!-- Traditional Rangoli SVG Pattern (Fades in ~2.5s) -->
            <div id="rangoliContainer" class="absolute w-[300px] h-[300px] sm:w-[390px] sm:h-[390px] opacity-0 transition-opacity duration-1000 pointer-events-none flex items-center justify-center">
                <svg class="rangoli-spin w-full h-full text-amber-400/40" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <circle cx="100" cy="100" r="95" stroke="currentColor" stroke-width="1.2" stroke-dasharray="3 3"/>
                    <circle cx="100" cy="100" r="82" stroke="currentColor" stroke-width="1"/>
                    <circle cx="100" cy="100" r="60" stroke="#f59e0b" stroke-width="1.5" stroke-opacity="0.6"/>
                    
                    <!-- Decorative Rangoli Petals -->
                    <g stroke="currentColor" stroke-width="1.5" fill="none">
                        <path d="M100 18 Q125 58 100 98 Q75 58 100 18Z"/>
                        <path d="M100 182 Q125 142 100 102 Q75 142 100 182Z"/>
                        <path d="M18 100 Q58 125 98 100 Q58 75 18 100Z"/>
                        <path d="M182 100 Q142 125 102 100 Q142 75 182 100Z"/>
                        <path d="M42 42 Q80 70 100 100 Q70 80 42 42Z"/>
                        <path d="M158 158 Q120 130 100 100 Q130 120 158 158Z"/>
                        <path d="M158 42 Q130 80 100 100 Q120 70 158 42Z"/>
                        <path d="M42 158 Q70 120 100 100 Q80 130 42 158Z"/>
                    </g>
                    <!-- Sacred Dots (Bindu Motif) -->
                    <circle cx="100" cy="8" r="3.5" fill="#f59e0b"/>
                    <circle cx="100" cy="192" r="3.5" fill="#f59e0b"/>
                    <circle cx="8" cy="100" r="3.5" fill="#f59e0b"/>
                    <circle cx="192" cy="100" r="3.5" fill="#f59e0b"/>
                    <circle cx="35" cy="35" r="2.5" fill="#ef4444"/>
                    <circle cx="165" cy="165" r="2.5" fill="#ef4444"/>
                    <circle cx="165" cy="35" r="2.5" fill="#ef4444"/>
                    <circle cx="35" cy="165" r="2.5" fill="#ef4444"/>
                </svg>
            </div>

            <!-- Sacred Brass Diya Artwork (SVG) -->
            <div id="diyaTouchArea" class="cursor-pointer relative z-30 transition-transform hover:scale-105 active:scale-95 group">
                
                <!-- Ambient Warm Diya Glow -->
                <div id="flameAmbientGlow" class="absolute -top-14 left-1/2 -translate-x-1/2 w-32 h-32 bg-amber-500/0 rounded-full blur-2xl transition-all duration-1000 pointer-events-none"></div>

                <svg class="w-48 h-48 sm:w-60 sm:h-60 drop-shadow-2xl overflow-visible" viewBox="0 0 200 200">
                    <defs>
                        <radialGradient id="flameOuter" cx="50%" cy="85%" r="65%">
                            <stop offset="0%" stop-color="#fffbeb"/>
                            <stop offset="30%" stop-color="#f59e0b"/>
                            <stop offset="70%" stop-color="#dc2626"/>
                            <stop offset="100%" stop-color="#7f1d1d" stop-opacity="0"/>
                        </radialGradient>
                        <radialGradient id="flameCore" cx="50%" cy="50%" r="50%">
                            <stop offset="0%" stop-color="#ffffff"/>
                            <stop offset="65%" stop-color="#fef08a"/>
                            <stop offset="100%" stop-color="#f59e0b"/>
                        </radialGradient>
                        <!-- Brass Metallic Diya Gradient -->
                        <linearGradient id="brassGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                            <stop offset="0%" stop-color="#fef08a"/>
                            <stop offset="30%" stop-color="#d97706"/>
                            <stop offset="70%" stop-color="#78350f"/>
                            <stop offset="100%" stop-color="#451a03"/>
                        </linearGradient>
                        <linearGradient id="goldHighlight" x1="0%" y1="0%" x2="100%" y2="0%">
                            <stop offset="0%" stop-color="#fef08a"/>
                            <stop offset="50%" stop-color="#f59e0b"/>
                            <stop offset="100%" stop-color="#b45309"/>
                        </linearGradient>
                    </defs>

                    <!-- Diya Base Shadow -->
                    <ellipse cx="100" cy="168" rx="70" ry="14" fill="rgba(0,0,0,0.6)" filter="blur(5px)"/>

                    <!-- Diya Brass Body -->
                    <path d="M 25 110 C 25 170, 175 170, 175 110 C 150 128, 130 133, 100 133 C 70 133, 50 128, 25 110 Z" 
                          fill="url(#brassGrad)" stroke="#fef08a" stroke-width="1.5"/>

                    <!-- Intricate Carved Rim -->
                    <path d="M 23 110 C 60 129, 140 129, 177 110 C 145 119, 55 119, 23 110 Z" 
                          fill="url(#goldHighlight)"/>
                    
                    <!-- Decorative Motif Dots on Diya -->
                    <circle cx="100" cy="146" r="3.5" fill="#fef08a"/>
                    <circle cx="78" cy="142" r="2.5" fill="#fef08a"/>
                    <circle cx="122" cy="142" r="2.5" fill="#fef08a"/>
                    <circle cx="58" cy="134" r="2" fill="#fef08a"/>
                    <circle cx="142" cy="134" r="2" fill="#fef08a"/>

                    <!-- Flame Group -->
                    <g id="flameGroup" class="transition-all duration-1000 opacity-0 transform scale-50" style="transform-origin: 100px 105px;">
                        <!-- Outer Flame -->
                        <path class="flame-outer" d="M 100 25 Q 128 72 114 104 C 106 114 94 114 86 104 Q 72 72 100 25 Z" 
                              fill="url(#flameOuter)"/>
                        <!-- Inner Flame Core -->
                        <path class="flame-inner" d="M 100 52 Q 113 82 107 102 C 103 107 97 107 93 102 Q 87 82 100 52 Z" 
                              fill="url(#flameCore)"/>
                        <!-- Wick Center -->
                        <ellipse cx="100" cy="105" rx="2.5" ry="1.8" fill="#ffffff"/>
                    </g>
                </svg>

                <div class="text-center mt-1">
                    <span id="diyaHint" class="text-[11px] text-amber-300/70 uppercase tracking-widest block transition-opacity duration-500 font-royal">
                        Tap Diya to seek blessings ✨
                    </span>
                </div>
            </div>
        </div>

        <!-- STAGE 3: Traditional Respectful Diwali Wish Card (Reveals ~5.0s) -->
        <div id="wishCard" class="royal-card w-full rounded-3xl p-6 sm:p-9 text-center transition-all duration-1000 transform opacity-0 translate-y-8 scale-95 pointer-events-none absolute relative z-40">
            
            <!-- Traditional Subheading Tag -->
            <div class="inline-flex items-center gap-2 px-3.5 py-1 rounded-full bg-amber-500/15 border border-amber-500/35 mb-3">
                <i class="fa-solid fa-om text-amber-400 text-xs"></i>
                <span class="text-amber-200 text-xs uppercase tracking-widest font-semibold font-royal">Shubh Deepavali Blessings</span>
                <i class="fa-solid fa-om text-amber-400 text-xs"></i>
            </div>

            <!-- Respectful Heading -->
            <h1 class="text-2xl sm:text-4xl font-traditional text-transparent bg-clip-text bg-gradient-to-r from-amber-200 via-yellow-400 to-amber-100 mb-2 glow-gold-text">
                Happy Diwali, <br/>
                <span id="targetName" class="font-royal text-3xl sm:text-5xl text-amber-300 font-bold block mt-1">Respected Bua Ji & Fufa Ji</span>
            </h1>

            <!-- Respectful & Warm Message -->
            <p id="targetMessage" class="text-amber-100/90 text-sm sm:text-base font-light leading-relaxed max-w-lg mx-auto my-4">
                "Pranaam Bua Ji & Fufa Ji 🙏. On this holy festival of lights, seeking your divine blessings. May Lord Ganesha & Goddess Lakshmi fill your life with eternal health, happiness, prosperity, and peace."
            </p>

            <!-- Traditional Motif Divider -->
            <div class="flex items-center justify-center gap-3 my-4 opacity-80">
                <div class="h-px w-14 bg-gradient-to-r from-transparent to-amber-400"></div>
                <span class="text-amber-400 text-xs font-traditional">🪔 🌸 🪔</span>
                <div class="h-px w-14 bg-gradient-to-l from-transparent to-amber-400"></div>
            </div>

            <!-- Footer Closing Remark -->
            <p class="text-xs sm:text-sm text-amber-200/80 font-royal italic mb-6">
                Wishing you both a joyous and prosperous Deepavali! ✨
            </p>

            <!-- Action Buttons -->
            <div class="flex flex-wrap items-center justify-center gap-3 pointer-events-auto">
                <button id="replayBtn" class="btn-gold-shimmer text-slate-950 font-extrabold px-6 py-2.5 rounded-full text-xs sm:text-sm shadow-xl hover:shadow-amber-500/30 active:scale-95 transition flex items-center gap-2">
                    <i class="fa-solid fa-rotate-right"></i> Replay Wish (8s)
                </button>

                <button id="blessingsBtn" class="bg-amber-950/80 hover:bg-amber-900 border border-amber-500/50 text-amber-200 font-semibold px-5 py-2.5 rounded-full text-xs sm:text-sm active:scale-95 transition flex items-center gap-2">
                    <i class="fa-solid fa-hands-praying text-amber-400"></i> Offer Pranaam
                </button>
            </div>
        </div>

    </main>

    <!-- Footer Note -->
    <footer class="w-full max-w-4xl mx-auto p-4 text-center z-20 relative">
        <p class="text-[11px] text-amber-200/60 font-royal">
            <i class="fa-solid fa-sparkles text-amber-400 mr-1"></i> Tap anywhere on the sky to burst celebratory fireworks!
        </p>
    </footer>

    <!-- MODAL FOR CUSTOMIZING NAMES & MESSAGE -->
    <div id="nameModal" class="fixed inset-0 bg-black/85 backdrop-blur-md z-50 flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
        <div class="royal-card border border-amber-500/50 rounded-2xl p-6 w-full max-w-md shadow-2xl text-center transform scale-95 transition-transform duration-300" id="modalBox">
            <h3 class="text-xl font-bold text-amber-300 mb-1 font-royal">Personalize Wish</h3>
            <p class="text-xs text-amber-200/70 mb-4">Customize names and blessing message to share customized links</p>
            
            <label class="block text-left text-xs text-amber-300 font-semibold mb-1">Names / Title:</label>
            <input type="text" id="nameInput" placeholder="e.g. Respected Bua Ji & Fufa Ji" 
                   class="w-full bg-black/50 border border-amber-500/40 rounded-xl px-4 py-2.5 text-amber-100 placeholder-slate-500 text-sm focus:outline-none focus:border-amber-400 mb-4">
            
            <label class="block text-left text-xs text-amber-300 font-semibold mb-1">Blessing Message:</label>
            <textarea id="msgInput" rows="3" placeholder="Write your heartfelt message..." 
                      class="w-full bg-black/50 border border-amber-500/40 rounded-xl px-4 py-2.5 text-amber-100 placeholder-slate-500 text-xs sm:text-sm focus:outline-none focus:border-amber-400 mb-5 resize-none"></textarea>

            <div class="flex gap-3">
                <button id="cancelModalBtn" class="w-1/2 py-2.5 rounded-xl text-xs bg-white/5 hover:bg-white/10 text-amber-200 border border-white/10 transition">Cancel</button>
                <button id="saveModalBtn" class="w-1/2 py-2.5 rounded-xl text-xs bg-amber-500 hover:bg-amber-400 text-slate-950 font-bold transition">Save & Apply</button>
            </div>
        </div>
    </div>

    <!-- TOAST NOTIFICATION FOR LINK COPYING -->
    <div id="toast" class="fixed bottom-6 left-1/2 -translate-x-1/2 z-50 bg-amber-500 text-slate-950 px-5 py-2.5 rounded-full text-xs font-bold shadow-2xl transition-all duration-300 opacity-0 pointer-events-none transform translate-y-4 flex items-center gap-2">
        <i class="fa-solid fa-circle-check"></i>
        <span id="toastMsg">Shareable link copied to clipboard!</span>
    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        /* ===================================================================
           1. URL PARAMETER PARSER (Enable Sharing Custom Names/Messages)
           =================================================================== */
        function loadParamsFromURL() {
            const urlParams = new URLSearchParams(window.location.search);
            const name = urlParams.get('to');
            const msg = urlParams.get('msg');

            if (name) {
                document.getElementById('targetName').innerText = name;
                document.getElementById('nameTagDisplay').innerText = name;
            }
            if (msg) {
                document.getElementById('targetMessage').innerText = `"${msg}"`;
            }
        }
        loadParamsFromURL();

        function showToast(message) {
            const toast = document.getElementById('toast');
            const toastMsg = document.getElementById('toastMsg');
            toastMsg.innerText = message;
            toast.classList.remove('opacity-0', 'pointer-events-none', 'translate-y-4');
            toast.classList.add('opacity-100', 'translate-y-0');

            setTimeout(() => {
                toast.classList.remove('opacity-100', 'translate-y-0');
                toast.classList.add('opacity-0', 'pointer-events-none', 'translate-y-4');
            }, 3000);
        }

        /* ===================================================================
           2. WEB AUDIO API SYNTHESIZER (Festive Classical Tones & Explosions)
           =================================================================== */
        class TraditionalAudioSynth {
            constructor() {
                this.ctx = null;
                this.isPlaying = false;
                this.interval = null;
            }

            init() {
                if (!this.ctx) {
                    const AudioCtx = window.AudioContext || window.webkitAudioContext;
                    this.ctx = new AudioCtx();
                }
                if (this.ctx.state === 'suspended') {
                    this.ctx.resume();
                }
            }

            playHarmonicNote(freq, duration = 2.2) {
                if (!this.ctx || !this.isPlaying) return;
                try {
                    const osc = this.ctx.createOscillator();
                    const gain = this.ctx.createGain();
                    
                    osc.type = 'triangle'; // Warm acoustic timbre
                    osc.frequency.setValueAtTime(freq, this.ctx.currentTime);
                    
                    gain.gain.setValueAtTime(0, this.ctx.currentTime);
                    gain.gain.linearRampToValueAtTime(0.12, this.ctx.currentTime + 0.15);
                    gain.gain.exponentialRampToValueAtTime(0.001, this.ctx.currentTime + duration);

                    osc.connect(gain);
                    gain.connect(this.ctx.destination);

                    osc.start();
                    osc.stop(this.ctx.currentTime + duration);
                } catch(e){}
            }

            playBurstSound() {
                if (!this.ctx || !this.isPlaying) return;
                try {
                    const bufferSize = this.ctx.sampleRate * 0.12;
                    const buffer = this.ctx.createBuffer(1, bufferSize, this.ctx.sampleRate);
                    const data = buffer.getChannelData(0);
                    for (let i = 0; i < bufferSize; i++) {
                        data[i] = Math.random() * 2 - 1;
                    }

                    const noise = this.ctx.createBufferSource();
                    noise.buffer = buffer;

                    const filter = this.ctx.createBiquadFilter();
                    filter.type = 'bandpass';
                    filter.frequency.value = 800 + Math.random() * 1400;

                    const gain = this.ctx.createGain();
                    gain.gain.setValueAtTime(0.09, this.ctx.currentTime);
                    gain.gain.exponentialRampToValueAtTime(0.001, this.ctx.currentTime + 0.12);

                    noise.connect(filter);
                    filter.connect(gain);
                    gain.connect(this.ctx.destination);

                    noise.start();
                } catch(e){}
            }

            startFestiveMelody() {
                this.init();
                this.isPlaying = true;
                
                const indianNotes = [220.00, 246.94, 277.18, 329.63, 369.99, 440.00, 493.88];

                if (this.interval) clearInterval(this.interval);

                this.interval = setInterval(() => {
                    if (!this.isPlaying) return;
                    const freq = indianNotes[Math.floor(Math.random() * indianNotes.length)];
                    this.playHarmonicNote(freq, 2.5);
                }, 900);
            }

            stop() {
                this.isPlaying = false;
                if (this.interval) clearInterval(this.interval);
            }
        }

        const audioSynth = new TraditionalAudioSynth();

        /* ===================================================================
           3. FIREWORKS & SPARKLE CANVAS ENGINE
           =================================================================== */
        const canvas = document.getElementById('fireworksCanvas');
        const ctx = canvas.getContext('2d');
        let particles = [];
        let width = canvas.width = window.innerWidth;
        let height = canvas.height = window.innerHeight;

        window.addEventListener('resize', () => {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
        });

        class Particle {
            constructor(x, y, color, speed, angle) {
                this.x = x;
                this.y = y;
                this.color = color;
                this.vx = Math.cos(angle) * speed;
                this.vy = Math.sin(angle) * speed;
                this.friction = 0.96;
                this.gravity = 0.04;
                this.alpha = 1;
                this.decay = Math.random() * 0.014 + 0.008;
                this.size = Math.random() * 3 + 1.2;
            }

            update() {
                this.vx *= this.friction;
                this.vy *= this.friction;
                this.vy += this.gravity;
                this.x += this.vx;
                this.y += this.vy;
                this.alpha -= this.decay;
            }

            draw() {
                ctx.save();
                ctx.globalAlpha = Math.max(0, this.alpha);
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.shadowBlur = 12;
                ctx.shadowColor = this.color;
                ctx.fill();
                ctx.restore();
            }
        }

        function createFirework(x, y, particleCount = 45) {
            const palette = ['#fbbf24', '#f59e0b', '#ef4444', '#dc2626', '#38bdf8', '#ffffff'];
            const color = palette[Math.floor(Math.random() * palette.length)];
            
            for (let i = 0; i < particleCount; i++) {
                const angle = (Math.PI * 2 / particleCount) * i + (Math.random() * 0.2);
                const speed = Math.random() * 6.5 + 2;
                particles.push(new Particle(x, y, color, speed, angle));
            }
            audioSynth.playBurstSound();
        }

        function renderCanvas() {
            ctx.fillStyle = 'rgba(20, 5, 10, 0.22)';
            ctx.fillRect(0, 0, width, height);

            for (let i = particles.length - 1; i >= 0; i--) {
                particles[i].update();
                particles[i].draw();
                if (particles[i].alpha <= 0) {
                    particles.splice(i, 1);
                }
            }
            requestAnimationFrame(renderCanvas);
        }
        renderCanvas();

        window.addEventListener('click', (e) => {
            if (e.target.closest('button') || e.target.closest('#nameModal')) return;
            createFirework(e.clientX, e.clientY, 40);
        });

        /* ===================================================================
           4. 8-SECOND AUTOMATED TIMELINE ANIMATION LOGIC
           =================================================================== */
        let animationStartTime = null;
        let animationDuration = 8000;
        let timelineReq = null;

        const flameGroup = document.getElementById('flameGroup');
        const flameAmbientGlow = document.getElementById('flameAmbientGlow');
        const diyaSection = document.getElementById('diyaSection');
        const rangoliContainer = document.getElementById('rangoliContainer');
        const wishCard = document.getElementById('wishCard');
        const progressBar = document.getElementById('progressBar');
        const stageLabel = document.getElementById('stageLabel');
        const timerLabel = document.getElementById('timerLabel');
        const diyaHint = document.getElementById('diyaHint');

        function start8SecondAnimation() {
            animationStartTime = performance.now();
            
            flameGroup.style.opacity = '0';
            flameGroup.style.transform = 'scale(0.2)';
            flameAmbientGlow.style.backgroundColor = 'rgba(245, 158, 11, 0)';

            rangoliContainer.style.opacity = '0';
            rangoliContainer.style.transform = 'scale(0.6) rotate(0deg)';

            wishCard.style.opacity = '0';
            wishCard.style.transform = 'translateY(35px) scale(0.95)';
            wishCard.style.pointerEvents = 'none';

            diyaSection.style.transform = 'scale(1) translateY(0px)';
            diyaHint.style.opacity = '1';

            let bursts = { b1: false, b2: false, b3: false };

            function updateTimeline(now) {
                const elapsed = now - animationStartTime;
                const progress = Math.min(1, elapsed / animationDuration);
                const seconds = (elapsed / 1000).toFixed(1);

                progressBar.style.width = `${progress * 100}%`;
                timerLabel.innerText = `${Math.min(8.0, seconds)}s / 8.0s`;

                // --- PHASE 1: 0.0s – 2.5s ---
                if (elapsed < 2500) {
                    stageLabel.innerText = "Phase 1: Lighting the Sacred Diya";
                    
                    const p1 = Math.min(1, elapsed / 2200);
                    flameGroup.style.opacity = p1;
                    flameGroup.style.transform = `scale(${0.3 + p1 * 0.7})`;
                    flameAmbientGlow.style.backgroundColor = `rgba(245, 158, 11, ${p1 * 0.45})`;
                    flameAmbientGlow.style.transform = `translate(-50%, 0) scale(${1 + p1 * 0.5})`;
                }

                // --- PHASE 2: 2.5s – 5.0s ---
                else if (elapsed >= 2500 && elapsed < 5000) {
                    stageLabel.innerText = "Phase 2: Sacred Rangoli & Sky Fireworks";
                    
                    const p2 = Math.min(1, (elapsed - 2500) / 2000);
                    rangoliContainer.style.opacity = p2 * 0.85;
                    rangoliContainer.style.transform = `scale(${0.75 + p2 * 0.25})`;

                    if (elapsed > 2700 && !bursts.b1) {
                        bursts.b1 = true;
                        createFirework(width * 0.22, height * 0.28, 45);
                        createFirework(width * 0.78, height * 0.24, 45);
                    }
                    if (elapsed > 3900 && !bursts.b2) {
                        bursts.b2 = true;
                        createFirework(width * 0.5, height * 0.18, 50);
                    }
                }

                // --- PHASE 3: 5.0s – 8.0s ---
                else if (elapsed >= 5000) {
                    stageLabel.innerText = "Phase 3: Traditional Blessings Reveal";
                    
                    const p3 = Math.min(1, (elapsed - 5000) / 2000);
                    
                    diyaSection.style.transform = `scale(0.85) translateY(-8px)`;
                    diyaHint.style.opacity = '0';

                    wishCard.style.opacity = p3;
                    wishCard.style.transform = `translateY(${35 - p3 * 35}px) scale(${0.95 + p3 * 0.05})`;

                    if (elapsed > 6000 && !bursts.b3) {
                        bursts.b3 = true;
                        wishCard.style.pointerEvents = 'auto';
                        createFirework(width * 0.18, height * 0.38, 40);
                        createFirework(width * 0.82, height * 0.38, 40);
                    }
                }

                if (progress < 1) {
                    timelineReq = requestAnimationFrame(updateTimeline);
                } else {
                    stageLabel.innerText = "Wish Complete! Tap anywhere to burst fireworks ✨";
                }
            }

            if (timelineReq) cancelAnimationFrame(timelineReq);
            timelineReq = requestAnimationFrame(updateTimeline);
        }

        window.addEventListener('load', () => {
            setTimeout(start8SecondAnimation, 300);
        });

        document.getElementById('replayBtn').addEventListener('click', () => {
            start8SecondAnimation();
        });

        /* ===================================================================
           5. MICRO-INTERACTIONS & SHARE LOGIC
           =================================================================== */
        const diyaTouchArea = document.getElementById('diyaTouchArea');
        const blessingsBtn = document.getElementById('blessingsBtn');
        const shareLinkBtn = document.getElementById('shareLinkBtn');

        function spawnFloatingPetal(x, y) {
            const petal = document.createElement('div');
            petal.className = 'floating-petal text-amber-400 text-lg sm:text-2xl z-50';
            petal.innerHTML = '🌸';
            petal.style.left = `${x - 12}px`;
            petal.style.top = `${y - 12}px`;
            document.body.appendChild(petal);

            setTimeout(() => petal.remove(), 3000);
        }

        diyaTouchArea.addEventListener('click', (e) => {
            e.stopPropagation();
            
            flameGroup.style.transform = 'scale(1.35)';
            flameAmbientGlow.style.backgroundColor = 'rgba(251, 191, 36, 0.85)';
            setTimeout(() => {
                flameGroup.style.transform = 'scale(1)';
                flameAmbientGlow.style.backgroundColor = 'rgba(245, 158, 11, 0.45)';
            }, 450);

            const rect = diyaTouchArea.getBoundingClientRect();
            for (let i = 0; i < 6; i++) {
                setTimeout(() => {
                    const rx = rect.left + rect.width / 2 + (Math.random() - 0.5) * 50;
                    const ry = rect.top + 20;
                    spawnFloatingPetal(rx, ry);
                }, i * 90);
            }

            audioSynth.playHarmonicNote(523.25, 1.2);
        });

        blessingsBtn.addEventListener('click', () => {
            const rect = blessingsBtn.getBoundingClientRect();
            for (let i = 0; i < 10; i++) {
                setTimeout(() => {
                    const rx = rect.left + Math.random() * rect.width;
                    const ry = rect.top;
                    spawnFloatingPetal(rx, ry);
                    createFirework(rx, ry - 40, 18);
                }, i * 70);
            }
        });

        shareLinkBtn.addEventListener('click', () => {
            const name = document.getElementById('targetName').innerText.replace('\n', ' ');
            const msg = document.getElementById('targetMessage').innerText.replace(/^"|"$/g, '');
            
            const shareUrl = `${window.location.origin}${window.location.pathname}?to=${encodeURIComponent(name)}&msg=${encodeURIComponent(msg)}`;
            
            const tempInput = document.createElement('input');
            tempInput.value = shareUrl;
            document.body.appendChild(tempInput);
            tempInput.select();
            document.execCommand('copy');
            document.body.removeChild(tempInput);
            
            showToast("Shareable link copied to clipboard!");
        });

        /* ===================================================================
           6. AUDIO CONTROLLER
           =================================================================== */
        const audioToggle = document.getElementById('audioToggle');
        const audioIcon = document.getElementById('audioIcon');

        audioToggle.addEventListener('click', (e) => {
            e.stopPropagation();
            if (audioSynth.isPlaying) {
                audioSynth.stop();
                audioIcon.className = 'fa-solid fa-music opacity-50';
            } else {
                audioSynth.startFestiveMelody();
                audioIcon.className = 'fa-solid fa-volume-high text-amber-300 animate-pulse';
            }
        });

        window.addEventListener('click', () => {
            if (!audioSynth.ctx) {
                audioSynth.init();
            }
        }, { once: true });

        /* ===================================================================
           7. MODAL DIALOG CONTROLLER
           =================================================================== */
        const openModalBtn = document.getElementById('openModalBtn');
        const nameModal = document.getElementById('nameModal');
        const modalBox = document.getElementById('modalBox');
        const cancelModalBtn = document.getElementById('cancelModalBtn');
        const saveModalBtn = document.getElementById('saveModalBtn');
        const nameInput = document.getElementById('nameInput');
        const msgInput = document.getElementById('msgInput');
        const targetName = document.getElementById('targetName');
        const targetMessage = document.getElementById('targetMessage');
        const nameTagDisplay = document.getElementById('nameTagDisplay');

        function toggleModal(show) {
            if (show) {
                nameModal.classList.remove('opacity-0', 'pointer-events-none');
                modalBox.classList.remove('scale-95');
                modalBox.classList.add('scale-100');
                nameInput.value = targetName.innerText.replace('\n', ' ');
                msgInput.value = targetMessage.innerText.replace(/^"|"$/g, '');
                nameInput.focus();
            } else {
                nameModal.classList.add('opacity-0', 'pointer-events-none');
                modalBox.classList.remove('scale-100');
                modalBox.classList.add('scale-95');
            }
        }

        openModalBtn.addEventListener('click', (e) => {
            e.stopPropagation();
            toggleModal(true);
        });

        cancelModalBtn.addEventListener('click', () => toggleModal(false));

        saveModalBtn.addEventListener('click', () => {
            const nameVal = nameInput.value.trim();
            const msgVal = msgInput.value.trim();

            if (nameVal) {
                targetName.innerText = nameVal;
                nameTagDisplay.innerText = nameVal;
            }
            if (msgVal) {
                targetMessage.innerText = `"${msgVal}"`;
            }
            toggleModal(false);
            showToast("Wish updated! Use 'Share Wish' to copy customized link.");
        });
    </script>
</body>
</html>
