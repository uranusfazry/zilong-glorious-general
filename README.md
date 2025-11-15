<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UranusFazry MLBB Portal | Zilong Glorious General</title>
    
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Libraries -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script>

    <style>
        /* Import Fonts */
        /* Dark, gothic serif for headings and modern sans‑serif for body */
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700;800&display=swap');
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap');

        /* Color Variables */
        :root {
        /* Palette inspired by Rafaela – Flower Fairy */
            --rafaela-sky: #f5e8fd;        /* pastel sky */
            --rafaela-cloud: #f9f7fc;      /* creamy clouds */
            --rafaela-teal: #00b4c0;       /* teal outfit */
            --rafaela-pink: #e95fa6;       /* fairy pink */
            --rafaela-yellow: #ffd77e;     /* soft yellow */
            --rafaela-purple: #c79eda;     /* lavender purple */
            --rafaela-highlight: #ffe2b0;  /* warm highlight */
            --rafaela-smoke: #e6d3ef;      /* subtle purple haze */
            --rafaela-green: #8ccd84;      /* fresh leaves */

            /* Palette inspired by Zilong – Glorious General */
            --zilong-night: #0d1b2a;       /* dark night sky */
            --zilong-ocean: #1b3b5f;       /* deep ocean blue */
            --zilong-teal: #2ed9c3;        /* glowing teal energy */
            --zilong-gold: #d3a14d;        /* royal gold */
            --zilong-aqua: #6ad1e0;        /* moonlit aqua */
            --zilong-steel: #2c3e50;       /* steel grey */
            --zilong-highlight: #b7b9c2;   /* pale silver highlight */
            --zilong-shadow: #102e46;      /* shadow navy */

            /* Legacy mappings for compatibility */
            --raven-dark: var(--zilong-night);
            --wing-black: var(--zilong-ocean);
            --blood-red: var(--zilong-teal);
            --sunset-gold: var(--zilong-gold);
            --twilight-blue: var(--zilong-aqua);
            --moon-pink: var(--zilong-aqua);
            --shadow-grey: var(--zilong-steel);
            --highlight-amber: var(--zilong-gold);
            --feather-glow: var(--zilong-aqua);

            /* Aliases for previous Franco variables mapped to Zilong palette */
            --franco-dark: var(--zilong-night);
            --franco-steel: var(--zilong-steel);
            --franco-orange: var(--zilong-teal);
            --franco-highlight: var(--zilong-gold);
            --franco-red: var(--zilong-gold);
            --franco-gold: var(--zilong-gold);
            --franco-deep: var(--zilong-ocean);
            --franco-green: var(--zilong-teal);

            /* Generic color variables reused throughout the CSS */
            --flame-red: var(--zilong-teal);
            --lava-orange: var(--zilong-gold);
            --gold: var(--zilong-gold);
            --bright-gold: var(--zilong-aqua);
            --ember-glow: var(--zilong-aqua);
        }

        /* Reset & Base */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: 'Inter', sans-serif;
            /* Deep purple fading into dark steel */
            background: linear-gradient(180deg, var(--zilong-night) 0%, var(--zilong-steel) 100%);
            color: #fff;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
            display: flex;
            flex-direction: column;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }

        /* Background Effects */
        #bg-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            overflow: hidden;
        }

        .bg-media {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            /* Tint the original video with a cool teal aura */
            filter: brightness(0.3) saturate(1.5) hue-rotate(10deg);
            transition: transform 0.5s ease, opacity 0.5s ease, filter 0.5s ease;
        }

        #bg-video {
            opacity: 0.25;
            z-index: 1;
        }

        #bg-image {
            opacity: 0;
            z-index: 0;
        }

        @media (min-width: 1024px) {
            .bg-media {
                width: 100vh;
                height: 100vw;
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%) rotate(-90deg);
            }
        }

        /* Celestial Aura Overlay */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background:
                radial-gradient(circle at 30% 35%, rgba(46, 217, 195, 0.25) 0%, transparent 60%),
                radial-gradient(circle at 75% 20%, rgba(106, 209, 224, 0.20) 0%, transparent 60%),
                radial-gradient(circle at 50% 70%, rgba(211, 161, 77, 0.2) 0%, transparent 70%),
                radial-gradient(circle at 85% 80%, rgba(183, 185, 194, 0.15) 0%, transparent 70%);
            z-index: 1;
            pointer-events: none;
            animation: auraPulse 12s ease-in-out infinite;
        }

        @keyframes auraPulse {
            0%, 100% { opacity: 0.4; }
            50% { opacity: 0.8; }
        }

        /* Ancient Wind Overlay */
        body::after {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image:
                linear-gradient(rgba(46, 217, 195, 0.05) 1px, transparent 1px),
                linear-gradient(90deg, rgba(211, 161, 77, 0.05) 1px, transparent 1px);
            background-size: 120px 120px;
            z-index: 1;
            pointer-events: none;
            animation: windDrift 60s linear infinite;
        }

        @keyframes windDrift {
            0% { transform: translate(0, 0); }
            100% { transform: translate(120px, 120px); }
        }

        #particle-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }

        .content-layer {
            position: relative;
            z-index: 10;
        }

        main.content-layer {
            flex-grow: 1;
        }

        /* Typography */
        .font-cinzel { font-family: 'Cinzel', serif; }
        .font-playfair { font-family: 'Cinzel', serif; }

        .flame-text {
            /* Teal accent for hero energy */
            color: var(--zilong-teal);
        }

        .gold-text {
            /* Golden accent for royal elements */
            color: var(--zilong-gold);
        }

        .lava-text {
            /* Aqua accent for moonlit highlights */
            color: var(--zilong-aqua);
        }

        /* Navbar */
        .navbar {
            background: rgba(13, 27, 42, 0.85);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border-bottom: 2px solid rgba(46, 217, 195, 0.4);
            box-shadow: 0 4px 30px rgba(106, 209, 224, 0.25);
            transition: all 0.3s ease;
        }

        .navbar .container > div {
            height: 70px;
            transition: height 0.3s ease;
        }

        @media (min-width: 768px) {
            .navbar .container > div {
                height: 90px;
            }
        }

        .nav-item {
            transition: all 0.3s ease;
            position: relative;
            padding: 0.5rem 1rem;
        }

        .nav-item:hover span, .nav-item:hover i {
            color: var(--zilong-gold);
            text-shadow: 0 0 15px var(--zilong-teal);
        }

        .nav-item::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--zilong-teal), var(--zilong-gold));
            transition: width 0.3s ease;
            border-radius: 2px;
            box-shadow: 0 0 10px var(--zilong-teal);
        }

        .nav-item:hover::after {
            width: 100%;
        }

        /* Dropdown */
        .dropdown {
            display: none;
            position: absolute;
            background: rgba(19, 39, 62, 0.95);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 2px solid var(--zilong-teal);
            box-shadow: 0 10px 40px rgba(106, 209, 224, 0.3);
            border-radius: 12px;
            margin-top: 12px;
            animation: dropFadeIn 0.3s ease;
        }

        @keyframes dropFadeIn {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .group:hover .dropdown {
            display: block;
        }

        /* Mobile Menu */
        #mobile-menu-overlay {
            position: fixed;
            inset: 0;
            background: rgba(13, 27, 42, 0.8);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            z-index: 55;
            transition: opacity 0.3s ease;
        }

        #mobile-menu {
            position: fixed;
            top: 0;
            right: 0;
            height: 100%;
            width: 80%;
            max-width: 320px;
            background: rgba(19, 39, 62, 0.95);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-left: 2px solid var(--zilong-teal);
            z-index: 60;
            transform: translateX(100%);
            transition: transform 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            padding: 2rem 1.5rem;
            display: flex;
            flex-direction: column;
        }

        #mobile-menu.open {
            transform: translateX(0);
        }

        /* Buttons */
        .btn-lava {
            font-family: 'Cinzel', serif;
            background: linear-gradient(135deg, var(--zilong-teal), var(--zilong-gold));
            border: 2px solid var(--zilong-gold);
            border-radius: 8px;
            padding: 0.75rem 1.5rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            z-index: 1;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            text-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
            box-shadow: 0 0 20px rgba(46, 217, 195, 0.3);
        }

        .btn-lava::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(183, 185, 194, 0.6), transparent);
            transition: left 0.5s ease;
            z-index: -1;
            animation: lavaFlow 3s ease-in-out infinite;
        }

        @keyframes lavaFlow {
            0%, 100% { left: -100%; }
            50% { left: 100%; }
        }

        .btn-lava:hover {
            box-shadow: 0 0 30px var(--zilong-gold), 0 0 50px var(--zilong-teal);
            transform: translateY(-3px);
            border-color: var(--zilong-gold);
        }

        .btn-lava:active {
            transform: translateY(0) scale(0.97);
            box-shadow: 0 0 15px var(--zilong-gold);
            transition-duration: 0.1s;
        }

        .btn-secondary {
            font-family: 'Cinzel', serif;
            background: rgba(19, 39, 62, 0.4);
            border: 2px solid rgba(46, 217, 195, 0.5);
            border-radius: 8px;
            padding: 0.75rem 1.5rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.05em;
            transition: all 0.3s ease;
            color: var(--zilong-teal);
        }

        .btn-secondary:hover {
            background: rgba(19, 39, 62, 0.5);
            border-color: var(--zilong-gold);
            box-shadow: 0 0 20px rgba(46, 217, 195, 0.3);
        }

        /* Portal Cards */
        .portal-card {
            background: rgba(19, 39, 62, 0.6);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border: 2px solid;
            border-radius: 16px;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.4);
        }

        .portal-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3), 0 0 40px currentColor;
        }

        .portal-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent 30%, rgba(46, 217, 195, 0.15) 50%, transparent 70%);
            transform: rotate(45deg);
            animation: goldShimmer 5s linear infinite;
            opacity: 0.8;
        }

        @keyframes goldShimmer {
            0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
            100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
        }

        .delete-btn {
            position: absolute;
            top: 12px;
            right: 12px;
            color: rgba(46, 217, 195, 0.8);
            background: rgba(13, 27, 42, 0.4);
            border-radius: 50%;
            width: 32px;
            height: 32px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
            z-index: 20;
            opacity: 0.7;
            border: 1px solid rgba(211, 161, 77, 0.5);
        }

        .portal-card:hover .delete-btn {
            opacity: 1;
        }

        .delete-btn:hover {
            color: var(--zilong-teal);
            background: rgba(19, 39, 62, 0.6);
            transform: scale(1.15);
            box-shadow: 0 0 15px var(--zilong-teal);
        }

        /* Profile/Avatar */
        .profile {
            margin: 0 auto 2rem;
            width: 160px;
            height: 160px;
            border-radius: 50%;
            overflow: hidden;
            border: 4px solid var(--zilong-gold);
            position: relative;
        }

        .profile img, .profile video {
            width: 100%;
            height: 100%;
            object-fit: cover;
            position: relative;
            z-index: 1;
        }

        /* Time Display */
        .time-container {
            background: rgba(19, 39, 62, 0.8);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border: 2px solid var(--zilong-gold);
            box-shadow: 0 0 30px rgba(46, 217, 195, 0.4), inset 0 0 25px rgba(211, 161, 77, 0.2);
            border-radius: 12px;
            position: relative;
            overflow: hidden;
        }

        .time-container::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(106, 209, 224, 0.3), transparent);
            animation: timeScan 4s ease-in-out infinite;
        }

        @keyframes timeScan {
            0%, 100% { left: -100%; }
            50% { left: 100%; }
        }

        /* Modals */
        .modal-overlay {
            background: rgba(19, 39, 62, 0.85);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            animation: modalFadeIn 0.3s ease;
        }

        .modal-content {
            background: rgba(19, 39, 62, 0.95);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border: 2px solid var(--zilong-teal);
            box-shadow: 0 0 50px rgba(106, 209, 224, 0.4);
            border-radius: 16px;
            animation: modalSlideIn 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        @keyframes modalFadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes modalSlideIn {
            from { transform: translateY(-40px) scale(0.9); opacity: 0; }
            to { transform: translateY(0) scale(1); opacity: 1; }
        }

        /* Inputs */
        input, textarea, select {
            background: rgba(13, 27, 42, 0.9) !important;
            border: 2px solid rgba(46, 217, 195, 0.4);
            transition: all 0.3s ease;
            border-radius: 8px;
            color: #fff;
            font-family: 'Inter', sans-serif;
        }

        input:focus, textarea:focus, select:focus {
            border-color: var(--zilong-teal);
            box-shadow: 0 0 20px rgba(106, 209, 224, 0.5);
            outline: none;
            background: rgba(19, 39, 62, 0.95) !important;
        }

        select option {
            background: var(--zilong-night);
            color: #fff;
            padding: 10px;
        }

        ::placeholder {
            color: rgba(106, 209, 224, 0.6);
            opacity: 1;
        }

        .modal-content code {
            background: rgba(0, 0, 0, 0.4);
            color: var(--zilong-gold);
            padding: 3px 6px;
            border-radius: 4px;
            font-family: 'Inter', sans-serif;
        }

        /* Scrollbar */
        ::-webkit-scrollbar { width: 12px; }
        ::-webkit-scrollbar-track { background: rgba(19, 39, 62, 0.6); }
        ::-webkit-scrollbar-thumb {
            background: linear-gradient(180deg, var(--zilong-teal), var(--zilong-gold));
            border-radius: 6px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: linear-gradient(180deg, var(--zilong-gold), var(--zilong-teal));
        }

        /* Logo Animation */
        .logo-pulse {
            animation: flamePulse 4s ease-in-out infinite;
        }

        @keyframes flamePulse {
            0%, 100% {
                transform: scale(1);
                filter: drop-shadow(0 0 15px var(--gold));
            }
            50% {
                transform: scale(1.15);
                filter: drop-shadow(0 0 30px var(--lava-orange));
            }
        }

        /* Footer */
        footer {
            background: rgba(34, 25, 44, 0.9);
            border-top: 2px solid rgba(199, 157, 76, 0.3);
            margin-top: auto;
            height: 70px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 0 1rem;
            box-shadow: 0 -4px 30px rgba(199, 157, 76, 0.2);
        }

        footer p:first-child {
            font-size: 14px;
        }

        /* Utility Classes */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1rem;
        }

        .hidden { display: none; }

        /* Light Mode toggle: convert tinted video and brighten image */
        body.light-mode #bg-image {
            opacity: 1 !important;
            filter: saturate(1.15);
        }
        body.light-mode #bg-video {
            opacity: 0.35;
            z-index: 1;
        }
    </style>
