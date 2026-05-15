<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kyoto Explorer - Trip Showcase</title>
    <style>
        :root {
            --accent: #e11d48;
            --dark: #0f172a;
            --muted: #475569;
            --bg: #f8fafc;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: system-ui, sans-serif; }
        body { background: var(--bg); color: var(--dark); line-height: 1.6; }
        
        /* Hero Section */
        .hero { 
            background: linear-gradient(rgba(15, 23, 42, 0.6), rgba(15, 23, 42, 0.8)), url('https://unsplash.com') center/cover;
            color: white; 
            padding: 80px 20px; 
            text-align: center;
        }
        .hero h1 { font-size: 2.5rem; margin-bottom: 10px; }
        .hero p { font-size: 1.1rem; opacity: 0.9; max-width: 600px; margin: 0 auto; }
        
        /* Stats Dashboard */
        .stats { 
            display: flex; 
            justify-content: space-around; 
            max-width: 800px; 
            margin: -30px auto 40px; 
            background: white; 
            padding: 20px; 
            border-radius: 12px; 
            box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);
        }
        .stat-item { text-align: center; }
        .stat-item .num { font-size: 1.5rem; font-weight: bold; color: var(--accent); }
        .stat-item .label { font-size: 0.8rem; color: var(--muted); text-transform: uppercase; }

        /* Main Grid Content */
        .container { max-width: 1100px; margin: 0 auto; padding: 0 20px; display: grid; grid-template-columns: 2fr 1fr; gap: 30px; }
        @media (max-width: 768px) { .container { grid-template-columns: 1fr; } }

        /* Timeline / Schedule */
        .section-title { font-size: 1.5rem; margin-bottom: 20px; display: flex; align-items: center; gap: 10px; }
        .timeline { border-left: 3px solid #cbd5e1; padding-left: 20px; margin-left: 10px; }
        .timeline-item { position: relative; margin-bottom: 30px; }
        .timeline-item::before { 
            content: ''; 
            position: absolute; 
            left: -28px; 
            top: 5px; 
            width: 12px; 
            height: 12px; 
            border-radius: 50%; 
            background: var(--accent); 
            border: 3px solid white;
        }
        .time { font-size: 0.85rem; font-weight: bold; color: var(--accent); }
        .timeline-card { background: white; padding: 15px; border-radius: 8px; margin-top: 5px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); }
        .timeline-card h4 { margin-bottom: 5px; }
        .timeline-card p { font-size: 0.9rem; color: var(--muted); }

        /* Sidebar Cards */
        .sidebar { display: flex; flex-direction: column; gap: 20px; }
        .sidebar-panel { background: white; padding: 20px; border-radius: 12px; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.05); }
        .sidebar-panel h3 { margin-bottom: 15px; font-size: 1.2rem; }
        .gallery { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
        .gallery img { width: 100%; height: 80px; object-fit: cover; border-radius: 6px; cursor: pointer; transition: transform 0.2s; }
        .gallery img:hover { transform: scale(1.05); }
        .tag-list { display: flex; flex-wrap: wrap; gap: 8px; list-style: none; }
        .tag { background: #ffe4e6; color: var(--accent); padding: 4px 10px; border-radius: 20px; font-size: 0.8rem; font-weight: 500; }
    </style>
</head>
<body>

    <!-- Hero Header Component -->
    <header class="hero">
        <h1>🌸 Kyoto Autumn Getaway</h1>
        <p>A curated 3-day itinerary exploring historic temples, bamboo groves, and traditional tea houses in Japan's cultural heart.</p>
    </header>

    <!-- High-level Trip Meta Dashboard -->
    <section class="stats">
        <div class="stat-item"><div class="num">3 Days</div><div class="label">Duration</div></div>
        <div class="stat-item"><div class="num">$650</div><div class="label">Est. Budget</div></div>
        <div class="stat-item"><div class="num">Solo</div><div class="label">Trip Style</div></div>
    </section>

    <!-- Main Content Area -->
    <main class="container">
        
        <!-- Interactive Itinerary Section -->
        <section>
            <h2 class="section-title">📅 Daily Itinerary Schedule</h2>
            <div class="timeline">
                <div class="timeline-item">
                    <span class="time">DAY 1 · MORNING</span>
                    <div class="timeline-card">
                        <h4>Fushimi Inari Shrine</h4>
                        <p>Hike early through thousands of vibrant vermilion torii gates up Mount Inari to avoid large midday crowds.</p>
                    </div>
                </div>
                <div class="timeline-item">
                    <span class="time">DAY 1 · AFTERNOON</span>
                    <div class="timeline-card">
                        <h4>Kiyomizu-dera Temple</h4>
                        <p>Explore the historic wooden stage offering sweeping panoramic vistas over the hillside cherry and maple trees.</p>
                    </div>
                </div>
                <div class="timeline-item">
                    <span class="time">DAY 2 · ALL DAY</span>
                    <div class="timeline-card">
                        <h4>Arashiyama Bamboo Grove</h4>
                        <p>Stroll the towering green stalks, visit the nearby Tenryu-ji landscape garden, and cross Togetsukyo Bridge.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Dynamic Sidebar Panels -->
        <aside class="sidebar">
            <!-- Visual Asset Gallery -->
            <div class="sidebar-panel">
                <h3>📸 Route Highlights</h3>
                <div class="gallery">
                    <img src="https://unsplash.com" alt="Kyoto temple" onclick="alert('Viewing: Kiyomizu-dera')">
                    <img src="https://unsplash.com" alt="Torii gates" onclick="alert('Viewing: Fushimi Inari')">
                    <img src="https://unsplash.com" alt="Gion streets" onclick="alert('Viewing: Gion District')">
                    <img src="https://unsplash.com" alt="Bamboo forest" onclick="alert('Viewing: Arashiyama')">
                </div>
            </div>

            <!-- Trip Logistics / Metadata Tags -->
            <div class="sidebar-panel">
                <h3>🎒 Quick Details</h3>
                <ul class="tag-list">
                    <li class="tag">🍁 Autumn Peak</li>
                    <li class="tag">🚊 JR Pass Valid</li>
                    <li class="tag">🍣 Foodie Friendly</li>
                    <li class="tag">👟 Heavy Walking</li>
                    <li class="tag">📷 Photography Tour</li>
                </ul>
            </div>
        </aside>

    </main>

</body>
</html>
