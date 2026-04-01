<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laxman Khot - Film & Creative</title>
    <!-- Importing Cinematic Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #070707;
            --fg: #e2e2e2;
            --grey: #666666;
            --dark-border: #1a1a1a;
        }

        body {
            margin: 0;
            background-color: var(--bg);
            color: var(--fg);
            font-family: 'Inter', sans-serif;
            -webkit-font-smoothing: antialiased;
            overflow-x: hidden;
        }

        /* --- FILM GRAIN OVERLAY --- */
        .noise {
            position: fixed;
            top: 0; left: 0; width: 100vw; height: 100vh;
            pointer-events: none;
            z-index: 9999;
            opacity: 0.05;
            background-image: url('data:image/svg+xml;utf8,%3Csvg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg"%3E%3Cfilter id="noiseFilter"%3E%3CfeTurbulence type="fractalNoise" baseFrequency="0.8" numOctaves="3" stitchTiles="stitch"/%3E%3C/filter%3E%3Crect width="100%25" height="100%25" filter="url(%23noiseFilter)"/%3E%3C/svg%3E');
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 40px;
            position: relative;
            z-index: 10;
        }

        /* --- VIEWFINDER TOP BAR --- */
        .top-bar {
            display: flex;
            justify-content: space-between;
            padding: 30px 0;
            font-size: 0.75rem;
            letter-spacing: 2px;
            color: var(--grey);
            border-bottom: 1px solid var(--dark-border);
            text-transform: uppercase;
        }
        .top-bar .rec {
            color: #d92525;
            animation: blink 2s infinite;
        }
        @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

        /* --- HERO SECTION --- */
        header {
            padding: 12vh 0 10vh;
            border-bottom: 1px solid var(--dark-border);
        }
        
        h1.hero {
            font-family: 'Playfair Display', serif;
            font-size: clamp(5rem, 15vw, 12rem);
            font-weight: 400;
            line-height: 0.85;
            letter-spacing: -0.02em;
            margin: 0;
            text-transform: uppercase;
            color: #ffffff;
        }

        .hero-role {
            font-family: 'Inter', sans-serif;
            margin-top: 40px;
            color: var(--grey);
            font-size: 0.9rem;
            letter-spacing: 4px;
            font-weight: 300;
        }

        /* --- SECTIONS --- */
        section {
            padding: 120px 0;
            border-bottom: 1px solid var(--dark-border);
        }

        .section-header {
            display: flex;
            align-items: baseline;
            gap: 20px;
            margin-bottom: 60px;
        }

        .section-num {
            font-family: 'Playfair Display', serif;
            font-size: 3rem;
            color: var(--grey);
            font-style: italic;
        }

        h2.section-title {
            font-family: 'Inter', sans-serif;
            font-size: 1rem;
            font-weight: 400;
            text-transform: uppercase;
            letter-spacing: 4px;
            color: var(--fg);
            margin: 0;
        }

        /* --- ABOUT GRID --- */
        .about-grid {
            display: grid;
            grid-template-columns: 1.2fr 0.8fr;
            gap: 100px;
        }

        .about-text p {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            line-height: 1.5;
            font-weight: 400;
            color: #b3b3b3;
            margin-top: 0;
            margin-bottom: 40px;
        }

        .about-text strong {
            color: var(--fg);
            font-weight: 400;
            font-style: italic;
        }

        .meta-list {
            margin-bottom: 50px;
        }

        .meta-title {
            font-size: 0.65rem;
            text-transform: uppercase;
            color: var(--grey);
            letter-spacing: 3px;
            margin-bottom: 20px;
            border-bottom: 1px solid var(--dark-border);
            padding-bottom: 10px;
        }

        ul.clean-list {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        ul.clean-list li {
            padding: 10px 0;
            font-size: 0.85rem;
            display: flex;
            justify-content: space-between;
            color: #a0a0a0;
            letter-spacing: 1px;
        }

        ul.clean-list li span {
            color: var(--grey);
            font-family: 'Playfair Display', serif;
            font-style: italic;
            font-size: 1rem;
        }

        /* --- PROJECT GRID --- */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 80px 40px;
        }

        .project-card {
            display: flex;
            flex-direction: column;
            group: hover;
        }

        .media-wrapper {
            position: relative;
            width: 100%;
            background: #000;
            margin-bottom: 25px;
            border: 1px solid #111;
        }

        .scroll-hint {
            position: absolute;
            top: -25px;
            right: 0;
            font-size: 0.55rem;
            letter-spacing: 3px;
            color: var(--grey);
            text-transform: uppercase;
        }

        .card-media {
            width: 100%;
            aspect-ratio: 16/9;
            display: flex;
            overflow-x: auto;
            scroll-snap-type: x mandatory;
        }
        
        .card-media::-webkit-scrollbar { height: 6px; }
        .card-media::-webkit-scrollbar-track { background: #111; }
        .card-media::-webkit-scrollbar-thumb { background: #333; border-radius: 3px; }
        .card-media::-webkit-scrollbar-thumb:hover { background: #555; }

        .card-media-item {
            flex: 0 0 100%;
            scroll-snap-align: center;
            height: 100%;
        }
        .card-media-item img, .card-media-item iframe {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border: none;
            filter: grayscale(100%) contrast(1.2) brightness(0.9);
            transition: filter 0.8s ease;
        }
        .project-card:hover .card-media-item img, 
        .project-card:hover .card-media-item iframe {
            filter: grayscale(0%) contrast(1) brightness(1);
        }

        .card-title {
            font-family: 'Playfair Display', serif;
            font-size: 2rem;
            font-weight: 400;
            margin: 0 0 10px 0;
            color: #fff;
        }

        .card-role {
            color: var(--grey);
            font-size: 0.7rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 15px;
        }

        .card-desc {
            font-size: 0.9rem;
            line-height: 1.6;
            color: #888;
            margin-bottom: 25px;
            font-weight: 300;
        }

        /* --- CERTIFICATE GRID --- */
        .cert-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
        }
        .cert-link {
            text-decoration: none;
            display: block;
        }
        .cert-item {
            transition: all 0.4s ease;
            display: flex;
            flex-direction: column;
            cursor: pointer;
        }
        .cert-media {
            width: 100%;
            aspect-ratio: 1.414; /* Standard certificate ratio */
            background: #0a0a0a;
            margin-bottom: 20px;
            border: 1px solid var(--dark-border);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--grey);
            font-family: 'Inter', sans-serif;
            font-size: 0.8rem;
            letter-spacing: 3px;
            text-transform: uppercase;
            transition: all 0.4s ease;
        }
        .cert-item:hover .cert-media {
            background: #151515;
            border-color: var(--grey);
            color: #fff;
            transform: translateY(-5px);
        }
        .cert-title {
            font-family: 'Playfair Display', serif;
            font-size: 1.5rem;
            color: var(--fg);
            margin: 0 0 10px 0;
            font-weight: 400;
            border-top: 1px solid var(--dark-border);
            padding-top: 15px;
            transition: border-color 0.3s ease, color 0.3s ease;
        }
        .cert-item:hover .cert-title {
            border-color: var(--grey);
            color: #fff;
        }
        .cert-org {
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            color: var(--grey);
        }

        /* --- CINEMATIC BUTTONS --- */
        .btn {
            display: inline-block;
            border: 1px solid var(--grey);
            background: transparent;
            color: var(--fg);
            text-decoration: none;
            text-transform: uppercase;
            padding: 14px 30px;
            font-size: 0.75rem;
            letter-spacing: 3px;
            transition: all 0.4s ease;
            cursor: pointer;
            width: fit-content;
        }

        .btn:hover {
            background: var(--fg);
            color: var(--bg);
            border-color: var(--fg);
        }

        .btn-small {
            padding: 10px 20px;
            font-size: 0.65rem;
            margin-top: auto;
        }

        /* --- ENHANCED FOOTER --- */
        footer {
            padding: 80px 40px;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            gap: 30px;
            color: var(--grey);
            font-size: 0.8rem;
            letter-spacing: 2px;
        }
        
        .footer-left {
            font-size: 0.75rem;
            text-transform: uppercase;
        }

        .footer-contact {
            display: flex;
            gap: 40px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .contact-item a {
            color: var(--fg);
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .contact-item a:hover {
            color: #ffffff;
        }

        .contact-icon {
            width: 18px;
            height: 18px;
            fill: none;
            stroke: var(--grey);
            stroke-width: 1.5;
            stroke-linecap: round;
            stroke-linejoin: round;
            transition: stroke 0.3s ease;
        }
        
        .contact-item:hover .contact-icon {
            stroke: var(--fg);
        }

        @media (max-width: 900px) {
            .about-grid { grid-template-columns: 1fr; gap: 60px; }
            .top-bar { flex-direction: column; gap: 10px; align-items: center; }
            footer { flex-direction: column; text-align: center; }
            .footer-contact { flex-direction: column; gap: 20px; align-items: center; }
            h1.hero { font-size: 4rem; }
        }
    </style>
</head>
<body>

    <!-- CSS Film Grain -->
    <div class="noise"></div>

    <div class="container">
        
        <div class="top-bar">
            <span>SYS. 01 / NEW DELHI</span>
            <span class="rec">[ REC • ]</span>
            <span>T/C 00:00:24:12</span>
        </div>

        <!-- HEADER -->
        <header>
            <h1 class="hero">Laxman<br>Khot.</h1>
            <div class="hero-role">DIRECTOR — CREATIVE STRATEGIST</div>
        </header>

        <!-- ABOUT SECTION -->
        <section>
            <div class="section-header">
                <span class="section-num">01</span>
                <h2 class="section-title">Director's Profile</h2>
            </div>
            
            <div class="about-grid">
                <div class="about-text">
                    <p>I am a media professional with on-set experience across Kannada feature films, independent filmmaking, and broadcast media — backed by creative strategy work at <strong>McCann Worldgroup.</strong></p>
                    <p>Having handled end-to-end production on independent short films, I understand everything from script analysis and location scouting to talent management, scheduling, and post-production. Fluent across multiple languages, I have a strong instinct for <strong>culturally authentic storytelling.</strong></p>
                    
                    <a href="./Laxman_Khot_CV_v19_1.docx" class="btn" download style="margin-top: 20px;">Download Resumé</a>
                </div>
                
                <div>
                    <div class="meta-list">
                        <div class="meta-title">Selected Experience</div>
                        <ul class="clean-list">
                            <li>Creative Copywriter <span>McCann Worldgroup</span></li>
                            <li>AI Linguist & Scriptwriter <span>Krutrim AI (Ola)</span></li>
                            <li>Editorial Design <span>College Newsletter</span></li>
                            <li>Copy Editor <span>NewFirst Kannada TV</span></li>
                            <li>Filmmaker <span>IFP 50-Hour Challenge</span></li>
                        </ul>
                    </div>

                    <div class="meta-list">
                        <div class="meta-title">Languages</div>
                        <ul class="clean-list">
                            <li>Hindi <span>Fluent</span></li>
                            <li>English <span>Proficient</span></li>
                            <li>Kannada <span>Native</span></li>
                            <li>Telugu / Tamil / Marathi / Malayalam <span>Basic</span></li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- FILMOGRAPHY -->
        <section>
            <div class="section-header">
                <span class="section-num">02</span>
                <h2 class="section-title">Filmography</h2>
            </div>
            
            <div class="projects-grid">
                
                <!-- YUVARATNA -->
                <div class="project-card">
                    <div class="media-wrapper">
                        <div class="scroll-hint">[ Swipe / Scroll -> ]</div>
                        <div class="card-media">
                            <div class="card-media-item">
                                <iframe src="https://www.youtube.com/embed/a1L1EviALUg" title="Yuvaratna Kannada" allowfullscreen></iframe>
                            </div>
                            <div class="card-media-item">
                                <iframe src="https://www.youtube.com/embed/o_E53tfZP1A" title="Yuvaratna Hindi" allowfullscreen></iframe>
                            </div>
                        </div>
                    </div>
                    <h3 class="card-title">Yuvaratna</h3>
                    <div class="card-role">Production Support</div>
                    <p class="card-desc">Major commercial Kannada release (2019). Supported large-scale shoot operations. Features Kannada & Hindi trailers.</p>
                </div>

                <!-- SPOOKY COLLEGE -->
                <div class="project-card">
                    <div class="media-wrapper">
                        <div class="card-media">
                            <div class="card-media-item">
                                <iframe src="https://www.youtube.com/embed/S-R_RO49UdY" title="Spooky College Trailer" allowfullscreen></iframe>
                            </div>
                        </div>
                    </div>
                    <h3 class="card-title">Spooky College</h3>
                    <div class="card-role">Assistant Director</div>
                    <p class="card-desc">Full-length Kannada Feature Film. Handled shot planning, scheduling, and comprehensive on-set coordination.</p>
                </div>

                <!-- THE SMILE I HATE -->
                <div class="project-card">
                    <div class="media-wrapper">
                        <div class="card-media">
                            <div class="card-media-item">
                                <iframe src="https://www.youtube.com/embed/-gAihzkv0gY" title="The Smile I Hate Short Film" allowfullscreen></iframe>
                            </div>
                        </div>
                    </div>
                    <h3 class="card-title">The Smile I Hate</h3>
                    <div class="card-role">Writer / Director / Performer</div>
                    <p class="card-desc">Independent Short Film (2023). Managed end-to-end production with a peer-recognised directorial vision.</p>
                </div>

            </div>
        </section>

        <!-- CREATIVE STRATEGY -->
        <section>
            <div class="section-header">
                <span class="section-num">03</span>
                <h2 class="section-title">Creative Strategy</h2>
            </div>
            
            <div class="projects-grid">
                
                <!-- TECHNOSPORT -->
                <div class="project-card">
                    <div class="media-wrapper">
                        <div class="scroll-hint">[ Swipe / Scroll -> ]</div>
                        <div class="card-media">
                            <div class="card-media-item">
                                <img src="./Techno%20Sport.png" alt="Technosport">
                            </div>
                            <div class="card-media-item">
                                <img src="./TEchno%20Sport%201.png" alt="Technosport 2">
                            </div>
                        </div>
                    </div>
                    <h3 class="card-title">Technosport</h3>
                    <div class="card-role">Creative Copywriter</div>
                    <p class="card-desc">Ideated and developed a 360° campaign concept and festival-led brand activation. Translated brief into a pitch-ready framework.</p>
                    <a href="./TECHNO%20SPORT%20MOVE%20EASY.pdf" target="_blank" class="btn btn-small">View Pitch Deck</a>
                </div>

                <!-- CAMPA COLA -->
                <div class="project-card">
                    <div class="media-wrapper">
                        <div class="scroll-hint">[ Swipe / Scroll -> ]</div>
                        <div class="card-media">
                            <div class="card-media-item"><img src="./Campa%20IPL.png" alt="Campa Cola"></div>
                            <div class="card-media-item"><img src="./Campa%20IPL%201.png" alt="Campa Image 1"></div>
                            <div class="card-media-item"><img src="./Campa%20IPL%202.png" alt="Campa Image 2"></div>
                            <div class="card-media-item"><img src="./Campa%20IPL%203.png" alt="Campa Image 3"></div>
                            <div class="card-media-item"><img src="./Campa-Cola-Food%20Court-V2-01.jpg" alt="Campa Food Court"></div>
                            <div class="card-media-item"><img src="./Campa-Cola-Food%20Court-V2-02.jpg" alt="Campa Food Court"></div>
                        </div>
                    </div>
                    <h3 class="card-title">Campa Cola</h3>
                    <div class="card-role">Creative Copywriter</div>
                    <p class="card-desc">Developed creative routes, content themes, and pitch decks for major brand activations including IPL and Ramadan campaigns.</p>
                    <a href="./Campa%20Power%20up%20Ramadan%20KV.pdf" target="_blank" class="btn btn-small">View Ramadan Pitch</a>
                </div>

                <!-- NESTLE -->
                <div class="project-card">
                    <div class="media-wrapper">
                        <div class="scroll-hint">[ Swipe / Scroll -> ]</div>
                        <div class="card-media">
                            <div class="card-media-item"><img src="./Nestle%20Maggie.png" alt="Nestle Maggi"></div>
                            <div class="card-media-item"><img src="./Nestle%20Maggie%201.png" alt="Maggi 2"></div>
                            <div class="card-media-item"><img src="./Nestle%20Maggie%202.png" alt="Maggi 3"></div>
                        </div>
                    </div>
                    <h3 class="card-title">Maggi (Nestlé)</h3>
                    <div class="card-role">Creative Copywriter</div>
                    <p class="card-desc">Ideated brand activations and festival-led content themes, collaborating deeply across Creative, Strategy, and Planning teams.</p>
                </div>

                <!-- COLLEGE NEWSLETTER -->
                <div class="project-card">
                    <div class="media-wrapper">
                        <div class="card-media">
                            <div class="card-media-item">
                                <!-- UPDATED TO MATCH YOUR EXACT FILE NAME: "Magazine cover Page.png" -->
                                <a href="./MBSphere%20Volume%202%20Edition%203%20(1).pdf" target="_blank" style="display: block; width: 100%; height: 100%;">
                                    <img src="./Magazine%20cover%20Page.png" alt="MBSphere Newsletter Cover" style="width: 100%; height: 100%; object-fit: cover; filter: grayscale(100%) contrast(1.2) brightness(0.9); transition: filter 0.8s ease;" onmouseover="this.style.filter='grayscale(0%) contrast(1) brightness(1)'" onmouseout="this.style.filter='grayscale(100%) contrast(1.2) brightness(0.9)'" onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';">
                                    
                                    <div style="display: none; width: 100%; height: 100%; align-items: center; justify-content: center; background: #0a0a0a; color: var(--grey); font-family: 'Inter', sans-serif; font-size: 0.8rem; letter-spacing: 3px; text-transform: uppercase; border: 1px solid var(--dark-border);">
                                        [ Image Not Found ]
                                    </div>
                                </a>
                            </div>
                        </div>
                    </div>
                    <h3 class="card-title">MBSphere Newsletter</h3>
                    <div class="card-role">Editorial & Layout Design</div>
                    <p class="card-desc">Spearheaded the editorial direction, layout design, and content curation for the official college newsletter, blending cinematic aesthetics with print storytelling.</p>
                    <a href="./MBSphere%20Volume%202%20Edition%203%20(1).pdf" target="_blank" class="btn btn-small">View Newsletter PDF</a>
                </div>

            </div>
        </section>

        <!-- CERTIFICATIONS SECTION -->
        <section style="border-bottom: none;">
            <div class="section-header">
                <span class="section-num">04</span>
                <h2 class="section-title">Certifications</h2>
            </div>
            
            <div class="cert-grid">
                
                <!-- CERTIFICATE 1 (Cinematic Composition) -->
                <a href="./Certificate-%20Cinematic%20Composition.pdf" target="_blank" class="cert-link">
                    <div class="cert-item">
                        <div class="cert-media">
                            <span>[ View PDF ]</span>
                        </div>
                        <h3 class="cert-title">Cinematic Composition</h3>
                        <div class="cert-org">Certification</div>
                    </div>
                </a>

                <!-- CERTIFICATE 2 (Claude 101) -->
                <a href="./certificate-Claude%20101.pdf" target="_blank" class="cert-link">
                    <div class="cert-item">
                        <div class="cert-media">
                            <span>[ View PDF ]</span>
                        </div>
                        <h3 class="cert-title">Claude 101</h3>
                        <div class="cert-org">Anthropic</div>
                    </div>
                </a>

                <!-- CERTIFICATE 3 (IFC 13) -->
                <a href="./IFC%2013.pdf" target="_blank" class="cert-link">
                    <div class="cert-item">
                        <div class="cert-media">
                            <span>[ View PDF ]</span>
                        </div>
                        <h3 class="cert-title">IFC 13</h3>
                        <div class="cert-org">Certification</div>
                    </div>
                </a>

                <!-- CERTIFICATE 4 (IFP 15) -->
                <a href="./IFP%2015.pdf" target="_blank" class="cert-link">
                    <div class="cert-item">
                        <div class="cert-media">
                            <span>[ View PDF ]</span>
                        </div>
                        <h3 class="cert-title">IFP 15</h3>
                        <div class="cert-org">Certification</div>
                    </div>
                </a>

            </div>
        </section>

    </div>
    
    <!-- ENHANCED FOOTER WITH ICONS -->
    <footer>
        <div class="footer-left">
            &copy; 2026 Laxman Khot
        </div>
        
        <div class="footer-contact">
            <!-- Email -->
            <div class="contact-item">
                <svg class="contact-icon" viewBox="0 0 24 24">
                    <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path>
                    <polyline points="22,6 12,13 2,6"></polyline>
                </svg>
                <a href="mailto:khotlaxman9632@gmail.com">khotlaxman9632@gmail.com</a>
            </div>

            <!-- Phone -->
            <div class="contact-item">
                <svg class="contact-icon" viewBox="0 0 24 24">
                    <path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path>
                </svg>
                <a href="tel:+919632617304">+91 96326 17304</a>
            </div>

            <!-- LinkedIn -->
            <div class="contact-item">
                <svg class="contact-icon" viewBox="0 0 24 24">
                    <path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path>
                    <rect x="2" y="9" width="4" height="12"></rect>
                    <circle cx="4" cy="4" r="2"></circle>
                </svg>
                <a href="https://www.linkedin.com/in/laxman-khot-a54689214" target="_blank">LinkedIn</a>
            </div>
        </div>
    </footer>

</body>
</html>
