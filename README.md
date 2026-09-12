# food-waste-management
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hostel Waste Management</title>
  
  <!-- Link your CSS file -->
  <link rel="stylesheet" href="style.css">
  
  <!-- Load Chart.js library -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>

  <!-- Paste your HTML content here -->

  <!-- Link your JavaScript file BEFORE body closes -->
  <script src="script.js"></script>
</body>
</html><!-- Chart.js CDN Integration -->
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<!-- Top Navigation Header -->
<header>
  <div class="brand">
    <div class="brand-icon">♻</div>
    <span>Hostel Food Waste Management</span>
  </div>
  <nav>
    <a href="#dashboard" onclick="switchNav('Dashboard')">Dashboard</a>
    <a href="#guides" onclick="openModal('Composting Guide')">Guides</a>
    <a href="#leaderboard" onclick="switchNav('Leaderboard')">Leaderboards</a>
  </nav>
</header>

<div class="container">

  <!-- Core Action Buttons -->
  <div class="action-grid">
    <div class="action-card">
      <div class="img-preview">🍛</div>
      <button class="btn-blue" onclick="openModal('Report Food Waste')">Report Food Waste</button>
    </div>
    <div class="action-card">
      <div class="img-preview">🗑️</div>
      <button class="btn-green" onclick="openModal('Segregate Waste')">Segregate Waste</button>
    </div>
    <div class="action-card">
      <div class="img-preview">📶</div>
      <button class="btn-blue" onclick="openModal('Track Bin Levels')">Track Bin Levels</button>
    </div>
    <div class="action-card">
      <div class="img-preview">🚛</div>
      <button class="btn-green" onclick="openModal('Request Pickup')">Request Pickup</button>
    </div>
  </div>

  <!-- Analytics Dashboard Panels -->
  <div class="dashboard-grid">
    
    <!-- Panel 1: Daily Waste Overview -->
    <div class="panel">
      <div class="panel-title">Daily Waste Overview</div>
      <div class="kpi-row">
        <span>➕ Total Waste Today:</span>
        <span class="kpi-value" id="kpiTotal">250 kg</span>
      </div>
      <div class="kpi-row">
        <span>✅ Composted:</span>
        <span class="kpi-value" id="kpiComposted">150 kg</span>
      </div>
      <div class="kpi-row">
        <span>✔️ Recycled:</span>
        <span class="kpi-value" id="kpiRecycled">70 kg</span>
      </div>
      
      <!-- Chart Canvas -->
      <div class="chart-box">
        <canvas id="wasteDistributionChart"></canvas>
      </div>
    </div>

    <!-- Panel 2: Environmental Impact -->
    <div class="panel">
      <div class="panel-title">Environmental Impact</div>
      
      <div class="env-highlight">
        <div style="font-size: 0.85rem; color: #444;">Carbon Savings</div>
        <div class="val" id="envCarbon">320 kg CO₂ Reduced</div>
      </div>

      <div class="env-highlight" style="background: #e1f5fe; border-left-color: var(--btn-blue);">
        <div style="font-size: 0.85rem; color: #444;">Energy Generated</div>
        <div class="val" style="color: var(--btn-blue);" id="envEnergy">50 kWh from Biogas</div>
      </div>

      <div style="margin-top: auto; font-size: 0.85rem; color: var(--text-muted);">
        ⚡ Rapid 7-day bio-drum composter prevents anaerobic decay, drastically cutting methane emissions[cite: 1].
      </div>
    </div>

    <!-- Panel 3: Student Leaderboard -->
    <div class="panel">
      <div class="panel-title" style="display: flex; justify-content: space-between;">
        <span>Student Leaderboard</span>
        <a href="#" style="font-size: 0.8rem; color: var(--btn-blue);" onclick="openModal('Leaderboard Details')">View All &gt;</a>
      </div>
      <ul class="lb-list">
        <li class="lb-item">
          <div class="lb-avatar" style="background: #ffe0b2;">🥇</div>
          <div style="flex: 1;">
            <strong>1. Block A</strong>
            <div style="font-size: 0.8rem; color: #777;">750 pts</div>
          </div>
        </li>
        <li class="lb-item">
          <div class="lb-avatar" style="background: #e1bee7;">🥈</div>
          <div style="flex: 1;">
            <strong>2. Block C</strong>
            <div style="font-size: 0.8rem; color: #777;">620 pts</div>
          </div>
        </li>
        <li class="lb-item">
          <div class="lb-avatar" style="background: #b2dfdb;">🥉</div>
          <div style="flex: 1;">
            <strong>3. Block B</strong>
            <div style="font-size: 0.8rem; color: #777;">580 pts</div>
          </div>
        </li>
      </ul>
    </div>
  </div>

  <!-- Calculated Cost Savings Section -->
  <div class="financial-section">
    <div class="panel-title">📊 Calculated Cost Savings & Financial Projections</div>
    <p style="font-size: 0.9rem; color: #555; margin: 0;">
      Based on replacing commercial fertilizer and cutting off-site municipal transit expenses for campus operations[cite: 1].
    </p>
    <div class="fin-grid">
      <div class="fin-card">
        <div style="font-size: 0.85rem; color: #666;">Chemical Fertilizer Savings</div>
        <div class="num" id="costFertilizer">₹96,000 / yr</div>
      </div>
      <div class="fin-card">
        <div style="font-size: 0.85rem; color: #666;">Waste Transport Savings</div>
        <div class="num" id="costTransport">₹1,44,000 / yr</div>
      </div>
      <div class="fin-card">
        <div style="font-size: 0.85rem; color: #666;">Labor & Operational Savings</div>
        <div class="num" id="costLabor">₹60,000 / yr</div>
      </div>
      <div class="fin-card" style="border-top-color: var(--btn-blue);">
        <div style="font-size: 0.85rem; color: #666;">Total Net Savings</div>
        <div class="num" style="color: var(--btn-blue);" id="costTotal">₹3,00,000 / yr</div>
      </div>
    </div>
  </div>

  <!-- Support, Education & Donation Row -->
  <div class="support-grid">
    <div class="support-card" onclick="openModal('Composting Guide')">
      <div class="support-card-left">
        <span style="font-size: 1.5rem;">🌱</span>
        <span>Composting Guide</span>
      </div>
      <span>&rsaquo;</span>
    </div>

    <div class="support-card" onclick="openModal('Recycling Rules')">
      <div class="support-card-left">
        <span style="font-size: 1.5rem;">♻️</span>
        <span>Recycling Rules</span>
      </div>
      <span>&rsaquo;</span>
    </div>

    <div class="support-card" onclick="openModal('Donate Surplus Food')">
      <div class="support-card-left">
        <span style="font-size: 1.5rem;">🎁</span>
        <span>Donate Surplus Food</span>
      </div>
      <span>&rsaquo;</span>
    </div>
  </div>

  <!-- Special Emergency Alert Buttons -->
  <div class="emergency-grid">
    <button class="btn-alert-danger" onclick="openModal('Report Hazardous Waste')">
      ⚠️ Report Hazardous Waste &rsaquo;
    </button>
    <button class="btn-alert-warning" onclick="openModal('Emergency Overflow')">
      ⚠️ Emergency Overflow Alert &rsaquo;
    </button>
  </div>