</head>
<body>
    <!-- Background -->
    <div id="bg-container">
        <video id="bg-video" class="bg-media" autoplay muted playsinline>
            <!-- We reuse the original video source but tinted via CSS filters -->
            <source src="https://files.catbox.moe/4gi6v5.mp4" type="video/mp4">
        </video>
        <!-- Use local image for the background -->
        <img id="bg-image" class="bg-media" src="zilong.png" alt="Zilong Background">
    </div>
    <canvas id="particle-canvas"></canvas>

    <!-- Navbar -->
    <nav class="navbar fixed top-0 left-0 right-0 z-50 content-layer" style="position: fixed; top: 0; left: 0; right: 0; z-index: 50;">
        <div class="container" style="max-width: 1200px; margin: 0 auto; padding: 0 1rem;">
            <div style="display: flex; justify-content: space-between; align-items: center;">
                <!-- Logo -->
                <div id="logo-container" style="display: flex; align-items: center; cursor: pointer; user-select: none; -webkit-user-select: none; -moz-user-select: none; -ms-user-select: none;">
                    <!-- Use the hero image as a small logo -->
                    <img src="https://i.imghippo.com/files/EePl9866XxI.png" alt="Zilong Logo" class="logo-pulse" style="height: 50px; width: auto; border-radius: 8px;" draggable="false">
                    <span class="font-cinzel gold-text" style="font-weight: 700; font-size: 1.25rem; letter-spacing: 0.05em; margin-left: 1rem;">MLBB ZILONG</span>
                </div>

                <!-- Desktop Nav -->
                <div style="display: none;" class="desktop-nav">
                    <div class="nav-item relative group" style="display: inline-block; position: relative;">
                            <button class="flame-text" style="display: flex; align-items: center; gap: 0.5rem; background: none; border: none; cursor: pointer; font-family: 'Cinzel', serif; font-size: 0.875rem; text-transform: uppercase;">
                                <i class="fas fa-dragon"></i>
                                <span>Forge</span>
                                <i class="fas fa-chevron-down" style="font-size: 0.75rem; transition: transform 0.3s;"></i>
                            </button>
                            <div class="dropdown" style="position: absolute; right: 0; width: 320px; padding: 1.5rem; margin-top: 0.75rem;">
                                <h3 class="font-cinzel" style="font-size: 0.875rem; margin-bottom: 1rem; text-transform: uppercase; letter-spacing: 0.05em; color: var(--zilong-gold);">Create Portal</h3>
                                
                                <button onclick="showAddLinkModal()" class="btn-secondary" style="width: 100%; font-size: 0.875rem; margin-bottom: 1rem;">
                                    <i class="fas fa-plus" style="margin-right: 0.5rem;"></i>Add Portal
                                </button>

                                <h3 class="font-cinzel" style="font-size: 0.875rem; margin-top: 1.5rem; margin-bottom: 1rem; text-transform: uppercase; letter-spacing: 0.05em; color: var(--zilong-gold);">Data Vault</h3>
                                <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 0.75rem;">
                                    <button onclick="importData()" class="btn-secondary" style="width: 100%; font-size: 0.75rem; padding: 0.5rem 1rem;"><i class="fas fa-upload" style="margin-right: 0.25rem;"></i>Import</button>
                                    <button onclick="backupData()" class="btn-secondary" style="width: 100%; font-size: 0.75rem; padding: 0.5rem 1rem;"><i class="fas fa-download" style="margin-right: 0.25rem;"></i>Backup</button>
                                </div>

                                <h3 class="font-cinzel" style="font-size: 0.875rem; margin-top: 1.5rem; margin-bottom: 1rem; text-transform: uppercase; letter-spacing: 0.05em; color: var(--zilong-gold);">Purge System</h3>
                                <button onclick="showConfirmationModal('Initiate system purge?', resetAllSettings)" class="btn-secondary" style="width: 100%; font-size: 0.875rem;">
                                    <i class="fas fa-skull-crossbones" style="margin-right: 0.5rem;"></i>Reset All
                                </button>
                            </div>
                    </div>
                </div>

                <!-- Mobile Menu Button -->
                <div class="mobile-nav-toggle">
                    <button id="mobile-menu-button" class="flame-text" style="background: none; border: none; font-size: 2rem; cursor: pointer; outline: none;">
                        <i class="fas fa-dragon"></i>
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Mobile Menu -->
    <div id="mobile-menu-overlay" class="fixed inset-0 z-50 hidden" style="position: fixed; top: 0; left: 0; right: 0; bottom: 0; z-index: 55;" onclick="closeMobileMenu()"></div>
    <div id="mobile-menu" style="padding: 2rem 1.5rem;">
        <div style="display: flex; justify-content: space-between; align-items: center; padding-bottom: 1rem; border-bottom: 1px solid rgba(199, 157, 76, 0.3);">
            <span class="font-cinzel" style="font-size: 1.125rem; color: var(--zilong-gold);">FORGE</span>
            <button onclick="closeMobileMenu()" style="background: none; border: none; font-size: 1.5rem; cursor: pointer; color: var(--zilong-gold);">
                <i class="fas fa-times"></i>
            </button>
        </div>

        <div style="flex-grow: 1; overflow-y: auto;">
            <h3 class="font-cinzel" style="font-size: 0.875rem; margin-bottom: 0.75rem; margin-top: 1rem; text-transform: uppercase; letter-spacing: 0.05em; color: var(--zilong-gold);">Portal</h3>
            <button onclick="showAddLinkModal(); closeMobileMenu();" class="btn-secondary" style="width: 100%; font-size: 0.875rem; margin-bottom: 1rem;">
                <i class="fas fa-plus" style="margin-right: 0.5rem;"></i>Add Portal
            </button>

            <h3 class="font-cinzel" style="font-size: 0.875rem; margin-top: 1rem; margin-bottom: 0.75rem; text-transform: uppercase; letter-spacing: 0.05em; color: var(--zilong-gold);">Data</h3>
            <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 0.75rem; margin-bottom: 1rem;">
                <button onclick="importData(); closeMobileMenu();" class="btn-secondary" style="width: 100%; font-size: 0.75rem; padding: 0.5rem 1rem;"><i class="fas fa-upload" style="margin-right: 0.25rem;"></i>Import</button>
                <button onclick="backupData(); closeMobileMenu();" class="btn-secondary" style="width: 100%; font-size: 0.75rem; padding: 0.5rem 1rem;"><i class="fas fa-download" style="margin-right: 0.25rem;"></i>Backup</button>
            </div>

            <h3 class="font-cinzel" style="font-size: 0.875rem; margin-top: 1rem; margin-bottom: 0.75rem; text-transform: uppercase; letter-spacing: 0.05em; color: var(--zilong-gold);">System</h3>
            <button onclick="showConfirmationModal('Initiate system purge?', resetAllSettings); closeMobileMenu();" class="btn-secondary" style="width: 100%; font-size: 0.875rem; margin-bottom: 1rem;">
                <i class="fas fa-skull-crossbones" style="margin-right: 0.5rem;"></i>Reset All
            </button>
        </div>
    </div>

    <!-- Main Content -->
    <main class="container content-layer" style="padding-top: 120px; padding-bottom: 2rem;">
        <header style="text-align: center; margin-bottom: 3rem;">
            <!-- Profile -->
            <div class="profile">
                <!-- Use Zilong image for avatar -->
                <img src="zilong.png" alt="Zilong Avatar" style="object-position: center; will-change: transform;">
            </div>

            <!-- Epic Title -->
            <div style="display: inline-block; margin-bottom: 1.5rem;">
                <!-- Update heading to reflect Glorious General theme -->
                <h1 class="font-playfair" data-text="Glorious General" style="font-size: 2.5rem; font-weight: 900; margin-bottom: 1rem; color: var(--zilong-gold);">GLORIOUS GENERAL</h1>
            </div>
            <!-- Tagline describing Zilong's role -->
            <p class="font-cinzel flame-text" style="font-size: 1.125rem; text-transform: uppercase; letter-spacing: 0.1em; font-weight: 600;">MLBB Creator &amp; Web Developer</p>
            <p style="max-width: 42rem; margin: 1.5rem auto 0; font-size: 1rem; line-height: 1.6; color: rgba(106, 209, 224, 0.8);">
            </p>
        </header>

        <!-- Time Display -->
        <div style="display: flex; justify-content: center; margin-bottom: 3rem;">
            <div class="time-container" style="padding: 1.5rem 2rem; text-align: center;">
                <div id="time" class="font-cinzel gold-text" style="font-size: 2.5rem; font-weight: 700;">00:00:00</div>
                <div id="date" class="font-cinzel flame-text" style="font-size: 1rem; text-transform: uppercase; letter-spacing: 0.05em; margin-top: 0.5rem;">Loading...</div>
            </div>
        </div>

        <!-- Portal Grid -->
        <div id="portals-grid" style="display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); gap: 1.5rem; margin-bottom: 3rem;">
            <!-- Portal cards rendered by JS -->
        </div>
    </main>

    <!-- Footer -->
    <footer class="content-layer" style="text-align: center; color: #fff;">
        <p class="font-cinzel" style="font-size: 0.875rem; opacity: 0.85;">© 2025 Created by GLORIOUS GENERAL | All Rights Reserved</p>
        <p class="gold-text font-cinzel" style="font-size: 0.75rem; margin-top: 0.5rem;">Forged by Uranus Support Technology</p>
    </footer>

    <!-- Add Portal Modal -->
    <div id="add-portal-modal" class="fixed inset-0 flex items-center justify-center z-50 hidden modal-overlay" style="position: fixed; top: 0; left: 0; right: 0; bottom: 0; display: none; align-items: center; justify-content: center; z-index: 50;">
        <div class="modal-content" style="max-width: 28rem; width: 100%; margin: 0 1.5rem; position: relative; padding: 2rem;">
            <button onclick="document.getElementById('add-portal-modal').style.display = 'none'" style="position: absolute; top: 1rem; right: 1rem; font-size: 2rem; background: none; border: none; cursor: pointer; transition: all 0.3s;" class="flame-text">×</button>
            
            <h2 class="font-cinzel gold-text" style="font-size: 1.5rem; margin-bottom: 1.5rem; text-transform: uppercase; letter-spacing: 0.05em; font-weight: 700;">Forge New Portal</h2>

            <form id="portal-form" style="display: flex; flex-direction: column; gap: 1rem;">
                <div>
                    <label for="portal-name" class="font-cinzel gold-text" style="display: block; margin-bottom: 0.5rem; text-transform: uppercase; font-size: 0.875rem; letter-spacing: 0.05em;">Portal Name</label>
                    <input type="text" id="portal-name" style="width: 100%; padding: 0.75rem; border-radius: 8px; font-size: 1rem;" placeholder="Enter portal name" required>
                </div>

                <div>
                    <label for="portal-url" class="font-cinzel gold-text" style="display: block; margin-bottom: 0.5rem; text-transform: uppercase; font-size: 0.875rem; letter-spacing: 0.05em;">Destination URL</label>
                    <input type="url" id="portal-url" style="width: 100%; padding: 0.75rem; border-radius: 8px; font-size: 1rem;" placeholder="https://your-link.com" required>
                </div>

                <div>
                    <label for="portal-icon" class="font-cinzel gold-text" style="display: block; margin-bottom: 0.5rem; text-transform: uppercase; font-size: 0.875rem; letter-spacing: 0.05em;">Portal Icon</label>
                    <select id="portal-icon" style="width: 100%; padding: 0.75rem; border-radius: 8px; font-size: 1rem; appearance: none;">
                        <option value="fas fa-sword">🗡️ Sword</option>
                        <option value="fas fa-shield-alt">🛡️ Shield</option>
                        <option value="fas fa-bolt">⚡ Bolt</option>
                        <option value="fas fa-crosshairs">🎯 Target</option>
                        <option value="fas fa-robot">🤖 Robot</option>
                        <option value="fas fa-microchip">🔧 Chip</option>
                        <option value="fab fa-whatsapp">💬 WhatsApp</option>
                        <option value="fab fa-youtube">▶️ YouTube</option>
                        <option value="fab fa-instagram">📸 Instagram</option>
                        <option value="fab fa-tiktok">🎵 TikTok</option>
                    </select>
                </div>
                
                <div>
                    <label for="portal-description" class="font-cinzel gold-text" style="display: block; margin-bottom: 0.5rem; text-transform: uppercase; font-size: 0.875rem; letter-spacing: 0.05em;">Description</label>
                    <textarea id="portal-description" rows="2" style="width: 100%; padding: 0.75rem; border-radius: 8px; font-size: 1rem; resize: vertical;" placeholder="Brief description..."></textarea>
                </div>

                <div>
                    <label class="font-cinzel gold-text" style="display: block; margin-bottom: 0.5rem; text-transform: uppercase; font-size: 0.875rem; letter-spacing: 0.05em;">Portal Theme</label>
                    <div style="display: flex; justify-content: space-around; padding-top: 0.5rem;">
                        <!-- Zilong portal theme options: Teal, Gold, Aqua -->
                        <label style="display: flex; align-items: center; gap: 0.5rem; cursor: pointer; padding: 0.5rem; border-radius: 8px; transition: all 0.3s;">
                            <input type="radio" name="portal-color" value="#2ed9c3" style="width: 1.25rem; height: 1.25rem; accent-color: var(--zilong-teal);" checked>
                            <span class="font-cinzel" style="font-weight: 700; color: var(--zilong-teal);">Teal</span>
                        </label>
                        <label style="display: flex; align-items: center; gap: 0.5rem; cursor: pointer; padding: 0.5rem; border-radius: 8px; transition: all 0.3s;">
                            <input type="radio" name="portal-color" value="#d3a14d" style="width: 1.25rem; height: 1.25rem; accent-color: var(--zilong-gold);">
                            <span class="font-cinzel" style="font-weight: 700; color: var(--zilong-gold);">Gold</span>
                        </label>
                        <label style="display: flex; align-items: center; gap: 0.5rem; cursor: pointer; padding: 0.5rem; border-radius: 8px; transition: all 0.3s;">
                            <input type="radio" name="portal-color" value="#6ad1e0" style="width: 1.25rem; height: 1.25rem; accent-color: var(--zilong-aqua);">
                            <span class="font-cinzel" style="font-weight: 700; color: var(--zilong-aqua);">Aqua</span>
                        </label>
                    </div>
                </div>

                <div style="display: flex; justify-content: flex-end; gap: 0.75rem; padding-top: 0.5rem;">
                    <button type="button" onclick="document.getElementById('add-portal-modal').style.display = 'none'" class="btn-secondary" style="padding: 0.75rem 1.5rem; font-size: 0.875rem;">
                        Cancel
                    </button>
                    <button type="submit" class="btn-lava" style="padding: 0.75rem 1.5rem; font-size: 0.875rem;">
                        Forge
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Confirmation Modal -->
    <div id="confirmation-modal" class="fixed inset-0 flex items-center justify-center hidden modal-overlay" style="position: fixed; top: 0; left: 0; right: 0; bottom: 0; display: none; align-items: center; justify-content: center; z-index: 60;">
        <div class="modal-content" style="max-width: 28rem; width: 100%; margin: 0 1rem; position: relative; padding: 2rem; text-align: center;">
            <h2 class="font-cinzel flame-text" style="font-size: 1.25rem; margin-bottom: 1rem; font-weight: 700;">Confirm Action</h2>
            <p id="confirmation-message" style="margin-bottom: 1.5rem; font-size: 1.125rem; color: rgba(211, 161, 77, 0.9);">Are you sure?</p>
            <div style="display: flex; justify-content: center; gap: 1rem;">
                <button id="confirm-cancel-btn" class="btn-secondary" style="padding: 0.75rem 1.5rem; font-size: 0.875rem;">
                    Cancel
                </button>
                <button id="confirm-ok-btn" class="btn-lava" style="padding: 0.75rem 1.5rem; font-size: 0.875rem;">
                    Confirm
                </button>
            </div>
        </div>
    </div>

    <input type="file" id="import-file-input" class="hidden" style="display: none;" accept=".zip,.txt,application/json">

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            let isVideoFinished = false;

            const bgVideo = document.getElementById('bg-video');
            const bgImage = document.getElementById('bg-image');

            if (bgVideo && bgImage) {
                const handleVideoEnd = () => {
                    bgVideo.style.opacity = '0';
                    if (!document.body.classList.contains('light-mode')) {
                        bgImage.style.opacity = '0.35';
                    }
                    isVideoFinished = true;
                };

                const handleVideoError = (e) => {
                    console.error("Video background failed:", e);
                    handleVideoEnd();
                };
                
                bgVideo.addEventListener('ended', handleVideoEnd);
                bgVideo.addEventListener('error', handleVideoError);

                const playPromise = bgVideo.play();
                if (playPromise !== undefined) {
                    playPromise.catch(error => {
                        console.warn("Autoplay blocked:", error);
                        handleVideoEnd();
                    });
                }
            }

            const logoContainer = document.getElementById('logo-container');
            const portalsGrid = document.getElementById('portals-grid');
            const portalForm = document.getElementById('portal-form');
            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            const mobileMenuOverlay = document.getElementById('mobile-menu-overlay');
            const timeDisplay = document.getElementById('time');
            const dateDisplay = document.getElementById('date');
            const importFileInput = document.getElementById('import-file-input');
            const confirmationModal = document.getElementById('confirmation-modal');
            const confirmationMessage = document.getElementById('confirmation-message');
            const confirmOkBtn = document.getElementById('confirm-ok-btn');
            const confirmCancelBtn = document.getElementById('confirm-cancel-btn');

            let portals = [];
            let onConfirmCallback = null;

            const defaultPortals = [
                { 
                    name: 'Zilong Premium Access', 
                    url: 'https://api.whatsapp.com/send/?phone=6287872521809&text=Halo%2C+saya+ingin+membeli+Akses+Website+Premium+Tanpa+Iklan+sebesar+Rp25.000.+Mohon+transfer+ke+DANA+087734421123+dan+kirimkan+bukti+pembayarannya.+Pesanan+akan+diproses+maksimal+1x24+jam.+Terima+kasih.&type=phone_number&app_absent=0', 
                    icon: 'fas fa-dragon', 
                    color: '#2ed9c3', 
                    description: 'Upgrade sekarang — akses semua website uranus tanpa iklan cuma Rp25K' 
                },
                { 
                    name: 'Buy Zilong Glorious General', 
                    url: 'https://api.whatsapp.com/send/?phone=6287872521809&text=Halo%2C+saya+ingin+membeli+Kode+Website+MLBB+Zilong+Glorious+General+sebesar+Rp100.000.+Mohon+transfer+ke+DANA+087734421123+dan+kirimkan+bukti+pembayarannya.+Pesanan+akan+diproses+maksimal+1x24+jam.+Terima+kasih.&type=phone_number&app_absent=0', 
                    icon: 'fas fa-sword', 
                    color: '#d3a14d', 
                    description: 'Beli kode website MLBB Zilong Glorious General edisi premium seharga Rp100K' 
                }
            ];

            function initPortalApp() {
                portals = JSON.parse(localStorage.getItem('portals')) || defaultPortals;
                renderPortals();
                updateTime();
                setInterval(updateTime, 1000);

                logoContainer.addEventListener('click', () => {
                    if (!isVideoFinished) {
                        console.log("Light mode locked until video ends.");
                        return;
                    }
                    document.body.classList.toggle('light-mode');
                    if (!document.body.classList.contains('light-mode') && bgVideo.style.opacity === '0') {
                        bgImage.style.opacity = '0.35';
                    }
                });

                mobileMenuButton.addEventListener('click', () => {
                    mobileMenu.classList.add('open');
                    mobileMenuOverlay.classList.remove('hidden');
                    mobileMenuOverlay.style.display = 'block';
                    document.body.style.overflow = 'hidden';
                });

                mobileMenuOverlay.addEventListener('click', closeMobileMenu);

                portalForm.addEventListener('submit', handlePortalFormSubmit);
                importFileInput.addEventListener('change', handleFileImport);
                confirmCancelBtn.addEventListener('click', () => {
                    confirmationModal.classList.add('hidden');
                    confirmationModal.style.display = 'none';
                });
                confirmOkBtn.addEventListener('click', () => {
                    if (typeof onConfirmCallback === 'function') {
                        onConfirmCallback();
                    }
                    confirmationModal.classList.add('hidden');
                    confirmationModal.style.display = 'none';
                    onConfirmCallback = null;
                });

                // Show desktop nav on larger screens
                window.addEventListener('resize', updateNavDisplay);
                updateNavDisplay();
            }

            function updateNavDisplay() {
                const desktopNav = document.querySelector('.desktop-nav');
                const mobileToggle = document.querySelector('.mobile-nav-toggle');
                if (window.innerWidth >= 768) {
                    if (desktopNav) desktopNav.style.display = 'block';
                    if (mobileToggle) mobileToggle.style.display = 'none';
                } else {
                    if (desktopNav) desktopNav.style.display = 'none';
                    if (mobileToggle) mobileToggle.style.display = 'block';
                }
            }

            window.closeMobileMenu = function() {
                mobileMenu.classList.remove('open');
                mobileMenuOverlay.classList.add('hidden');
                mobileMenuOverlay.style.display = 'none';
                document.body.style.overflow = '';
            }

            window.showConfirmationModal = function(message, callback) {
                confirmationMessage.textContent = message;
                onConfirmCallback = callback;
                confirmationModal.classList.remove('hidden');
                confirmationModal.style.display = 'flex';
            }

            function renderPortals() {
                portalsGrid.innerHTML = '';

                portals.forEach((portal, index) => {
                    const portalElement = document.createElement('div');
                    portalElement.style.height = '100%';

                    const portalColor = portal.color || '#e65027';
                    const cardStyle = `color: ${portalColor}; border-color: ${portalColor};`;
                    const textStyle = `color: ${portalColor}; text-shadow: 0 0 15px ${portalColor};`;
                    
                    let iconClass = portal.icon || 'fas fa-fire';
                    if (!portal.icon || (!portal.icon.startsWith('fa') && !portal.icon.startsWith('http') && !portal.icon.startsWith('data:image'))) {
                        iconClass = 'fas fa-fire'; 
                    }

                    const iconHtml = (iconClass.startsWith('data:image') || iconClass.startsWith('http'))
                        ? `<img src="${iconClass}" style="margin: 0 auto 1rem; height: 3rem; width: 3rem; object-fit: contain;" alt="${portal.name} icon" onerror="this.style.display='none'; this.nextSibling.style.display='block';"><i class="fas fa-fire" style="font-size: 3rem; margin-bottom: 1rem; display: none; ${textStyle}"></i>`
                        : `<i class="${iconClass}" style="font-size: 3rem; margin-bottom: 1rem; ${textStyle}"></i>`;

                    const descriptionHtml = portal.description ? portal.description : '&nbsp;';

                    portalElement.innerHTML = `
                        <div class="portal-card" style="${cardStyle} height: 100%;">
                            <a href="${portal.url}" target="_blank" style="display: block; height: 100%; padding: 1.5rem; text-align: center; position: relative; text-decoration: none; color: inherit;">
                                <div style="position: relative; z-index: 10; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%;">
                                    ${iconHtml}
                                    <h3 class="font-cinzel" style="font-weight: 700; text-transform: uppercase; letter-spacing: 0.05em; word-break: break-word; font-size: 1.125rem; margin-bottom: 0.5rem; ${textStyle}">${portal.name}</h3>
                                    <p style="font-size: 0.875rem; color: rgba(199, 157, 76, 0.8); margin-top: 0.5rem; line-height: 1.4;">${descriptionHtml}</p>
                                </div>
                                
                                <button onclick="event.preventDefault(); event.stopPropagation(); showConfirmationModal('Destroy portal ${portal.name}?', () => deletePortalAction(${index}))" class="delete-btn">
                                    <i class="fas fa-times" style="font-size: 0.875rem;"></i>
                                </button>
                            </a>
                        </div>
                    `;

                    portalsGrid.appendChild(portalElement);
                });
            }

            function handlePortalFormSubmit(e) {
                e.preventDefault();

                const name = document.getElementById('portal-name').value;
                const url = document.getElementById('portal-url').value || "#";
                const description = document.getElementById('portal-description').value || "";
                const icon = document.getElementById('portal-icon').value;
                const color = document.querySelector('input[name=\"portal-color\"]:checked').value;

                addPortalToArray(name, url, icon, color, description);
            }

            function addPortalToArray(name, url, icon, color, description) {
                portals.push({ name, url, icon, color, description });
                savePortals();
                renderPortals();
                document.getElementById('add-portal-modal').classList.add('hidden');
                document.getElementById('add-portal-modal').style.display = 'none';
                resetPortalForm();
            }

            window.deletePortalAction = function(index) {
                portals.splice(index, 1);
                savePortals();
                renderPortals();
            }

            function resetPortalForm() {
                portalForm.reset();
            }

            function savePortals() {
                localStorage.setItem('portals', JSON.stringify(portals));
            }

            window.showAddLinkModal = function() {
                document.getElementById('add-portal-modal').classList.remove('hidden');
                document.getElementById('add-portal-modal').style.display = 'flex';
                resetPortalForm();
                if (mobileMenu.classList.contains('open')) {
                    closeMobileMenu();
                }
            }

            function updateTime() {
                const now = new Date();
                timeDisplay.textContent = now.toLocaleTimeString('en-GB');
                dateDisplay.textContent = now.toLocaleDateString('id-ID', {
                    weekday: 'long', year: 'numeric', month: 'long', day: 'numeric'
                });
            }

            window.resetAllSettings = function() {
                localStorage.removeItem('portals');
                location.reload();
            }

            window.backupData = async () => {
                const dataToBackup = {
                    portals: JSON.parse(localStorage.getItem('portals')) || defaultPortals,
                };
                const dataStr = JSON.stringify(dataToBackup, null, 2);
                try {
                    const zip = new JSZip();
                    zip.file("uranusfazry_backup.json", dataStr);
                    const content = await zip.generateAsync({ type: "blob", compression: "DEFLATE" });
                    const url = URL.createObjectURL(content);
                    const a = document.createElement('a');
                    a.href = url;
                    a.download = 'uranusfazry_backup.zip';
                    document.body.appendChild(a);
                    a.click();
                    document.body.removeChild(a);
                    URL.revokeObjectURL(url);
                } catch (error) {
                    console.error("Error creating ZIP:", error);
                    alert("Backup failed.");
                }
            };

            window.importData = () => {
                importFileInput.click();
            };

            async function handleFileImport(event) {
                const file = event.target.files[0];
                if (!file) return;

                if (file.type === "application/zip" || file.name.endsWith(".zip")) {
                    const reader = new FileReader();
                    reader.onload = async (e) => {
                        try {
                            const zip = await JSZip.loadAsync(e.target.result);
                            const backupFile = zip.file("uranusfazry_backup.json");
                            if (backupFile) {
                                const jsonContent = await backupFile.async("string");
                                await processImportedData(jsonContent);
                            } else {
                                alert('Invalid ZIP file.');
                            }
                        } catch (error) {
                            console.error('Error reading ZIP:', error);
                            alert('Failed to read ZIP file.');
                        }
                    };
                    reader.readAsArrayBuffer(file);
                } else if (file.type === "text/plain" || file.type === "application/json" || file.name.endsWith(".txt")) {
                    const reader = new FileReader();
                    reader.onload = async (e) => {
                        await processImportedData(e.target.result);
                    };
                    reader.readAsText(file);
                } else {
                    alert("Unsupported file type.");
                }
                event.target.value = '';
            }

            async function processImportedData(jsonContent) {
                try {
                    const importedData = JSON.parse(jsonContent);
                    if (importedData && Array.isArray(importedData.portals)) {
                        localStorage.setItem('portals', JSON.stringify(importedData.portals));
                        showConfirmationModal('Data imported. Page will reload.', () => {
                            location.reload();
                        });
                    } else {
                        alert('Invalid backup format.');
                    }
                } catch (error) {
                    console.error('Error parsing backup:', error);
                    alert('Failed to parse backup file.');
                }
            }

            initPortalApp();
        });
    </script>
</body>
</html>
