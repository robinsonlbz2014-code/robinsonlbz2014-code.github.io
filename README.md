<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WanderPlan - One-Page Trip Planner</title>
    <style>
        :root {
            --primary: #2563eb;
            --secondary: #0ea5e9;
            --dark: #1e293b;
            --light: #f8fafc;
            --success: #22c55e;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: system-ui, sans-serif; }
        body { background: var(--light); color: var(--dark); padding: 20px; }
        header { text-align: center; margin-bottom: 30px; background: linear-gradient(135deg, var(--primary), var(--secondary)); padding: 40px 20px; color: white; border-radius: 12px; }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; max-width: 1200px; margin: 0 auto; }
        .card { background: white; padding: 20px; border-radius: 12px; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1); }
        h2 { margin-bottom: 15px; color: var(--primary); border-bottom: 2px solid var(--light); padding-bottom: 5px; }
        input, button { width: 100%; padding: 10px; margin-bottom: 10px; border: 1px solid #cbd5e1; border-radius: 6px; font-size: 14px; }
        button { background: var(--primary); color: white; border: none; font-weight: bold; cursor: pointer; }
        button:hover { background: #1d4ed8; }
        ul { list-style: none; }
        li { padding: 10px; background: var(--light); margin-bottom: 8px; border-radius: 6px; display: flex; justify-content: space-between; align-items: center; }
        .delete-btn { width: auto; margin: 0; padding: 4px 8px; background: #ef4444; }
        .delete-btn:hover { background: #dc2626; }
        .checked { text-decoration: line-through; opacity: 0.6; }
    </style>
</head>
<body>

    <header>
        <h1>📍 WanderPlan</h1>
        <p>Your Ultimate Single-Page Trip Companion</p>
    </header>

    <div class="grid">
        <!-- Section 1: Trip Details -->
        <div class="card">
            <h2>✈️ Destination</h2>
            <input type="text" id="destInput" placeholder="Where are you going?">
            <input type="date" id="dateInput">
            <button onclick="saveDetails()">Save Trip Details</button>
            <p id="tripDisplay" style="margin-top: 15px; font-weight: bold; text-align: center;"></p>
        </div>

        <!-- Section 2: Itinerary Builder -->
        <div class="card">
            <h2>📅 Itinerary</h2>
            <input type="text" id="activityInput" placeholder="e.g., Visit Eiffel Tower">
            <input type="time" id="timeInput">
            <button onclick="addActivity()">Add Activity</button>
            <ul id="itineraryList"></ul>
        </div>

        <!-- Section 3: Packing Checklist -->
        <div class="card">
            <h2>🧳 Packing List</h2>
            <input type="text" id="itemInput" placeholder="e.g., Passport, Charger">
            <button onclick="addItem()">Add Item</button>
            <ul id="packingList"></ul>
        </div>
    </div>

    <script>
        // Save Destination Details
        function saveDetails() {
            const dest = document.getElementById('destInput').value;
            const date = document.getElementById('dateInput').value;
            if (!dest || !date) return alert('Please fill in all fields');
            document.getElementById('tripDisplay').innerText = `🚀 Trip to ${dest} on ${date}!`;
        }

        // Add Activity to Itinerary
        function addActivity() {
            const activity = document.getElementById('activityInput').value;
            const time = document.getElementById('timeInput').value;
            if (!activity || !time) return alert('Please enter activity and time');
            
            const li = document.createElement('li');
            li.innerHTML = `<span>⏰ ${time} - ${activity}</span> <button class="delete-btn" onclick="this.parentElement.remove()">X</button>`;
            document.getElementById('itineraryList').appendChild(li);
            
            document.getElementById('activityInput').value = '';
            document.getElementById('timeInput').value = '';
        }

        // Add Item to Packing List
        function addItem() {
            const item = document.getElementById('itemInput').value;
            if (!item) return alert('Please enter an item');
            
            const li = document.createElement('li');
            li.innerHTML = `<span onclick="this.classList.toggle('checked')" style="cursor:pointer;">⬜ ${item}</span> <button class="delete-btn" onclick="this.parentElement.remove()">X</button>`;
            document.getElementById('packingList').appendChild(li);
            
            document.getElementById('itemInput').value = '';
        }
    </script>
</body>
</html>