</div>

<!-- Reusable Modal Window -->
<div class="modal-overlay" id="modalOverlay">
  <div class="modal-content">
    <h3 id="modalTitle">Modal Title</h3>
    <div id="modalBody"></div>
    <div class="modal-actions">
      <button class="btn-close" onclick="closeModal()">Close</button>
      <button class="btn-submit" id="modalSubmitBtn" onclick="submitModal()">Submit</button>
    </div>
  </div>
</div>
root {
  --bg-gradient: linear-gradient(135deg, #eef4f0 0%, #e2ede7 100%);
  --header-bg: #1c6b37;
  --card-bg: #ffffff;
  --text-dark: #2c3e50;
  --text-muted: #666666;
  --btn-blue: #0277bd;
  --btn-green: #2e7d32;
  --btn-orange: #d84315;
  --btn-red: #c62828;
  --border-radius: 12px;
  --shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

* { 
  box-sizing: border-box; 
}

body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: var(--bg-gradient);
  color: var(--text-dark);
  padding-bottom: 40px;
}

/* Header */
header {
  background: var(--header-bg);
  color: white;
  padding: 14px 28px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
}

.brand {
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: 1.3rem;
  font-weight: 700;
}

.brand-icon {
  width: 32px;
  height: 32px;
  background: #4caf50;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}

nav {
  display: flex;
  gap: 20px;
  font-size: 0.95rem;
}

nav a {
  color: white;
  text-decoration: none;
  opacity: 0.9;
  transition: opacity 0.2s;
}

nav a:hover { 
  opacity: 1; 
  text-decoration: underline; 
}

/* Layout Container */
.container {
  max-width: 1140px;
  margin: 24px auto;
  padding: 0 16px;
}

/* Action Cards */
.action-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
  margin-bottom: 24px;
}

.action-card {
  background: var(--card-bg);
  border-radius: var(--border-radius);
  box-shadow: var(--shadow);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.action-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.12);
}

