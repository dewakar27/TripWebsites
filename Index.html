<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" /><meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Deju Travel Assistant</title>
  <style>
    body {
      margin: 0;
      font-family: "Segoe UI", sans-serif;
      background: #f4f7fb;
      color: #222;
    }
    header { background: #003366; color: #fff; padding: 1.5rem; text-align:center; font-size:1.8rem; font-weight:600; }
    .intro { padding:1rem; text-align:center; color:#555; }
    /* Cards */
    .day-card { display:flex; flex-direction: column; background:#fff; border-radius:8px; box-shadow:0 4px 10px rgba(0,0,0,0.1); overflow:hidden; margin:1rem 0; }
    .day-card img { width:100%; height:160px; object-fit:cover; }
    .day-content { padding:1rem; }
    .day-content h4 { margin:0 0 .5rem; }
    .btn, .bot-btn { background:#003366; color:#fff; border:none; border-radius:5px; padding:.7rem 1rem; cursor:pointer; font-weight:600; transition:0.2s; }
    .btn:hover, .bot-btn:hover { background:#0059b3; }
    .planner { max-width:800px; margin:2rem auto; padding:2rem; background:#fff; border-radius:10px; box-shadow:0 4px 12px rgba(0,0,0,0.08); }
    .planner input, .planner select { padding:.6rem; font-size:1rem; width:100%; border:1px solid #ccc; border-radius:5px; margin-top: .5rem; }
    .planner label { margin-top:1rem; display:block; font-weight:600; }
    .total { margin:1rem 0; font-weight:600; font-size:1.1rem; }
    .planner button { margin-top:1rem; }
    .footer { text-align:center; color:#555; font-size:0.9rem; margin:2rem 1rem; }
    /* Loader */
    #loader { position:fixed; width:100%; height:100%; background:#003366; display:flex; align-items:center; justify-content:center; flex-direction:column; z-index:9999; }
    .spinner { border:6px solid #f3f3f3; border-top:6px solid #00ccff; border-radius:50%; width:60px; height:60px; animation:spin 1s linear infinite; margin-bottom:1rem; }
    @keyframes spin { to{transform:rotate(360deg);} }
    /* DejuBot */
    #dejuChat { position:fixed; bottom:90px; right:20px; width:320px; max-height:420px; background:#fff; border:2px solid #003366; border-radius:10px; box-shadow:0 4px 12px rgba(0,0,0,0.2); display:none; flex-direction:column; overflow:hidden; z-index:9999; }
    .chat-header { background:#003366; color:#fff; padding:.7rem; font-weight:bold; text-align:center; }
    .chat-body { padding:1rem; flex-grow:1; overflow-y:auto; font-size:.95rem; background:#f9f9f9; }
    .chat-input-area { display:flex; border-top:1px solid #ccc; }
    .chat-input-area input { flex:1; border:none; padding:.6rem; font-size:1rem; }
    .chat-input-area button { background:#003366; color:#fff; border:none; padding:0 .8rem; cursor:pointer; }
    .bot-msg, .user-msg { margin-bottom:.6rem; padding:.6rem; border-radius:8px; max-width:90%; animation:fadeInMsg .4s; }
    .bot-msg { background:#e0ecff; align-self:flex-start; }
    .user-msg { background:#d1ffd1; align-self:flex-end; }
    #toggleChat { position:fixed; bottom:20px; right:20px; background:#003366; color:#fff; border:none; border-radius:50%; width:50px; height:50px; font-size:24px; cursor:pointer; z-index:10000; }
    @keyframes fadeInMsg { from{opacity:0; transform:translateY(10px);} to{opacity:1; transform:translateY(0);} }
    @media(max-width:768px){ .planner, .day-card, #dejuChat { width:90%; right:5%; left:5%; } }
  </style>
</head>
<body>
<div id="loader"><div class="spinner"></div><p style="color:#fff;font-size:1.2rem;">Loading travel vibes...</p></div>

<header>Deju Travel Assistant</header>
<div class="intro">Choose your destination, plan smart budget & enjoy a custom itinerary 😊</div>

<div class="planner">
  <label for="destination">Destination:</label>
  <select id="destination"><option value="">--Select--</option><option value="Japan">Japan</option><option value="Seattle">Seattle</option></select>
  <label for="days">Number of Days (2–7):</label>
  <select id="days"><option value="">--Days--</option><script>for(let i=2;i<=7;i++){document.write(`<option value="${i}">${i}</option>`);}</script></select>
  <label for="flightCost">Flight Cost ($):</label>
  <input type="number" id="flightCost" placeholder="Example: 1000">
  <label for="hotelCost">Avg Hotel per Night ($):</label>
  <input type="number" id="hotelCost" placeholder="e.g., 150">
  <label for="mealBudget">Meal Budget per Day ($):</label>
  <input type="number" id="mealBudget" placeholder="e.g., 60">
  <button class="btn" onclick="buildPlan()">Build My Trip Plan</button>

  <div id="totalBudget" class="total"></div>
  <div id="itineraryCards"></div>
  <button class="btn" onclick="rerollItinerary()">Try a Different Plan</button>
</div>

<button id="toggleChat">💬</button>
<div id="dejuChat">
  <div class="chat-header">DejuBot 🤖 – Travel Assistant</div>
  <div class="chat-body" id="chatBody"><div class="bot-msg">Hi! Tap Build Trip or say “Plan 3 days in Japan” 🗺️</div></div>
  <div class="chat-input-area">
    <input type="text" id="userInput" placeholder="Ask me...">
    <button onclick="sendMessage()">Send</button>
  </div>
</div>

<div class="footer">Built by <strong>Deju</strong> ❤️</div>

<script>
  // Loader
  window.addEventListener("load",()=>{setTimeout(()=>{document.getElementById("loader").style.display="none";},1500);});

  // Bot toggle & messaging
  document.getElementById("toggleChat").onclick=()=>{let c=document.getElementById("dejuChat");c.style.display=(c.style.display==="flex"?"none":"flex");};

  function sendMessage(){
    const msg=document.getElementById("userInput").value.trim();
    if(!msg) return;
    const chat=document.getElementById("chatBody");
    let bubU=document.createElement("div");bubU.className="user-msg";bubU.innerText=msg;chat.appendChild(bubU);
    document.getElementById("userInput").value="";
    setTimeout(()=>{
      let bub=document.createElement("div");bub.className="bot-msg";
      const lower=msg.toLowerCase();
      const daysMatch=msg.match(/(\d+)\s*day/);const d=daysMatch?parseInt(daysMatch[1]):0;
      if(lower.includes("japan")&&d>0){bub.innerHTML=generateCreativeItinerary("Japan",d);}
      else if(lower.includes("seattle")&&d>0){bub.innerHTML=generateCreativeItinerary("Seattle",d);}
      else if(lower.includes("help")){bub.innerText="Tap Build Trip or ask e.g. “Plan 4 days in Seattle”";}
      else{bub.innerText="Sorry, I didn't get that. Try “Plan 3 days in Japan”.";}
      chat.appendChild(bub);chat.scrollTop=chat.scrollHeight;
    },700);
  }

  // Trip building & reroll
  let currentDest="", currentDays=0;
  function buildPlan(){
    currentDest=document.getElementById("destination").value;
    currentDays=parseInt(document.getElementById("days").value);
    if(!currentDest||!currentDays){alert("Fill destination and days.");return;}
    const flight=parseFloat(document.getElementById("flightCost").value)||0;
    const hotel=parseFloat(document.getElementById("hotelCost").value)||0;
    const meal=parseFloat(document.getElementById("mealBudget").value)||0;
    const total=(flight+(hotel*currentDays)+(meal*currentDays)).toFixed(2);
    document.getElementById("totalBudget").innerText=`Estimated Budget: $${total}`;
    showItineraryCards(currentDest,currentDays);
  }
  function rerollItinerary(){
    if(currentDest&&currentDays) showItineraryCards(currentDest, currentDays);
  }

  function generateCreativeItinerary(dest, days){
    const j=["Tokyo Skytree & ramen 🍜","Shibuya Crossing & shops","Mt Fuji + Lake Kawaguchi","Kyoto shrines & bamboo forest","Osaka street‑food night","Hiroshima Peace Park","Nara Deer Park"]; 
    const s=["Pike Place & gum wall","Space Needle + Chihuly Museum","MoPOP & Armory lunch","Mt Rainier day hike","Gas Works Park picnic","Ferry to Bainbridge","Kerry Park sunset view"];
    const spots=dest==="Japan"?j:s;
    let out="";
    for(let i=1;i<=days;i++){const p=spots[Math.floor(Math.random()*spots.length)]; out+=`Day ${i}: ${p}<br>`;}
    return `🗓️ Your ${days}-Day ${dest} Itinerary:<br>${out}`;
  }

  function showItineraryCards(dest, days){
    const container=document.getElementById("itineraryCards");
    container.innerHTML="";
    const pics={
      Japan:[
        "https://images.unsplash.com/photo-1549692520-acc6669e2f0c?auto=format&fit=crop&w=800&q=80",
        "https://images.unsplash.com/photo-1504198458649-3128b932d6d3?auto=format&fit=crop&w=800&q=80",
        "https://images.unsplash.com/photo-1470770903676-69b98201ea1c?auto=format&fit=crop&w=800&q=80"
      ],
      Seattle:[
        "https://images.unsplash.com/photo-1521295121783-8a321d551ad2?auto=format&fit=crop&w=800&q=80",
        "https://images.unsplash.com/photo-1505761671935-60b3a7427bad?auto=format&fit=crop&w=800&q=80",
        "https://images.unsplash.com/photo-1547721064-da6cfb341d50?auto=format&fit=crop&w=800&q=80"
      ]
    };
    for(let i=1;i<=days;i++){
      const card=document.createElement("div");card.className="day-card";
      const img=document.createElement("img");
      const arr=pics[dest];
      img.src=arr[(i-1)%arr.length];
      const c=document.createElement("div");c.className="day-content";
      c.innerHTML=`<h4>Day ${i}</h4>${generateCreativeItinerary(dest,1).split("<br>")[1]}`;
      card.appendChild(img);card.appendChild(c);
      container.appendChild(card);
    }
  }
</script>
</body>
</html>
