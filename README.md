<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Trip Planner | Japan vs Seattle</title>
  <style>
    body {
      margin: 0;
      font-family: "Segoe UI", sans-serif;
      background: #f4f7fb;
      color: #222;
    }

    /* Loader Styles */
    #loader {
      position: fixed;
      width: 100%;
      height: 100%;
      background: #003366;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 9999;
    }

    .spinner {
      border: 6px solid #f3f3f3;
      border-top: 6px solid #00ccff;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      animation: spin 1s linear infinite;
      margin-bottom: 1rem;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    header {
      background-color: #003366;
      color: white;
      padding: 1.5rem;
      text-align: center;
      font-size: 1.8rem;
      font-weight: bold;
    }

    .intro {
      text-align: center;
      padding: 1rem;
      font-size: 1.1rem;
      color: #555;
    }

    .container {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      padding: 2rem 1rem;
      gap: 2rem;
    }

    .card {
      background: white;
      border-radius: 8px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.08);
      max-width: 400px;
      flex: 1;
      overflow: hidden;
      display: flex;
      flex-direction: column;
    }

    .card img {
      width: 100%;
      height: 250px;
      object-fit: cover;
    }

    .card-content {
      padding: 1rem;
      flex-grow: 1;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .btn {
      background-color: #003366;
      color: white;
      padding: 0.7rem 1rem;
      text-align: center;
      border-radius: 5px;
      text-decoration: none;
      font-weight: bold;
      margin-top: auto;
      transition: 0.2s;
    }

    .btn:hover {
      background-color: #0059b3;
    }

    .planner {
      max-width: 800px;
      background-color: white;
      margin: 2rem auto;
      padding: 2rem;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
    }

    .planner h3 {
      text-align: center;
      margin-bottom: 1.5rem;
    }

    .planner form {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }

    .planner input, .planner select {
      padding: 0.6rem;
      font-size: 1rem;
      border: 1px solid #ccc;
      border-radius: 5px;
    }

    .planner button {
      background-color: #003366;
      color: white;
      padding: 0.8rem;
      font-size: 1rem;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }

    .planner button:hover {
      background-color: #0059b3;
    }

    .footer {
      text-align: center;
      font-size: 0.9rem;
      color: #555;
      margin: 2rem 1rem 1rem;
    }

    /* AI Assistant */
    #assistant {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: white;
      border: 2px solid #003366;
      padding: 1rem;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      max-width: 300px;
      display: none;
      z-index: 999;
    }

    #assistant h4 {
      margin-top: 0;
    }

    .chat-bubble {
      margin-top: 0.5rem;
      background: #f0f0f0;
      padding: 0.5rem 0.8rem;
      border-radius: 10px;
    }

    #openChat {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: #003366;
      color: white;
      border: none;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      font-size: 24px;
      cursor: pointer;
    }

    @media (max-width: 768px) {
      .container {
        flex-direction: column;
        align-items: center;
      }
    }
  </style>
</head>
<body>

<!-- Loader -->
<div id="loader">
  <div class="spinner"></div>
  <p style="color: white; font-size: 1.2rem;">Loading your trip experience...</p>
</div>

<header>Compare Trips: Japan vs Seattle</header>

<div class="intro">
  Plan smarter, travel happier. Choose your dream destination and let Deju help you build the perfect itinerary ✨
</div>

<div class="container">
  <div class="card">
    <img src="https://images.unsplash.com/photo-1557579958-5a919d7a54a1?auto=format&fit=crop&w=1200&q=80" alt="Tokyo and Mount Fuji" />
    <div class="card-content">
      <h2>Japan</h2>
      <p>🌆 Culture, temples, sushi & high-tech cities.</p>
      <p><strong>Cost:</strong> $250–$300/day</p>
      <p><strong>Flight:</strong> ~$1000 roundtrip</p>
      <a href="https://www.japan.travel/en/" class="btn" target="_blank">Explore Japan</a>
    </div>
  </div>

  <div class="card">
    <img src="https://images.unsplash.com/photo-1589888629804-b2c1f4db26f1?auto=format&fit=crop&w=1200&q=80" alt="Seattle Skyline" />
    <div class="card-content">
      <h2>Seattle, Washington</h2>
      <p>🌲 Coffee, tech, skyline views, Mount Rainier.</p>
      <p><strong>Cost:</strong> $150–$200/day</p>
      <p><strong>Flight:</strong> ~$400–$600 domestic</p>
      <a href="https://visitseattle.org" class="btn" target="_blank">Explore Seattle</a>
    </div>
  </div>
</div>

<div class="planner">
  <h3>🧳 Plan Your Trip</h3>
  <form onsubmit="event.preventDefault(); generatePlan();">
    <label for="destination">Choose Destination:</label>
    <select id="destination" required>
      <option value="">-- Select --</option>
      <option value="Japan">Japan</option>
      <option value="Seattle">Seattle</option>
    </select>

    <label for="start-date">Start Date:</label>
    <input type="date" id="start-date" required />

    <label for="end-date">End Date:</label>
    <input type="date" id="end-date" required />

    <label for="flight-cost">Flight Cost ($):</label>
    <input type="number" id="flight-cost" placeholder="Example: 1000" />

    <button type="submit">Generate My Trip Plan</button>
  </form>

  <div id="trip-output" style="margin-top: 1.5rem; font-weight: 600;"></div>
</div>

<!-- AI Assistant Chat Popup -->
<div id="assistant">
  <h4>Hi, I’m DejuBot 🤖</h4>
  <div class="chat-bubble">Need help picking a destination or budget?</div>
  <div class="chat-bubble">Try Japan for culture 🍣 or Seattle for chill vibes ☕</div>
</div>
<button id="openChat">💬</button>

<div class="footer">
  Built by <strong>Deju</strong> ❤️ | Email: <a href="mailto:trips@yourdomain.com">trips@yourdomain.com</a>
</div>

<script>
  // Loader
  window.addEventListener("load", () => {
    const loader = document.getElementById("loader");
    setTimeout(() => {
      loader.style.display = "none";
    }, 2000);
  });

  // Toggle AI Assistant
  document.getElementById("openChat").onclick = function () {
    const box = document.getElementById("assistant");
    box.style.display = box.style.display === "block" ? "none" : "block";
  };

  // Generate Trip Plan
  function generatePlan() {
    const destination = document.getElementById("destination").value;
    const start = new Date(document.getElementById("start-date").value);
    const end = new Date(document.getElementById("end-date").value);
    const flight = parseFloat(document.getElementById("flight-cost").value) || 0;

    if (!destination || isNaN(start) || isNaN(end)) {
      alert("Please fill out all fields.");
      return;
    }

    const days = Math.ceil((end - start) / (1000 * 60 * 60 * 24)) + 1;
    if (days <= 0) {
      alert("End date must be after start date.");
      return;
    }

    const dailyCost = destination === "Japan" ? 275 : 175;
    const total = (dailyCost * days) + flight;

    let itinerary = "";
    for (let i = 1; i <= days; i++) {
      itinerary += `Day ${i}: Explore ${destination}<br>`;
    }

    document.getElementById("trip-output").innerHTML = `
      ✅ You're going to <strong>${destination}</strong> for <strong>${days} days</strong>.<br><br>
      ✈️ Flight cost: $${flight}<br>
      🏨 Estimated daily cost: $${dailyCost}<br>
      💵 <strong>Total Trip Cost: $${total}</strong><br><br>
      🗓️ <u>Itinerary</u><br>${itinerary}
    `;
  }
</script>

</body>
</html>