.action-card .img-preview {
  width: 100%;
  height: 110px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #f8faf9;
  font-size: 2.8rem;
}

.action-card button {
  width: 100%;
  border: none;
  padding: 12px;
  color: white;
  font-weight: 700;
  font-size: 0.95rem;
  cursor: pointer;
  transition: background 0.2s;
}

.btn-blue { background: var(--btn-blue); }
.btn-blue:hover { background: #01579b; }

.btn-green { background: var(--btn-green); }
.btn-green:hover { background: #1b5e20; }

/* Dashboard Grid */
.dashboard-grid {
  display: grid;
  grid-template-columns: 1fr 1.2fr 1fr;
  gap: 16px;
  margin-bottom: 24px;
}

@media (max-width: 900px) {
  .dashboard-grid { grid-template-columns: 1fr; }
}

.panel {
  background: var(--card-bg);
  border-radius: var(--border-radius);
  padding: 20px;
  box-shadow: var(--shadow);
  display: flex;
  flex-direction: column;
}

.panel-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--header-bg);
  margin-bottom: 16px;
  padding-bottom: 8px;
  border-bottom: 2px solid #eef4f0;
}

.kpi-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 12px;
  font-weight: 600;
  font-size: 0.95rem;
}

.kpi-value {
  font-size: 1.1rem;
  color: var(--text-dark);
  font-weight: 700;
}

.chart-box {
  position: relative;
  height: 180px;
  margin-top: auto;
}

.env-highlight {
  background: #e8f5e9;
  border-left: 4px solid var(--btn-green);
  padding: 12px;
  border-radius: 6px;
  margin-bottom: 12px;
}

.env-highlight .val {
  font-size: 1.25rem;
  font-weight: 800;
  color: var(--btn-green);
}

/* Financial Projections */
.financial-section {
  background: var(--card-bg);
  border-radius: var(--border-radius);
  padding: 20px;
  box-shadow: var(--shadow);
  margin-bottom: 24px;
}

.fin-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 12px;
  margin-top: 14px;
}

.fin-card {
  background: #f4f6f8;
  padding: 14px;
  border-radius: 8px;
  text-align: center;
  border-top: 3px solid var(--btn-green);
}

.fin-card .num {
  font-size: 1.3rem;
  font-weight: 800;
  color: var(--header-bg);
  margin-top: 4px;
}

/* Leaderboard */
.lb-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.lb-item {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 10px 0;
  border-bottom: 1px solid #eee;
}

.lb-avatar {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: #cfd8dc;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}

/* Support & Education */
.support-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 16px;
  margin-bottom: 24px;
}

.support-card {
  background: var(--card-bg);
  border-radius: var(--border-radius);
  padding: 16px 20px;
  box-shadow: var(--shadow);
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
  transition: background 0.2s;
}

