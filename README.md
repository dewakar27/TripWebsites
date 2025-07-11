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
      height: 200px;
      object-fit: cover;
    }

    .card-content {
      padding: 1rem;
      flex-grow: 1;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .card-content h2 {
      margin-top: 0;
      margin-bottom: 0.5rem;
    }

    .card-content p {
      margin: 0.5rem 0;
      line-height: 1.4;
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

    .planner label {
      font-weight: 600;
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

    @media (max-width: 768px) {
      .container {
        flex-direction: column;
        align-items: center;
      }
    }
  </style>
</head>
<body>

<header>Compare Trips: Japan vs Seattle</header>

<div class="intro">
  Not sure where to go next? Compare both and plan your dream trip below.
</div>

<div class="container">
  <!-- Japan Card -->
  <div class="card">
    <img src="https://cdn.britannica.com/12/188212-050-71D367A7/Kinkaku-ji-temple-Kyoto-Japan.jpg" alt="Japan Temple" />
    <div class="card-content">
      <h2>Japan</h2>
      <p>🌆 Culture, temples, sushi & high-tech cities.</p>
      <p><strong>Cost:</strong> $250–$300/day</p>
      <p><strong>Flight:</strong> ~$1000 roundtrip</p>
      <a href="https://www.japan.travel/en/" class="btn" target="_blank">Explore Japan</a>
    </div>
  </div>

  <!-- Seattle Card -->
  <div class="card">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Seattle_Skyline_-_July_2015.jpg/1200px-Seattle_Skyline_-_July_2015.jpg" alt="Seattle, Washington" />
    <div class="card-content">
      <h2>Seattle, Washington</h2>
      <p>🌲 Coffee, markets, tech scene & iconic skyline views.</p>
      <p><strong>Cost:</strong> $150–$200/day</p>
      <p><strong>Nearby:</strong> Mt. Rainier, Space Needle, Pike Place</p>
      <a href="https://visitseattle.org" class="btn" target="_blank">Explore Seattle</a>
    </div>
  </div>
</div>

<!-- Trip Planner Section -->
<div class="planner">
  <h3>🧳 Plan Your Trip</h3>
  <form onsubmit="event.preventDefault(); showPlan();">
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

    <button type="submit">Generate My Trip Plan</button>
  </form>

  <div id="trip-output" style="margin-top: 1.5rem; font-weight: 600;"></div>
</div>

<div class="footer">
  Built by <strong>Deju</strong> ❤️ | Questions? Email: 
  <a href="mailto:trips@yourdomain.com">trips@yourdomain.com</a>
</div>

<script>
  function showPlan() {
    const destination = document.getElementById("destination").value;
    const startDate = document.getElementById("start-date").value;
    const endDate = document.getElementById("end-date").value;

    if (!destination || !startDate || !endDate) return;

    const output = document.getElementById("trip-output");
    output.innerHTML = `✅ You’re going to <strong>${destination}</strong> from <strong>${startDate}</strong> to <strong>${endDate}</strong>.  
    Safe travels and enjoy your trip! 🧳✈️`;
  }
</script>

</body>
</html>
