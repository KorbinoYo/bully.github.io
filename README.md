<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BULLY</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body {
            font-family: 'IBM Plex Mono', monospace;
            background-color: #ffffff;
            color: #000000;
            -webkit-font-smoothing: antialiased;
            letter-spacing: -0.02em;
        }
        .track-item {
            transition: background-color 0.4s cubic-bezier(0.25, 1, 0.5, 1), color 0.4s ease;
            padding: 8px 12px;
            margin: 0 -12px;
            border-radius: 2px;
        }
        .track-item:hover {
            background-color: #f7f7f7;
            cursor: pointer;
        }
        .track-active {
            background-color: #000000 !important;
            color: #ffffff !important;
        }
        .disabled-btn {
            background-color: #efefef;
            color: #999999;
            cursor: not-allowed;
            transition: all 0.3s ease;
        }
        .album-cover {
            width: 100%;
            max-width: 540px;
            aspect-ratio: 1/1;
            object-fit: cover;
            filter: grayscale(100%);
            transition: filter 0.5s ease;
        }
        .album-cover:hover {
            filter: grayscale(0%);
        }
        ::selection {
            background: #000;
            color: #fff;
        }
    </style>
</head>
<body class="flex flex-col items-center py-16 px-6">

    <div class="w-full max-w-lg">
        <header class="mb-16">
            <h1 class="text-[13px] font-medium tracking-[0.2em]">BULLY</h1>
        </header>

        <section class="mb-16">
            <div id="cover-container" class="flex justify-center">
                <img src="https://cdn.fourthwall.com/offer/sh_1f9d32cb-967c-4531-ba12-3fbe52eeb5d9/71cfd756-321e-4764-b0c7-ceaf0cab410f.png" alt="BULLY COVER" class="album-cover" id="album-art">
            </div>
        </section>

        <section class="mb-16">
            <ul class="text-[11px] sm:text-[12px] uppercase tracking-[0.15em] leading-relaxed" id="tracklist">
                <li class="track-item" data-src="snippet1.mp3">01 PREACHER MAN</li>
                <li class="track-item" data-src="snippet2.mp3">02 BEAUTY AND THE BEAST</li>
                <li class="track-item" data-src="snippet3.mp3">03 LAST BREATH</li>
                <li class="track-item" data-src="snippet4.mp3">04 WHITE LINES</li>
                <li class="track-item" data-src="snippet5.mp3">05 I CAN'T WAIT</li>
                <li class="track-item" data-src="snippet6.mp3">06 BULLY</li>
                <li class="track-item" data-src="snippet7.mp3">07 ALL THE LOVE</li>
                <li class="track-item" data-src="snippet8.mp3">08 THIS ONE HERE</li>
                <li class="track-item" data-src="snippet9.mp3">09 HIGHS AND LOWS</li>
                <li class="track-item" data-src="snippet10.mp3">10 MISSION CONTROL</li>
                <li class="track-item" data-src="snippet11.mp3">11 CIRCLES</li>
                <li class="track-item" data-src="snippet12.mp3">12 DAMN</li>
                <li class="track-item" data-src="snippet13.mp3">13 LOSING YOUR MIND</li>
            </ul>
        </section>

        <section>
            <button class="disabled-btn w-full py-5 text-[10px] uppercase tracking-[0.25em] font-medium" disabled>
                DOWNLOAD DIGITAL ALBUM
            </button>
        </section>

        <footer class="mt-32 pb-16 opacity-20 text-[9px] uppercase tracking-[0.3em]">
            &copy; 2025 YZY. ALL RIGHTS RESERVED.
        </footer>
    </div>

    <audio id="audio-player"></audio>

    <script>
        const player = document.getElementById('audio-player');
        const tracks = document.querySelectorAll('.track-item');

        tracks.forEach(track => {
            track.addEventListener('click', () => {
                const src = track.getAttribute('data-src');
                
                if (track.classList.contains('track-active')) {
                    player.pause();
                    track.classList.remove('track-active');
                    return;
                }

                tracks.forEach(t => t.classList.remove('track-active'));
                
                track.classList.add('track-active');
                player.src = src;
                player.play().catch(e => {
                    console.log("Audio file missing. Replace 'data-src' attributes.");
                });
            });
        });

        player.onended = () => {
            tracks.forEach(t => t.classList.remove('track-active'));
        };
    </script>
</body>
</html>