.support-card:hover { background: #f8faf9; }

.support-card-left {
  display: flex;
  align-items: center;
  gap: 12px;
  font-weight: 600;
}

/* Emergency Buttons */
.emergency-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

@media (max-width: 650px) {
  .emergency-grid { grid-template-columns: 1fr; }
}

.btn-alert-danger {
  background: var(--btn-red);
  color: white;
  border: none;
  padding: 16px;
  border-radius: var(--border-radius);
  font-weight: 700;
  font-size: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  cursor: pointer;
  box-shadow: var(--shadow);
}

.btn-alert-warning {
  background: var(--btn-orange);
  color: white;
  border: none;
  padding: 16px;
  border-radius: var(--border-radius);
  font-weight: 700;
  font-size: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  cursor: pointer;
  box-shadow: var(--shadow);
}

/* Modals */
.modal-overlay {
  position: fixed;
  top: 0; left: 0; width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: none;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  padding: 24px;
  border-radius: 12px;
  max-width: 500px;
  width: 90%;
  box-shadow: 0 10px 25px rgba(0,0,0,0.2);
}

.modal-content h3 { margin-top: 0; color: var(--header-bg); }
.modal-content label { display: block; margin: 10px 0 4px; font-weight: 600; }
.modal-content input, .modal-content select, .modal-content textarea {
  width: 100%; padding: 8px 12px; border: 1px solid #ccc; border-radius: 6px;
}

.modal-actions {
  display: flex; justify-content: flex-end; gap: 10px; margin-top: 18px;
}

.btn-close { 
  background: #78909c; 
  color: white; 
  border: none; 
  padding: 8px 16px; 
  border-radius: 4px; 
  cursor: pointer; 
}

.btn-submit { 
  background: var(--btn-green); 
  color: white; 
  border: none; 
  padding: 8px 16px; 
  border-radius: 4px; 
  cursor: pointer; 
}
// State Tracking
let wasteData = { total: 250, composted: 150, recycled: 70, landfilled: 30 };
let chartInstance = null;

// Initialize Chart.js Donut Chart
window.addEventListener('DOMContentLoaded', () => {
  initChart();
});

function initChart() {
  const ctx = document.getElementById('wasteDistributionChart').getContext('2d');
  chartInstance = new Chart(ctx, {
    type: 'doughnut',
    data: {
      labels: ['Composted', 'Recycled', 'Landfilled'],
      datasets: [{
        data: [wasteData.composted, wasteData.recycled, wasteData.landfilled],
        backgroundColor: ['#2e7d32', '#0277bd', '#d84315'],
        borderWidth: 2
      }]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      plugins: {
        legend: { position: 'bottom', labels: { boxWidth: 12, font: { size: 11 } } }
      },
      cutout: '65%'
    }
  });
}

function updateMetrics() {
  document.getElementById('kpiTotal').innerText = `${wasteData.total} kg`;
  document.getElementById('kpiComposted').innerText = `${wasteData.composted} kg`;
  document.getElementById('kpiRecycled').innerText = `${wasteData.recycled} kg`;
  
  // Dynamic financial projections
  const annualBase = wasteData.composted * 365 * 5.5;
  document.getElementById('costFertilizer').innerText = `₹${Math.round(annualBase * 0.32).toLocaleString('en-IN')} / yr`;
  document.getElementById('costTransport').innerText = `₹${Math.round(annualBase * 0.48).toLocaleString('en-IN')} / yr`;
  document.getElementById('costLabor').innerText = `₹${Math.round(annualBase * 0.20).toLocaleString('en-IN')} / yr`;
  document.getElementById('costTotal').innerText = `₹${Math.round(annualBase).toLocaleString('en-IN')} / yr`;

  if (chartInstance) {
    chartInstance.data.datasets[0].data = [wasteData.composted, wasteData.recycled, wasteData.landfilled];
    chartInstance.update();
  }
}

// Modal Handlers
function openModal(actionType) {
  const modal = document.getElementById('modalOverlay');
  const title = document.getElementById('modalTitle');
  const body = document.getElementById('modalBody');
  const submitBtn = document.getElementById('modalSubmitBtn');
  
  modal.style.display = 'flex';
  title.innerText = actionType;
  submitBtn.style.display = 'inline-block';

  switch(actionType) {
    case 'Report Food Waste':
      body.innerHTML = `
        <label>Select Hostel / Mess:</label>
        <select id="swHostel"><option>Hostel Block A</option><option>Hostel Block B</option><option>Hostel Block C</option></select>
        <label>Daily Waste Amount (kg):</label>
        <input type="number" id="swAmount" placeholder="e.g. 25" />
      `;
      break;

    case 'Segregate Waste':
      body.innerHTML = `
        <label>Item Description:</label>
        <input type="text" id="segItem" placeholder="e.g. Dairy leftovers, Plastic cups..." />
        <button style="margin-top:10px; width:100%; padding:8px; background:#2e7d32; color:white; border:none; border-radius:4px;" onclick="checkSegregation()">Check Category</button>
        <div id="segFeedback" style="margin-top:10px; font-weight:600; padding:8px; border-radius:4px;"></div>
      `;
      submitBtn.style.display = 'none';
      break;

    case 'Track Bin Levels':
      body.innerHTML = `
        <p><strong>Mess Sensor Status (Real-time IoT):</strong></p>
        <ul>
          <li>Block A Smart Bin: <strong style="color:red;">88% Full</strong></li>
          <li>Block B Smart Bin: <strong style="color:green;">42% Full</strong></li>
          <li>Block C Smart Bin: <strong style="color:orange;">65% Full</strong></li>
        </ul>
      `;
      submitBtn.style.display = 'none';
      break;

    case 'Request Pickup':
      body.innerHTML = `
        <label>Pickup Location:</label>
        <select><option>Main Canteen Dumpster</option><option>Hostel Rear Bio-Drum</option></select>
        <label>Preferred Time Slot:</label>
        <input type="time" value="16:00" />
      `;
      break;

    case 'Composting Guide':
      body.innerHTML = `
        <p><strong>Rapid 7-Day Composting Rules:</strong></p>
        <ol>
          <li>Load degradable organic scraps (rice, vegetables, fruits) directly into bio-drum[cite: 1].</li>
          <li>Avoid non-compostable oils/meat scrap loads above 15% to ensure zero-odor operation[cite: 1].</li>
          <li>Bio-drum runs automated thermophilic fermentation for 7 days[cite: 1].</li>
        </ol>
      `;
      submitBtn.style.display = 'none';
      break;

    case 'Recycling Rules':
      body.innerHTML = `
        <p><strong>Stream Sorting Guidelines:</strong></p>
        <ul>
          <li><strong>Recyclable:</strong> Plastics, clean paper, metal cans, glass[cite: 1].</li>
          <li><strong>Biogas Stream:</strong> Fats, oils, heavy dairy scraps (processed via Anaerobic Digestion)[cite: 1].</li>
          <li><strong>Reject Stream:</strong> Mixed laminate snack packaging[cite: 1].</li>
        </ul>
      `;
      submitBtn.style.display = 'none';
      break;

    case 'Donate Surplus Food':
      body.innerHTML = `
        <label>Edible Surplus Servings Available:</label>
        <input type="number" placeholder="e.g. 50 meals" />
        <label>Partner NGO Pickup Channel:</label>
        <select><option>Local Food Bank Network</option><option>Community Kitchen Trust</option></select>
      `;
      break;

    case 'Report Hazardous Waste':
      body.innerHTML = `
        <p style="color:red;"><strong>⚠️ Hazardous Spill / Waste Alert</strong></p>
        <label>Hazard Type:</label>
        <select><option>Batteries / E-waste</option><option>Chemical Cleaners</option><option>Medical / Lab Residue</option></select>
        <label>Location Details:</label>
        <input type="text" placeholder="e.g. Block A Storage Yard" />
      `;
      break;

    case 'Emergency Overflow':
      body.innerHTML = `
        <p style="color:orange;"><strong>⚠️ Immediate Bin Clearance Request</strong></p>
        <label>Bin Identifier:</label>
        <input type="text" value="Main Hostel Canteen Dumpster #2" />
        <label>Urgency Level:</label>
        <select><option>Critical (Overflowing)</option><option>High (>90%)</option></select>
      `;
      break;

    default:
      body.innerHTML = `<p>Action triggered: ${actionType}</p>`;
      submitBtn.style.display = 'none';
  }
}

function closeModal() {
  document.getElementById('modalOverlay').style.display = 'none';
}

function submitModal() {
  const title = document.getElementById('modalTitle').innerText;
  
  if (title === 'Report Food Waste') {
    const amt = parseFloat(document.getElementById('swAmount').value) || 0;
    if (amt > 0) {
      wasteData.total += amt;
      wasteData.composted += Math.round(amt * 0.7);
      wasteData.recycled += Math.round(amt * 0.3);
      updateMetrics();
      alert(`Logged ${amt} kg food waste successfully!`);
    }
  } else {
    alert(`${title} dispatch request sent successfully!`);
  }
  
  closeModal();
}

function checkSegregation() {
  const item = document.getElementById('segItem').value.toLowerCase();
  const fb = document.getElementById('segFeedback');
  
  if (!item) return;

  if (['rice', 'vegetable', 'fruit', 'bread', 'peel'].some(w => item.includes(w))) {
    fb.style.background = '#d4edda';
    fb.style.color = '#155724';
    fb.innerText = '✅ Compostable Stream: Load into Rapid Bio-Drum[cite: 1].';
  } else if (['milk', 'oil', 'dairy', 'fat', 'meat'].some(w => item.includes(w))) {
    fb.style.background = '#fff3cd';
    fb.style.color = '#856404';
    let wasteData = { total: 250, composted: 150, recycled: 70, landfilled: 30 };
let chartInstance = null;

window.addEventListener('DOMContentLoaded', () => {
  initChart();
});

function initChart() {
  const canvas = document.getElementById('wasteDistributionChart');
  if (!canvas) return;
  const ctx = canvas.getContext('2d');
  
  chartInstance = new Chart(ctx, {
    type: 'doughnut',
    data: {
      labels: ['Composted', 'Recycled', 'Landfilled'],
      datasets: [{
        data: [wasteData.composted, wasteData.recycled, wasteData.landfilled],
        backgroundColor: ['#2e7d32', '#0277bd', '#d84315'],
        borderWidth: 2
      }]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      plugins: {
        legend: { position: 'bottom', labels: { boxWidth: 12, font: { size: 11 } } }
      },
      cutout: '65%'
    }
  });
}

function updateMetrics() {
  document.getElementById('kpiTotal').innerText = `${wasteData.total} kg`;
  document.getElementById('kpiComposted').innerText = `${wasteData.composted} kg`;
  document.getElementById('kpiRecycled').innerText = `${wasteData.recycled} kg`;
  
  const annualBase = wasteData.composted * 365 * 5.5;
  document.getElementById('costFertilizer').innerText = `₹${Math.round(annualBase * 0.32).toLocaleString('en-IN')} / yr`;
  document.getElementById('costTransport').innerText = `₹${Math.round(annualBase * 0.48).toLocaleString('en-IN')} / yr`;
  document.getElementById('costLabor').innerText = `₹${Math.round(annualBase * 0.20).toLocaleString('en-IN')} / yr`;
  document.getElementById('costTotal').innerText = `₹${Math.round(annualBase).toLocaleString('en-IN')} / yr`;

  if (chartInstance) {
    chartInstance.data.datasets[0].data = [wasteData.composted, wasteData.recycled, wasteData.landfilled];
    chartInstance.update();
  }
}

function openModal(actionType) {
  const modal = document.getElementById('modalOverlay');
  const title = document.getElementById('modalTitle');
  const body = document.getElementById('modalBody');
  const submitBtn = document.getElementById('modalSubmitBtn');
  
  modal.style.display = 'flex';
  title.innerText = actionType;
  submitBtn.style.display = 'inline-block';

  switch(actionType) {
    case 'Report Food Waste':
      body.innerHTML = `
        <label>Select Hostel / Mess:</label>
        <select id="swHostel"><option>Hostel Block A</option><option>Hostel Block B</option><option>Hostel Block C</option></select>
        <label>Daily Waste Amount (kg):</label>
        <input type="number" id="swAmount" placeholder="e.g. 25" />
      `;
      break;

    case 'Segregate Waste':
      body.innerHTML = `
        <label>Item Description:</label>
        <input type="text" id="segItem" placeholder="e.g. Dairy leftovers, Plastic cups..." />
        <button style="margin-top:10px; width:100%; padding:8px; background:#2e7d32; color:white; border:none; border-radius:4px;" onclick="checkSegregation()">Check Category</button>
        <div id="segFeedback" style="margin-top:10px; font-weight:600; padding:8px; border-radius:4px;"></div>
      `;
      submitBtn.style.display = 'none';
      break;

    case 'Track Bin Levels':
      body.innerHTML = `
        <p><strong>Mess Sensor Status (Real-time IoT):</strong></p>
        <ul>
          <li>Block A Smart Bin: <strong style="color:red;">88% Full</strong></li>
          <li>Block B Smart Bin: <strong style="color:green;">42% Full</strong></li>
          <li>Block C Smart Bin: <strong style="color:orange;">65% Full</strong></li>
        </ul>
      `;
      submitBtn.style.display = 'none';
      break;

    case 'Request Pickup':
      body.innerHTML = `
        <label>Pickup Location:</label>
        <select><option>Main Canteen Dumpster</option><option>Hostel Rear Bio-Drum</option></select>
        <label>Preferred Time Slot:</label>
        <input type="time" value="16:00" />
      `;
      break;

    case 'Composting Guide':
      body.innerHTML = `
        <p><strong>Rapid 7-Day Composting Rules:</strong></p>
        <ol>
          <li>Load degradable organic scraps (rice, vegetables, fruits) directly into bio-drum.</li>
          <li>Avoid non-compostable oils/meat scrap loads above 15% to ensure zero-odor operation.</li>
          <li>Bio-drum runs automated thermophilic fermentation for 7 days.</li>
        </ol>
      `;
      submitBtn.style.display = 'none';
      break;

    case 'Recycling Rules':
      body.innerHTML = `
        <p><strong>Stream Sorting Guidelines:</strong></p>
        <ul>
          <li><strong>Recyclable:</strong> Plastics, clean paper, metal cans, glass.</li>
          <li><strong>Biogas Stream:</strong> Fats, oils, heavy dairy scraps (processed via Anaerobic Digestion).</li>
          <li><strong>Reject Stream:</strong> Mixed laminate snack packaging.</li>
        </ul>
      `;
      submitBtn.style.display = 'none';
      break;

    case 'Donate Surplus Food':
      body.innerHTML = `
        <label>Edible Surplus Servings Available:</label>
        <input type="number" placeholder="e.g. 50 meals" />
        <label>Partner NGO Pickup Channel:</label>
        <select><option>Local Food Bank Network</option><option>Community Kitchen Trust</option></select>
      `;
      break;

    case 'Report Hazardous Waste':
      body.innerHTML = `
        <p style="color:red;"><strong>⚠️ Hazardous Spill / Waste Alert</strong></p>
        <label>Hazard Type:</label>
        <select><option>Batteries / E-waste</option><option>Chemical Cleaners</option><option>Medical / Lab Residue</option></select>
        <label>Location Details:</label>
        <input type="text" placeholder="e.g. Block A Storage Yard" />
      `;
      break;

    case 'Emergency Overflow':
      body.innerHTML = `
        <p style="color:orange;"><strong>⚠️ Immediate Bin Clearance Request</strong></p>
        <label>Bin Identifier:</label>
        <input type="text" value="Main Hostel Canteen Dumpster #2" />
        <label>Urgency Level:</label>
        <select><option>Critical (Overflowing)</option><option>High (>90%)</option></select>
      `;
      break;

    default:
      body.innerHTML = `<p>Action triggered: ${actionType}</p>`;
      submitBtn.style.display = 'none';
  }
}

function closeModal() {
  document.getElementById('modalOverlay').style.display = 'none';
}

function submitModal() {
  const title = document.getElementById('modalTitle').innerText;
  
  if (title === 'Report Food Waste') {
    const amt = parseFloat(document.getElementById('swAmount').value) || 0;
    if (amt > 0) {
      wasteData.total += amt;
      wasteData.composted += Math.round(amt * 0.7);
      wasteData.recycled += Math.round(amt * 0.3);
      updateMetrics();
      alert(`Logged ${amt} kg food waste successfully!`);
    }
  } else {
    alert(`${title} dispatch request sent successfully!`);
  }
  
  closeModal();
}

function checkSegregation() {
  const item = document.getElementById('segItem').value.toLowerCase();
  const fb = document.getElementById('segFeedback');
  
  if (!item) return;

  if (['rice', 'vegetable', 'fruit', 'bread', 'peel'].some(w => item.includes(w))) {
    fb.style.background = '#d4edda';
    fb.style.color = '#155724';
    fb.innerText = '✅ Compostable Stream: Load into Rapid Bio-Drum.';
  } else if (['milk', 'oil', 'dairy', 'fat', 'meat'].some(w => item.includes(w))) {
    fb.style.background = '#fff3cd';
    fb.style.color = '#856404';
    fb.innerText = '⚡ Biogas Stream: Send to Anaerobic Digestion.';
  } else if (['plastic', 'paper', 'can', 'glass', 'box'].some(w => item.includes(w))) {
    fb.style.background = '#cce5ff';
    fb.style.color = '#004085';
    fb.innerText = '♻️ Recyclable Stream: Secondary Material Sorting.';
  } else {
    fb.style.background = '#f8d7da';
    fb.style.color = '#721c24';
    fb.innerText = '⚠️ Special/Reject Stream: Route to Incineration or Controlled Disposal.';
  }
}

function switchNav(target) {
  if (target === 'Leaderboard') {
    openModal('Leaderboard Details');
  }
}
