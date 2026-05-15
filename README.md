<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trip Plan Showcase</title>
    <style>
        :root {
            --accent: #0284c7;
            --dark: #0f172a;
            --muted: #475569;
            --bg: #f8fafc;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: system-ui, sans-serif; }
        body { background: var(--bg); color: var(--dark); line-height: 1.6; }
        .hero { 
            background: linear-gradient(rgba(15, 23, 42, 0.6), rgba(15, 23, 42, 0.8)), var(--hero-img, #1e293b) center/cover;
            color: white; padding: 80px 20px; text-align: center;
        }
        .hero h1 { font-size: 2.5rem; margin-bottom: 10px; }
        .hero p { font-size: 1.1rem; opacity: 0.9; max-width: 600px; margin: 0 auto; }
        .stats { 
            display: flex; justify-content: space-around; max-width: 800px; 
            margin: -30px auto 40px; background: white; padding: 20px; 
            border-radius: 12px; box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);
        }
        .stat-item { text-align: center; }
        .stat-item .num { font-size: 1.5rem; font-weight: bold; color: var(--accent); }
        .stat-item .label { font-size: 0.8rem; color: var(--muted); text-transform: uppercase; }
        .container { max-width: 1100px; margin: 0 auto; padding: 0 20px; display: grid; grid-template-columns: 2fr 1fr; gap: 30px; }
        @media (max-width: 768px) { .container { grid-template-columns: 1fr; } }
        .section-title { font-size: 1.5rem; margin-bottom: 20px; }
        .timeline { border-left: 3px solid #cbd5e1; padding-left: 20px; margin-left: 10px; }
        .timeline-item { position: relative; margin-bottom: 30px; }
        .timeline-item::before { 
            content: ''; position: absolute; left: -28px; top: 5px; 
            width: 12px; height: 12px; border-radius: 50%; 
            background: var(--accent); border: 3px solid white;
        }
        .time { font-size: 0.85rem; font-weight: bold; color: var(--accent); text-transform: uppercase; }
        .timeline-card { background: white; padding: 15px; border-radius: 8px; margin-top: 5px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); }
        .timeline-card h4 { margin-bottom: 5px; }
        .timeline-card p { font-size: 0.9rem; color: var(--muted); }
        .sidebar { display: flex; flex-direction: column; gap: 20px; }
        .sidebar-panel { background: white; padding: 20px; border-radius: 12px; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05); }
        .sidebar-panel h3 { margin-bottom: 15px; font-size: 1.2rem; }
        .gallery { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
        .gallery img { width: 100%; height: 80px; object-fit: cover; border-radius: 6px; }
        .tag-list { display: flex; flex-wrap: wrap; gap: 8px; list-style: none; }
        .tag { background: #e0f2fe; color: var(--accent); padding: 4px 10px; border-radius: 20px; font-size: 0.8rem; font-weight: 500; }
    </style>
</head>
<body>

    <!-- Target elements populated by JavaScript -->
    <header class="hero" id="heroSection">
        <h1 id="tripTitle"></h1>
        <p id="tripDesc"></p>
    </header>

    <section class="stats" id="statsDashboard"></section>

    <main class="container">
        <section>
            <h2 class="section-title">📅 Itinerary</h2>
            <div class="timeline" id="itineraryTimeline"></div>
        </section>

        <aside class="sidebar">
            <div class="sidebar-panel">
                <h3>📸 Gallery</h3>
                <div class="gallery" id="imageGallery"></div>
            </div>

            <div class="sidebar-panel">
                <h3>🎒 Quick Details</h3>
                <ul class="tag-list" id="tagList"></ul>
            </div>
        </aside>
    </main>

    <script>
        // EDIT YOUR TRIP DATA DIRECTLY IN THIS CONFIGURATION OBJECT BELOW:
        const TRIP_CONFIG = {
            title: "🌲 Pacific Northwest Road Trip",
            description: "A scenic 5-day driving loop through lush temperate rainforests, rugged coastlines, and vibrant mountain towns.",
            heroImage: "https://unsplash.com",
            accentColor: "#0d9488", // Teal hex code

            stats: [
                { label: "Duration", value: "5 Days" },
                { label: "Est. Fuel", value: "$120" },
                { label: "Style", value: "Road Trip" }
            ],

            itinerary: [
                { time: "Day 1 · Morning", title: "Seattle Departure", desc: "Pick up the rental car and head west toward Olympic National Park via the Bainbridge ferry." },
                { time: "Day 1 · Afternoon", title: "Rialto Beach", desc: "Hike along the rocky coastline to see towering sea stacks and dramatic driftwood logs." },
                { time: "Day 2 · Morning", title: "Hoh Rain Forest", desc: "Walk the Hall of Mosses trail to view massive sitka spruce trees blanketed in hanging moss." },
                { time: "Day 3 · All Day", title: "Cannon Beach", desc: "Cross into Oregon to view Haystack Rock and explore tide pools during the afternoon low tide." }
            ],

            galleryImages: [
                "https://unsplash.com",
                "https://unsplash.com",
                "https://unsplash.com",
                "https://unsplash.com"
            ],

            tags: ["🌲 Outdoors", "🚗 Scenic Drive", "🏕️ Camping Friendly", "👟 Hiking", "🌦️ Rain Gear Required"]
        };

        // RENDER ENGINE (Do not modify unless you want to change layout mechanics)
        function renderTrip() {
            document.title = TRIP_CONFIG.title;
            document.documentElement.style.setProperty('--accent', TRIP_CONFIG.accentColor);
            document.getElementById('heroSection').style.setProperty('--hero-img', `url('${TRIP_CONFIG.heroImage}')`);
            document.getElementById('tripTitle').innerText = TRIP_CONFIG.title;
            document.getElementById('tripDesc').innerText = TRIP_CONFIG.description;

            // Render Stats
            document.getElementById('statsDashboard').innerHTML = TRIP_CONFIG.stats.map(s => `
                <div class="stat-item">
                    <div class="num">${s.value}</div>
                    <div class="label">${s.label}</div>
                </div>
            `).join('');

            // Render Itinerary
            document.getElementById('itineraryTimeline').innerHTML = TRIP_CONFIG.itinerary.map(item => `
                <div class="timeline-item">
                    <span class="time">${item.time}</span>
                    <div class="timeline-card">
                        <h4>${item.title}</h4>
                        <p>${item.desc}</p>
                    </div>
                </div>
            `).join('');

            // Render Gallery
            document.getElementById('imageGallery').innerHTML = TRIP_CONFIG.galleryImages.map(imgSrc => `
                <img src="${imgSrc}" alt="Trip Highlight Visual">
            `).join('');

            // Render Tags
            document.getElementById('tagList').innerHTML = TRIP_CONFIG.tags.map(tag => `
                <li class="tag">${tag}</li>
            `).join('');
        }

        // Initialize application build on load
        window.addEventListener('DOMContentLoaded', renderTrip);
    </script>
</body>
</html>
