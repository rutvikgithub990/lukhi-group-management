
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" />
<title>Lukhi Group of Industries - Management</title>
<style>
  /* Color Palette */
  :root {
    --primary-color: #4E73DF;        /* Indigo Blue */
    --secondary-color: #36B9CC;      /* Cyan Blue */
    --accent-color: #F6C23E;         /* Yellow/Gold */
    --light-bg: #F8F9FC;             /* Light Gray Background */
    --text-color: #343A40;           /* Dark Text */
    --card-color: #FFFFFF;           /* White Cards */
    --danger-color: #E74A3B;         /* Red */
    --success-color: #1CC88A;        /* Green */
    --font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  /* Global styles and resets */
  body,html {
    margin: 0; padding: 0; height: 100%; background: var(--light-bg);
    font-family: var(--font-family);
    color: var(--text-color);
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    overflow-x: hidden;
  }

  a, button {
    font-family: var(--font-family);
  }

  /* Login Container */
  #login {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background: var(--primary-color);
    color: white;
    padding: 20px;
  }
  #login h2 {
    margin-bottom: 15px;
    font-weight: 700;
    font-size: 2rem;
  }
  #login input {
    width: 280px;
    padding: 10px 12px;
    margin-bottom: 15px;
    border-radius: 6px;
    border: none;
    outline: none;
    font-size: 1rem;
  }
  #login button {
    width: 280px;
    background: var(--accent-color);
    border: none;
    padding: 12px;
    font-size: 1.1rem;
    font-weight: 700;
    border-radius: 6px;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  #login button:hover {
    background: #d4a90f;
  }
  #login-error {
    color: var(--danger-color);
    font-weight: 600;
    height: 20px;
    margin-top: 5px;
  }

  /* Container for logged in state */
  #app {
    display: flex;
    height: 100vh;
    overflow: hidden;
  }

  /* Sidebar Navigation */
  nav {
    background: var(--primary-color);
    color: white;
    width: 280px;
    display: flex;
    flex-direction: column;
    padding-top: 1rem;
    position: sticky;
    top: 0;
    height: 100vh;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
    user-select: none;
    z-index: 100;
  }
  nav h1 {
    font-size: 1.8rem;
    margin: 0 0 1rem 1rem;
    font-weight: 700;
  }
  nav ul {
    list-style: none;
    padding-left: 0;
    margin: 0;
    flex-grow: 1;
  }
  nav ul li {
    padding: 15px 30px;
    cursor: pointer;
    font-weight: 600;
    border-left: 5px solid transparent;
    transition: background-color 0.3s ease, border-left-color 0.3s ease;
  }
  nav ul li:hover, nav ul li.active {
    background: var(--secondary-color);
    border-left-color: var(--accent-color);
  }
  nav .logout-btn {
    padding: 15px 30px;
    cursor: pointer;
    font-weight: 600;
    background: var(--danger-color);
    border: none;
    color: white;
    width: 100%;
    text-align: left;
    border-radius: 0 10px 10px 0;
    margin-top: auto;
    transition: background-color 0.3s ease;
  }
  nav .logout-btn:hover {
    background: #bf3a2f;
  }

  /* Main Content */
  main {
    flex-grow: 1;
    overflow-y: auto;
    padding: 20px 30px;
    background: var(--light-bg);
  }

  main h2 {
    margin-top: 0;
    font-weight: 700;
    color: var(--primary-color);
    margin-bottom: 15px;
  }

  /* Cards layout for dashboard */
  .metrics {
    display: grid;
    grid-template-columns: repeat(auto-fit,minmax(220px,1fr));
    gap: 20px;
    margin-bottom: 30px;
  }

  .card {
    background: var(--card-color);
    border-radius: 12px;
    padding: 20px;
    box-shadow: 0 3px 8px rgba(0,0,0,0.07);
    font-weight: 700;
    font-size: 1.2rem;
    color: var(--text-color);
    display: flex;
    justify-content: space-between;
    align-items: center;
    user-select: none;
  }
  .card span {
    font-size: 1.8rem;
    color: var(--accent-color);
  }

  /* Tabs content */
  .tab {
    display: none;
    animation: fadeIn 0.3s ease forwards;
  }
  .tab.active {
    display: block;
  }
  @keyframes fadeIn {
    from {opacity: 0;}
    to {opacity: 1;}
  }

  /* Table Styles */
  table {
    width: 100%;
    border-collapse: collapse;
    background: var(--card-color);
    border-radius: 12px;
    box-shadow: 0 3px 8px rgba(0,0,0,0.07);
    overflow: hidden;
    margin-bottom: 20px;
  }

  thead tr {
    background: var(--primary-color);
    color: white;
    font-weight: 700;
  }

  th, td {
    padding: 12px 15px;
    text-align: left;
    border-bottom: 1px solid #eaeaea;
    vertical-align: middle;
  }

  tbody tr:hover {
    background: #f1f9ff;
  }

  /* Responsive scroll container for tables on small screens */
  .table-wrapper {
    overflow-x: auto;
  }

  /* Buttons */
  button, input[type="button"], input[type="submit"] {
    cursor: pointer;
    background: var(--primary-color);
    color: white;
    border: none;
    padding: 8px 14px;
    border-radius: 6px;
    font-weight: 600;
    transition: background-color 0.3s ease;
    user-select: none;
  }
  button:hover, input[type="button"]:hover, input[type="submit"]:hover {
    background: var(--secondary-color);
  }
  .btn-danger {
    background: var(--danger-color) !important;
  }
  .btn-danger:hover {
    background: #bf3a2f !important;
  }
  .btn-success {
    background: var(--success-color) !important;
  }
  .btn-success:hover {
    background: #14b27d !important;
  }

  /* Inputs */
  input[type="text"], input[type="number"], input[type="email"], input[type="date"], select {
    padding: 8px;
    border-radius: 6px;
    border: 1px solid #ccc;
    width: 100%;
    box-sizing: border-box;
    outline: none;
    transition: border-color 0.3s ease;
  }
  input[type="text"]:focus, input[type="number"]:focus, input[type="email"]:focus, input[type="date"]:focus, select:focus {
    border-color: var(--primary-color);
  }

  /* Modal */
  .overlay {
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: rgba(0,0,0,0.6);
    display: none;
    align-items: center;
    justify-content: center;
    z-index: 1000;
  }
  .overlay.show {
    display: flex;
  }
  .modal {
    background: var(--card-color);
    padding: 20px 25px;
    border-radius: 12px;
    max-width: 500px;
    width: 90%;
    max-height: 90vh;
    overflow-y: auto;
    box-shadow: 0 10px 25px rgba(0,0,0,0.15);
    position: relative;
  }
  .modal h3 {
    margin-top: 0;
    color: var(--primary-color);
  }
  .modal label {
    display: block;
    margin: 15px 0 5px;
    font-weight: 600;
  }
  .modal input, .modal select {
    margin-bottom: 8px;
  }
  .modal .modal-actions {
    margin-top: 20px;
    text-align: right;
  }
  .modal .close-btn {
    position: absolute;
    top: 12px; right: 16px;
    background: transparent;
    border: none;
    font-size: 1.6rem;
    font-weight: 700;
    color: var(--danger-color);
    cursor: pointer;
  }
  .modal .close-btn:hover {
    color: #bf3a2f;
  }

  /* Profile Image preview */
  .profile-img-preview {
    width: 100px;
    height: 100px;
    border-radius: 12px;
    object-fit: cover;
    display: block;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    user-select: none;
  }

  /* Search input */
  #searchEmployee {
    width: 100%;
    padding: 10px 12px;
    margin-bottom: 12px;
    border-radius: 8px;
    border: 1px solid #ccc;
    font-size: 1rem;
    outline: none;
  }

  /* Responsive */
  @media (max-width: 900px) {
    #app {
      flex-direction: column;
      height: auto;
    }
    nav {
      height: auto;
      width: 100%;
      position: relative;
      box-shadow: none;
      flex-direction: row;
      overflow-x: auto;
    }
    nav ul {
      display: flex;
      flex-direction: row;
      padding: 0;
      margin: 0;
      flex-grow: 1;
    }
    nav ul li {
      border-left: none;
      border-bottom: 3px solid transparent;
      flex: 1 0 auto;
      text-align: center;
      padding: 10px 5px;
      font-size: 0.9rem;
    }
    nav ul li:hover, nav ul li.active {
      border-bottom-color: var(--accent-color);
      background: var(--primary-color);
      border-left: none;
    }
    nav .logout-btn {
      border-radius: 0;
      margin-top: 0;
      text-align: center;
      width: 100px;
      flex-shrink: 0;
    }
  }
  @media (max-width: 600px) {
    .card {
      font-size: 1rem;
    }
    button, input[type="button"], input[type="submit"] {
      font-size: 0.9rem;
      padding: 6px 12px;
    }
    #searchEmployee {
      font-size: 0.9rem;
      padding: 8px 10px;
    }
  }
</style>
</head>
<body>
<div id="login">
  <h2>Login - Lukhi Group of Industries</h2>
  <input type="text" id="username" placeholder="Username" autocomplete="off" />
  <input type="password" id="password" placeholder="Password" autocomplete="off" />
  <button onclick="attemptLogin()">Login</button>
  <p id="login-error"></p>
</div>

<div id="app" style="display:none">
  <nav aria-label="Main navigation">
    <h1>Lukhi Group</h1>
    <ul id="navList" role="tablist">
      <li role="tab" tabindex="0" aria-selected="true" class="active" data-tab="dashboardTab" onclick="switchTab(event)">🏠 Dashboard</li>
      <li role="tab" tabindex="-1" aria-selected="false" data-tab="employeeTab" onclick="switchTab(event)">👤 Employee Management</li>
      <li role="tab" tabindex="-1" aria-selected="false" data-tab="salaryTab" onclick="switchTab(event)">💼 Salary Management</li>
      <li role="tab" tabindex="-1" aria-selected="false" data-tab="transactionTab" onclick="switchTab(event)">💳 Cash & Bank Transactions</li>
      <li role="tab" tabindex="-1" aria-selected="false" data-tab="plTab" onclick="switchTab(event)">📊 P&amp;L Reports</li>
    </ul>
    <button class="logout-btn" onclick="logout()">Logout</button>
  </nav>

  <main>
    <!-- Dashboard Tab -->
    <section id="dashboardTab" class="tab active" role="tabpanel" aria-label="Dashboard tab content">
      <h2>Dashboard</h2>
      <div class="metrics" aria-live="polite" aria-atomic="true">
        <div class="card" id="cardTotalSalary" title="Total salary paid this month">Total Salary Paid: ₹<span id="totalSalary">0</span></div>
        <div class="card" id="cardPendingAdvances" title="Pending advances">Pending Advances: ₹<span id="pendingAdvances">0</span></div>
        <div class="card" id="cardTotalEmployees" title="Total number of employees">Total Employees: <span id="totalEmployees">0</span></div>
        <div class="card" id="cardIncomeExpenses" title="Total income minus expenses">Total Income vs Expenses: ₹<span id="incomeVsExpenses">0</span></div>
      </div>
      <canvas id="dashboardChart" aria-label="Income vs Expenses over months" role="img" height="250"></canvas>
    </section>

    <!-- Employee Management Tab -->
    <section id="employeeTab" class="tab" role="tabpanel" aria-label="Employee management tab content" hidden>
      <h2>Employee Management</h2>
      <input type="text" id="searchEmployee" placeholder="Search Employee by Name, Role or Village" oninput="searchEmployees()" aria-label="Search employees" autocomplete="off" />
      <div class="table-wrapper" role="region" aria-live="polite" aria-atomic="true" aria-label="Employee list">
        <table id="employeeTable" tabindex="0" aria-describedby="empCountDesc" aria-label="Employee List Table">
          <thead>
            <tr>
              <th scope="col">Profile</th>
              <th scope="col">Full Name</th>
              <th scope="col">Short Name</th>
              <th scope="col">Role</th>
              <th scope="col">Contact 1</th>
              <th scope="col">Contact 2</th>
              <th scope="col">Email</th>
              <th scope="col">Village</th>
              <th scope="col">Address</th>
              <th scope="col">Actions</th>
            </tr>
          </thead>
          <tbody id="employeeList"></tbody>
        </table>
      </div>
      <button onclick="showEmployeeModal()">Add New Employee</button>
      <p id="empCountDesc">Total employees displayed: <span id="employeeCount">0</span></p>
    </section>

    <!-- Salary Management Tab -->
    <section id="salaryTab" class="tab" role="tabpanel" aria-label="Salary management tab content" hidden>
      <h2>Salary Management</h2>
      <div class="table-wrapper" role="region" aria-live="polite" aria-atomic="true" aria-label="Salary list">
        <table id="salaryTable" tabindex="0" aria-describedby="salaryCountDesc" aria-label="Salary List Table">
          <thead>
            <tr>
              <th scope="col">Number</th>
              <th scope="col">Name</th>
              <th scope="col">Role</th>
              <th scope="col">Type</th>
              <th scope="col">Meter/Present</th>
              <th scope="col">Rate</th>
              <th scope="col">Salary (₹)</th>
              <th scope="col">Advance (₹)</th>
              <th scope="col">Total Salary (₹)</th>
              <th scope="col">Given (₹)</th>
              <th scope="col">Pending Advance (₹)</th>
              <th scope="col">Actions</th>
            </tr>
          </thead>
          <tbody id="salaryList"></tbody>
          <tfoot>
            <tr>
              <th colspan="6" style="text-align:right;">Totals:</th>
              <th id="totalSalarySum">0</th>
              <th id="totalAdvanceSum">0</th>
              <th id="totalTotalSalarySum">0</th>
              <th id="totalGivenSum">0</th>
              <th id="totalPendingAdvanceSum">0</th>
              <th></th>
            </tr>
          </tfoot>
        </table>
      </div>
      <button onclick="showSalaryModal()">Add Salary Row</button>
      <button onclick="downloadSalaryPDF()" style="margin-left:10px;">Download Salary Sheet (PDF)</button>
    </section>

    <!-- Cash & Bank Transactions Tab -->
    <section id="transactionTab" class="tab" role="tabpanel" aria-label="Cash and bank transactions tab content" hidden>
      <h2>Cash & Bank Transactions</h2>
      <div class="table-wrapper" role="region" aria-live="polite" aria-atomic="true" aria-label="Transaction list">
        <table id="transactionTable" tabindex="0" aria-describedby="transactionCountDesc" aria-label="Transaction List Table">
          <thead>
            <tr>
              <th scope="col">Date</th>
              <th scope="col">Description</th>
              <th scope="col">Type</th>
              <th scope="col">Amount (₹)</th>
              <th scope="col">Actions</th>
            </tr>
          </thead>
          <tbody id="transactionList"></tbody>
        </table>
      </div>
      <button onclick="showTransactionModal()">Add Transaction</button>
      <p><strong>Current Cash/Bank Balance: ₹<span id="currentBalance">0</span></strong></p>
      <canvas id="transactionChart" aria-label="Monthly cash flow chart" role="img" height="250"></canvas>
    </section>

    <!-- Profit & Loss Reports Tab -->
    <section id="plTab" class="tab" role="tabpanel" aria-label="Profit and loss reports tab content" hidden>
      <h2>Profit & Loss Reports</h2>
      <div>
        <label for="plViewSelect">Select Account:</label>
        <select id="plViewSelect" onchange="renderPLView()">
          <option value="blade">Blade Business</option>
          <option value="textile">Shree Mahalaxmi Textile</option>
          <option value="personal">Personal Account</option>
        </select>
      </div>
      <div class="table-wrapper" role="region" aria-live="polite" aria-atomic="true" aria-label="Profit and Loss Report">
        <table id="plTable" aria-label="P&L Report Table">
          <thead>
            <tr>
              <th>Date</th>
              <th>Description</th>
              <th>Income (₹)</th>
              <th>Expense (₹)</th>
            </tr>
          </thead>
          <tbody id="plList"></tbody>
          <tfoot>
            <tr>
              <th colspan="2" style="text-align:right">Totals:</th>
              <th id="plTotalIncome">0</th>
              <th id="plTotalExpense">0</th>
            </tr>
            <tr>
              <th colspan="2" style="text-align:right">Net Profit:</th>
              <th colspan="2" id="plNetProfit">0</th>
            </tr>
          </tfoot>
        </table>
      </div>
      <canvas id="plChart" aria-label="P&L Line and Bar Charts" role="img" height="300"></canvas>
    </section>
  </main>
</div>

<!-- Modal Template -->
<div id="modalOverlay" class="overlay" role="dialog" aria-modal="true" aria-hidden="true">
  <div class="modal" role="document" aria-labelledby="modalTitle">
    <button class="close-btn" aria-label="Close modal" onclick="closeModal()">&times;</button>
    <h3 id="modalTitle"></h3>
    <div id="modalContent"></div>
  </div>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdn.jsdelivr.net/npm/jspdf"></script>
<script src="https://cdn.jsdelivr.net/npm/jspdf-autotable"></script>
<script>
  /* 
    Lukhi Group of Industries Management
    Author: ChatGPT
    Date: 2024
    Features:
    - Secure login
    - Dashboard with animated metrics & charts
    - Employee management with image upload & localStorage
    - Salary management with types, live calc & PDF export
    - Cash & Bank transactions with balances & chart
    - P&L reports for 3 accounts with charts
    - Responsive & accessible UI
  */

  // Credentials (hardcoded for client-side login)
  const USERNAME = "SMT@98258";
  const PASSWORD = "99045750388980344430";

  // Store references to DOM elements
  const loginDiv = document.getElementById('login');
  const appDiv = document.getElementById('app');
  const navList = document.getElementById('navList');
  const tabs = document.querySelectorAll('.tab');
  const loginError = document.getElementById('login-error');

  // =============================
  // LOGIN FUNCTIONALITY
  // =============================
  function attemptLogin() {
    const userInput = document.getElementById('username').value.trim();
    const passInput = document.getElementById('password').value.trim();

    if (userInput === USERNAME && passInput === PASSWORD) {
      loginError.textContent = "";
      loginDiv.style.display = "none";
      appDiv.style.display = "flex";
      initializeApp();
    } else {
      loginError.textContent = "Invalid username or password.";
    }
  }
  function logout() {
    if(confirm('Are you sure you want to logout?')) {
      // Clear all data, safer for demo; normally persist data.
      appDiv.style.display = 'none';
      loginDiv.style.display = 'flex';
      document.getElementById('username').value = '';
      document.getElementById('password').value = '';
      loginError.textContent = '';
      // Clear data in UI (optional)
      resetUI();
    }
  }

  function resetUI() {
    // Clear UI states or form inputs if needed
  }

  // =============================
  // NAVIGATION & TAB CONTROL
  // =============================
  function switchTab(event) {
    const selectedTabId = event.target.getAttribute('data-tab');
    if(!selectedTabId) return;

    // Update nav active state
    navList.querySelectorAll('li').forEach(li => {
      li.classList.toggle('active', li.getAttribute('data-tab') === selectedTabId);
      li.setAttribute('aria-selected', li.getAttribute('data-tab') === selectedTabId ? 'true' : 'false');
      li.tabIndex = li.getAttribute('data-tab') === selectedTabId ? 0 : -1;
    });

    // Show/hide tabs
    tabs.forEach(tab => {
      if(tab.id === selectedTabId) {
        tab.classList.add('active');
        tab.removeAttribute('hidden');
      } else {
        tab.classList.remove('active');
        tab.setAttribute('hidden', '');
      }
    });

    // Refresh charts or content on tab switch
    if(selectedTabId === 'dashboardTab') {
      renderDashboardCharts();
    } else if(selectedTabId === 'transactionTab') {
      renderTransactionChart();
    } else if(selectedTabId === 'plTab') {
      renderPLView();
    }

  }

  // =============================
  // DATA STORAGE SETUP
  // =============================
  // Use localStorage keys prefix
  const LS_PREFIX = 'lukhiGroup_';

  // Data keys
  const LS_EMPLOYEES = LS_PREFIX + 'employees';
  const LS_SALARIES = LS_PREFIX + 'salaries';
  const LS_TRANSACTIONS = LS_PREFIX + 'transactions';

  // In-memory cache for efficiency
  let employees = [];
  let salaries = [];
  let transactions = [];

  // =============================
  // INITIALIZE APP AFTER LOGIN
  // =============================
  function initializeApp() {
    // Load data from localStorage
    employees = loadData(LS_EMPLOYEES) || [];
    salaries = loadData(LS_SALARIES) || [];
    transactions = loadData(LS_TRANSACTIONS) || [];

    // Initial renderings
    renderEmployees();
    renderSalaries();
    renderTransactions();
    renderDashboard();
    renderDashboardCharts();
    renderTransactionChart();
    renderPLView();

    // ARIA live updates for employee count
    document.getElementById('employeeCount').textContent = employees.length;
  }

  function loadData(key) {
    try {
      const data = localStorage.getItem(key);
      return data ? JSON.parse(data) : null;
    } catch {
      return null;
    }
  }

  function saveData(key, data) {
    localStorage.setItem(key, JSON.stringify(data));
  }

  // =============================
  // DASHBOARD
  // =============================
  // Animated counters for dashboard cards
  function animateCount(elementId, targetValue, duration=1500) {
    const element = document.getElementById(elementId);
    if(!element) return;
    let start = 0;
    const stepTime = Math.abs(Math.floor(duration / targetValue));
    if(stepTime < 10) {
      // If targetValue too big, cap stepTime for smooth animation
      stepTime = 10;
    }
    function step() {
      start++;
      element.textContent = start.toLocaleString('en-IN');
      if (start < targetValue) {
        setTimeout(step, stepTime);
      }
    }
    step();
  }

  function renderDashboard() {
    // Compute dashboard metrics from data
    const totalSalaryPaid = salaries.reduce((sum,sal) => sum + Number(sal.given || 0), 0);
    const totalPendingAdvance = salaries.reduce((sum,sal) => sum + Number(sal.pendingAdvance || 0), 0);
    const totalEmployeesCount = employees.length;
    const totalIncome = transactions.filter(t => t.type === 'Income').reduce((sum,t) => sum + Number(t.amount),0);
    const totalExpense = transactions.filter(t => t.type === 'Expense').reduce((sum,t) => sum + Number(t.amount),0);
    const incomeVsExpenses = totalIncome - totalExpense;

    // Animate numbers on dashboard
    animateCount('totalSalary', Math.round(totalSalaryPaid));
    animateCount('pendingAdvances', Math.round(totalPendingAdvance));
    animateCount('totalEmployees', totalEmployeesCount);
    animateCount('incomeVsExpenses', Math.round(incomeVsExpenses));
  }

  let dashboardChart = null;
  function renderDashboardCharts() {
    // Monthly income vs expense data for last 6 months
    // Prepare month labels and sums
    const ctx = document.getElementById('dashboardChart').getContext('2d');
    // Generate last 6 months labels
    const monthsLabels = [];
    const incomesByMonth = [];
    const expensesByMonth = [];
    const now = new Date();
    for(let i=5; i>=0; i--){
      let d = new Date(now.getFullYear(), now.getMonth()-i, 1);
      monthsLabels.push(d.toLocaleString('default', {month: 'short', year: '2-digit'}));
      incomesByMonth.push(
        transactions.filter(t => {
          const td = new Date(t.date);
          return t.type==='Income' && td.getMonth()===d.getMonth() && td.getFullYear()===d.getFullYear();
        }).reduce((sum,t)=> sum+ Number(t.amount),0)
      );
      expensesByMonth.push(
        transactions.filter(t => {
          const td = new Date(t.date);
          return t.type==='Expense' && td.getMonth()===d.getMonth() && td.getFullYear()===d.getFullYear();
        }).reduce((sum,t)=> sum+ Number(t.amount),0)
      );
    }

    if(dashboardChart) {
      dashboardChart.data.labels = monthsLabels;
      dashboardChart.data.datasets[0].data = incomesByMonth;
      dashboardChart.data.datasets[1].data = expensesByMonth;
      dashboardChart.update();
      return;
    }

    dashboardChart = new Chart(ctx, {
      type: 'bar',
      data: {
        labels: monthsLabels,
        datasets: [
          {
            label: 'Income',
            backgroundColor: 'rgba(28, 200, 138,0.7)',
            borderColor: 'rgba(28, 200, 138,1)',
            borderWidth: 1,
            data: incomesByMonth,
          },
          {
            label: 'Expenses',
            backgroundColor: 'rgba(231, 74, 59, 0.7)',
            borderColor: 'rgba(231, 74, 59,1)',
            borderWidth: 1,
            data: expensesByMonth,
          }
        ]
      },
      options: {
        responsive:true,
        plugins: {
          legend: {
            labels: {
              color: 'var(--text-color)'
            }
          }
        },
        scales: {
          y: {
            beginAtZero:true,
            ticks: {
              color: 'var(--text-color)'
            }
          },
          x: {
            ticks: {
              color: 'var(--text-color)'
            }
          }
        }
      }
    });
  }

  // =============================
  // EMPLOYEE MANAGEMENT
  // =============================
  const employeeListEl = document.getElementById('employeeList');
  const employeeCountEl = document.getElementById('employeeCount');

  // Render Employee Table Rows
  function renderEmployees(filterText='') {
    employeeListEl.innerHTML = '';
    let filteredEmployees = employees;

    if(filterText.trim()) {
      const search = filterText.toLowerCase();
      filteredEmployees = employees.filter(emp =>
        emp.fullName.toLowerCase().includes(search) ||
        (emp.role && emp.role.toLowerCase().includes(search)) ||
        (emp.village && emp.village.toLowerCase().includes(search))
      );
    }

    filteredEmployees.forEach((emp, index) =>{
      const tr = document.createElement('tr');
      tr.innerHTML = `
        <td><img src="${emp.photo || 'https://via.placeholder.com/60?text=N'}" alt="Profile photo of ${emp.fullName}" class="profile-img-preview"></td>
        <td>${emp.fullName}</td>
        <td>${emp.shortName || ''}</td>
        <td>${emp.role || ''}</td>
        <td>${emp.contact1 || ''}</td>
        <td>${emp.contact2 || ''}</td>
        <td>${emp.email || ''}</td>
        <td>${emp.village || ''}</td>
        <td>${emp.address || ''}</td>
        <td>
          <button onclick="showEmployeeModal(${index})" aria-label="Edit employee ${emp.fullName}">Edit</button>
          <button class="btn-danger" onclick="deleteEmployee(${index})" aria-label="Delete employee ${emp.fullName}">Delete</button>
        </td>
      `;
      employeeListEl.appendChild(tr);
    });

    employeeCountEl.textContent = filteredEmployees.length;
  }

  // Search employees
  function searchEmployees() {
    const query = document.getElementById('searchEmployee').value;
    renderEmployees(query);
  }

  // Delete employee
  function deleteEmployee(index) {
    if(confirm(`Are you sure to delete employee "${employees[index].fullName}"? This action cannot be undone.`)) {
      employees.splice(index,1);
      saveData(LS_EMPLOYEES, employees);
      renderEmployees();
      renderDashboard();
    }
  }

  // === EMPLOYEE MODAL ===
  const modalOverlay = document.getElementById('modalOverlay');
  const modalTitleEl = document.getElementById('modalTitle');
  const modalContentEl = document.getElementById('modalContent');
  let currentEditEmployeeIndex = null;

  function showEmployeeModal(index=null) {
    currentEditEmployeeIndex = index;
    modalTitleEl.textContent = index === null ? 'Add New Employee' : 'Edit Employee';

    // Populate form for editing or empty for adding
    let emp = {
      fullName:'', shortName:'', role:'', contact1:'', contact2:'', email:'', photo:'', village:'', address:''
    };
    if(index !== null && employees[index]){
      emp = employees[index];
    }
    modalContentEl.innerHTML = `
      <form id="employeeForm">
        <label for="empFullName">Full Name *</label>
        <input type="text" id="empFullName" name="fullName" required value="${emp.fullName.replaceAll('"','&quot;')}"/>
        
        <label for="empShortName">Short Name</label>
        <input type="text" id="empShortName" name="shortName" value="${emp.shortName.replaceAll('"','&quot;')}"/>

        <label for="empRole">Role</label>
        <input type="text" id="empRole" name="role" value="${emp.role.replaceAll('"','&quot;')}"/>

        <label for="empContact1">Contact 1</label>
        <input type="text" id="empContact1" name="contact1" value="${emp.contact1.replaceAll('"','&quot;')}"/>

        <label for="empContact2">Contact 2</label>
        <input type="text" id="empContact2" name="contact2" value="${emp.contact2.replaceAll('"','&quot;')}"/>

        <label for="empEmail">Email ID</label>
        <input type="email" id="empEmail" name="email" value="${emp.email.replaceAll('"','&quot;')}" />

        <label for="empPhoto">Profile Photo</label>
        <img src="${emp.photo || 'https://via.placeholder.com/100?text=No+Photo'}" alt="Profile preview" class="profile-img-preview" id="empPhotoPreview"/>
        <input type="file" id="empPhoto" name="photo" accept="image/*" />

        <label for="empVillage">Village Name</label>
        <input type="text" id="empVillage" name="village" value="${emp.village.replaceAll('"','&quot;')}"/>

        <label for="empAddress">Full Address</label>
        <input type="text" id="empAddress" name="address" value="${emp.address.replaceAll('"','&quot;')}" />

        <div class="modal-actions">
          <button type="submit">${index === null ? 'Add' : 'Save'}</button>
          <button type="button" onclick="closeModal()">Cancel</button>
        </div>
      </form>
    `;

    // Handle photo preview update
    const photoInput = document.getElementById('empPhoto');
    photoInput.addEventListener('change', (e) => {
      const preview = document.getElementById('empPhotoPreview');
      if(e.target.files && e.target.files[0]){
        const reader = new FileReader();
        reader.onload = function(event){
          preview.src = event.target.result;
        };
        reader.readAsDataURL(e.target.files[0]);
      }
    });

    // Handle form submit
    const form = document.getElementById('employeeForm');
    form.onsubmit = function(event) {
      event.preventDefault();
      let formData = new FormData(form);
      
      // Read photo base64 if changed
      const photoElem = document.getElementById('empPhoto');
      
      if(photoElem.files && photoElem.files[0]) {
        const reader = new FileReader();
        reader.onload = function(event){
          saveEmployeeData(formData, event.target.result);
        };
        reader.readAsDataURL(photoElem.files[0]);
      } else {
        saveEmployeeData(formData, currentEditEmployeeIndex !== null ? employees[currentEditEmployeeIndex].photo : '');
      }
    };

    openModal();
  }

  // Save or update employee data
  function saveEmployeeData(formData, photoBase64) {
    const empData = {
      fullName: formData.get('fullName').trim(),
      shortName: formData.get('shortName').trim(),
      role: formData.get('role').trim(),
      contact1: formData.get('contact1').trim(),
      contact2: formData.get('contact2').trim(),
      email: formData.get('email').trim(),
      photo: photoBase64,
      village: formData.get('village').trim(),
      address: formData.get('address').trim()
    };

    if(currentEditEmployeeIndex !== null) {
      employees[currentEditEmployeeIndex] = empData;
    } else {
      employees.push(empData);
    }
    saveData(LS_EMPLOYEES, employees);
    closeModal();
    renderEmployees();
    renderDashboard();
  }

  // =============================
  // SALARY MANAGEMENT
  // =============================
  const salaryListEl = document.getElementById('salaryList');

  // Render salaries table rows
  function renderSalaries() {
    salaryListEl.innerHTML = '';
    salaries.forEach((sal, index) => {
      const tr = document.createElement('tr');

      // Calculate salary if needed
      let calculatedSalary = 0;
      if(sal.type === 'fixed'){
        calculatedSalary = (Number(sal.presentDays) || 0) * (Number(sal.rate) || 0);
      } else if(sal.type === 'production'){
        calculatedSalary = (Number(sal.meters) || 0) * (Number(sal.rate) || 0);
      }

      // Advance and given could be 0 if missing
      let advance = Number(sal.advance) || 0;
      let given = Number(sal.given) || 0;
      let totalSalary = calculatedSalary + advance;
      let pendingAdvance = totalSalary - given;

      // Save updated calculated fields back to salaries array for consistency
      salaries[index].salary = calculatedSalary;
      salaries[index].totalSalary = totalSalary;
      salaries[index].pendingAdvance = pendingAdvance;

      tr.innerHTML = `
        <td>${index+1}</td>
        <td>${sal.name}</td>
        <td>${sal.role}</td>
        <td>${sal.type === 'fixed' ? 'Fixed' : 'Production'}</td>
        <td contenteditable oninput="onSalaryFieldEdit(${index}, this, '${sal.type === 'fixed' ? 'presentDays' : 'meters'}')">${sal.type === 'fixed' ? (sal.presentDays || 0) : (sal.meters || 0)}</td>
        <td contenteditable oninput="onSalaryFieldEdit(${index}, this, 'rate')">${sal.rate || 0}</td>
        <td>${calculatedSalary.toFixed(2)}</td>
        <td contenteditable oninput="onSalaryFieldEdit(${index}, this, 'advance')">${advance}</td>
        <td>${totalSalary.toFixed(2)}</td>
        <td contenteditable oninput="onSalaryFieldEdit(${index}, this, 'given')">${given}</td>
        <td>${pendingAdvance.toFixed(2)}</td>
        <td>
          <button class="btn-danger" onclick="deleteSalary(${index})" aria-label="Delete salary record for ${sal.name}">Delete</button>
        </td>
      `;
      salaryListEl.appendChild(tr);
    });
    updateSalaryTotals();
  }

  // Handle editing of salary table fields inline
  function onSalaryFieldEdit(index, element, field) {
    let value = element.textContent.trim();
    if(field === 'rate' || field === 'presentDays' || field === 'meters' || field === 'advance' || field === 'given'){
      // Sanitize numeric input
      let num = parseFloat(value);
      if(isNaN(num) || num < 0) num = 0;
      salaries[index][field] = num;
      element.textContent = num;
    }

    renderSalaries(); // re-render to update calculated fields and totals
    renderDashboard(); // update dashboard metrics
  }

  // Add new salary row - prefill with employee info if any employees exist
  function showSalaryModal() {
    if(employees.length === 0){
      alert('No employees found. Please add employees first.');
      return;
    }

    modalTitleEl.textContent = 'Add Salary Entry';
    modalContentEl.innerHTML = `
      <form id="salaryForm">
        <label for="salEmployee">Employee Name *</label>
        <select id="salEmployee" name="name" required>
          <option value="">Select Employee</option>
          ${employees.map((emp,i)=>`<option value="${emp.fullName}">${emp.fullName} (${emp.role || ''})</option>`).join('')}
        </select>
        <label for="salRole">Role</label>
        <input type="text" id="salRole" name="role" readonly />

        <label for="salType">Salary Type *</label>
        <select id="salType" name="type" required>
          <option value="fixed">Fixed Salary (₹/Day × Present Days)</option>
          <option value="production">Production Salary (Meters × ₹/Meter)</option>
        </select>

        <div id="fixedSalaryInputs" style="display:none">
          <label for="salPresentDays">Present Days</label>
          <input type="number" id="salPresentDays" name="presentDays" min="0" step="1" value="0" />
        </div>
        <div id="productionSalaryInputs" style="display:none">
          <label for="salMeters">Meters Produced</label>
          <input type="number" id="salMeters" name="meters" min="0" step="0.01" value="0" />
        </div>
        
        <label for="salRate">Rate (₹)</label>
        <input type="number" id="salRate" name="rate" min="0" step="0.01" value="0" required />

        <label for="salAdvance">Advance (₹)</label>
        <input type="number" id="salAdvance" name="advance" min="0" step="0.01" value="0" />

        <label for="salGiven">Given (₹)</label>
        <input type="number" id="salGiven" name="given" min="0" step="0.01" value="0" />
        
        <div class="modal-actions">
          <button type="submit">Add Salary</button>
          <button type="button" onclick="closeModal()">Cancel</button>
        </div>
      </form>
    `;
    const salEmployeeSelect = document.getElementById('salEmployee');
    const salRoleInput = document.getElementById('salRole');
    const salTypeSelect = document.getElementById('salType');
    const fixedInputsDiv = document.getElementById('fixedSalaryInputs');
    const productionInputsDiv = document.getElementById('productionSalaryInputs');

    // Populate role automatically when employee selected
    salEmployeeSelect.addEventListener('change', e => {
      const empName = e.target.value;
      const emp = employees.find(em=>em.fullName === empName);
      salRoleInput.value = emp ? emp.role || '' : '';
    });

    // Show/hide inputs based on salary type
    salTypeSelect.addEventListener('change', e =>{
      if(e.target.value === 'fixed'){
        fixedInputsDiv.style.display = 'block';
        productionInputsDiv.style.display = 'none';
      } else {
        fixedInputsDiv.style.display = 'none';
        productionInputsDiv.style.display = 'block';
      }
    });

    // Initialize visibility
    salTypeSelect.dispatchEvent(new Event('change'));

    // Form submit
    document.getElementById('salaryForm').onsubmit = function(e) {
      e.preventDefault();
      const form = e.target;
      const formData = new FormData(form);
      const newSal = {
        name: formData.get('name'),
        role: formData.get('role'),
        type: formData.get('type'),
        presentDays: formData.get('presentDays') || 0,
        meters: formData.get('meters') || 0,
        rate: Number(formData.get('rate')) || 0,
        advance: Number(formData.get('advance')) || 0,
        given: Number(formData.get('given')) || 0
      };
      salaries.push(newSal);
      saveData(LS_SALARIES, salaries);

      closeModal();
      renderSalaries();
      renderDashboard();
    };

    openModal();
  }

  // Delete salary row
  function deleteSalary(index){
    if(confirm(`Delete salary record for ${salaries[index].name}?`)) {
      salaries.splice(index,1);
      saveData(LS_SALARIES, salaries);
      renderSalaries();
      renderDashboard();
    }
  }

  // Update salary totals at footer
  function updateSalaryTotals(){
    let totalSalarySum = 0, totalAdvanceSum = 0, totalTotalSalarySum = 0, totalGivenSum = 0, totalPendingAdvanceSum = 0;
    for(let sal of salaries){
      totalSalarySum += sal.salary || 0;
      totalAdvanceSum += sal.advance || 0;
      totalTotalSalarySum += sal.totalSalary || 0;
      totalGivenSum += sal.given || 0;
      totalPendingAdvanceSum += sal.pendingAdvance || 0;
    }
    document.getElementById('totalSalarySum').textContent = totalSalarySum.toFixed(2);
    document.getElementById('totalAdvanceSum').textContent = totalAdvanceSum.toFixed(2);
    document.getElementById('totalTotalSalarySum').textContent = totalTotalSalarySum.toFixed(2);
    document.getElementById('totalGivenSum').textContent = totalGivenSum.toFixed(2);
    document.getElementById('totalPendingAdvanceSum').textContent = totalPendingAdvanceSum.toFixed(2);
  }

  // Download Salary Sheet PDF using jsPDF and autotable
  async function downloadSalaryPDF() {
    if(!salaries.length){
      alert('No salary data to export.');
      return;
    }
    // Dynamically import jsPDF if needed (already included via CDN)
    const { jsPDF } = window.jspdf;

    const doc = new jsPDF({
      orientation: 'landscape',
      unit: 'pt',
      format: 'a4'
    });
    doc.setFontSize(18);
    doc.setTextColor('#4E73DF');
    doc.text('Lukhi Group of Industries - Salary Sheet', 40, 40);

    const columns = [
      {header: 'Number', dataKey:'number'},
      {header: 'Name', dataKey: 'name'},
      {header: 'Role', dataKey: 'role'},
      {header: 'Type', dataKey: 'type'},
      {header: 'Meter/Present', dataKey: 'meterPresent'},
      {header: 'Rate ₹', dataKey: 'rate'},
      {header: 'Salary ₹', dataKey: 'salary'},
      {header: 'Advance ₹', dataKey: 'advance'},
      {header: 'Total Salary ₹', dataKey: 'totalSalary'},
      {header: 'Given ₹', dataKey: 'given'},
      {header: 'Pending Advance ₹', dataKey: 'pendingAdvance'}
    ];

    const rows = salaries.map((sal,i) => {
      return {
        number: i+1,
        name: sal.name,
        role: sal.role,
        type: sal.type === 'fixed' ? 'Fixed' : 'Production',
        meterPresent: sal.type === 'fixed' ? sal.presentDays : sal.meters,
        rate: sal.rate.toFixed(2),
        salary: (sal.salary || 0).toFixed(2),
        advance: (sal.advance || 0).toFixed(2),
        totalSalary: (sal.totalSalary || 0).toFixed(2),
        given: (sal.given || 0).toFixed(2),
        pendingAdvance: (sal.pendingAdvance || 0).toFixed(2)
      };
    });

    doc.autoTable({
      head: [columns.map(c=>c.header)],
      body: rows.map(row=>columns.map(c=>row[c.dataKey])),
      startY: 60,
      theme: 'striped',
      headStyles: {fillColor: '#4E73DF', textColor: 'white'},
      styles: {
        fontSize: 9,
        cellPadding: 3
      }
    });

    doc.save('lukhi_group_salary_sheet.pdf');
  }

  // =============================
  // TRANSACTIONS MANAGEMENT
  // =============================
  const transactionListEl = document.getElementById('transactionList');
  const currentBalanceEl = document.getElementById('currentBalance');
  let transactionChartObj = null;

  function renderTransactions() {
    transactionListEl.innerHTML = '';
    transactions.forEach((trn, index) => {
      const tr = document.createElement('tr');
      tr.innerHTML = `
        <td>${trn.date}</td>
        <td>${trn.description}</td>
        <td>${trn.type}</td>
        <td>${Number(trn.amount).toFixed(2)}</td>
        <td>
          <button class="btn-danger" aria-label="Delete transaction: ${trn.description}" onclick="deleteTransaction(${index})">Delete</button>
        </td>
      `;
      transactionListEl.appendChild(tr);
    });
    updateCurrentBalance();
  }

  function updateCurrentBalance(){
    const incomeSum = transactions.filter(t=>t.type==='Income').reduce((sum,t)=>sum+Number(t.amount),0);
    const expenseSum = transactions.filter(t=>t.type==='Expense').reduce((sum,t)=>sum+Number(t.amount),0);
    const balance = incomeSum - expenseSum;
    currentBalanceEl.textContent = balance.toFixed(2);
  }

  function showTransactionModal(){
    modalTitleEl.textContent = 'Add Cash/Bank Transaction';
    modalContentEl.innerHTML = `
      <form id="transactionForm">
        <label for="trnDate">Date *</label>
        <input type="date" id="trnDate" name="date" required value="${new Date().toISOString().split('T')[0]}"/>
        <label for="trnDescription">Description *</label>
        <input type="text" id="trnDescription" name="description" required />
        <label for="trnType">Type *</label>
        <select id="trnType" name="type" required>
          <option value="Income">Income</option>
          <option value="Expense">Expense</option>
        </select>
        <label for="trnAmount">Amount (₹) *</label>
        <input type="number" id="trnAmount" name="amount" required step="0.01" min="0" />
        <div class="modal-actions">
          <button type="submit">Add Transaction</button>
          <button type="button" onclick="closeModal()">Cancel</button>
        </div>
      </form>
    `;
    document.getElementById('transactionForm').onsubmit = function(e){
      e.preventDefault();
      const form = e.target;
      const formData = new FormData(form);
      transactions.push({
        date: formData.get('date'),
        description: formData.get('description').trim(),
        type: formData.get('type'),
        amount: Number(formData.get('amount'))
      });
      saveData(LS_TRANSACTIONS, transactions);
      closeModal();
      renderTransactions();
      renderDashboard();
      renderDashboardCharts();
      renderTransactionChart();
    };
    openModal();
  }

  function deleteTransaction(index){
    if(confirm(`Delete transaction "${transactions[index].description}"?`)){
      transactions.splice(index,1);
      saveData(LS_TRANSACTIONS, transactions);
      renderTransactions();
      renderDashboard();
      renderDashboardCharts();
      renderTransactionChart();
    }
  }

  // Transaction Chart
  function renderTransactionChart(){
    const ctx = document.getElementById('transactionChart').getContext('2d');

    // Aggregate monthly income & expense for last 6 months
    const monthsLabels = [];
    const incomesByMonth = [];
    const expensesByMonth = [];
    const now = new Date();
    for(let i=5; i>=0; i--){
      const d = new Date(now.getFullYear(), now.getMonth()-i, 1);
      monthsLabels.push(d.toLocaleString('default', {month: 'short', year: '2-digit'}));
      incomesByMonth.push(
        transactions.filter(t => {
          const td = new Date(t.date);
          return t.type==='Income' && td.getMonth()===d.getMonth() && td.getFullYear()===d.getFullYear();
        }).reduce((sum,t)=>sum+Number(t.amount),0)
      );
      expensesByMonth.push(
        transactions.filter(t => {
          const td = new Date(t.date);
          return t.type==='Expense' && td.getMonth()===d.getMonth() && td.getFullYear()===d.getFullYear();
        }).reduce((sum,t)=>sum+Number(t.amount),0)
      );
    }
    if(transactionChartObj){
      transactionChartObj.data.labels = monthsLabels;
      transactionChartObj.data.datasets[0].data = incomesByMonth;
      transactionChartObj.data.datasets[1].data = expensesByMonth;
      transactionChartObj.update();
      return;
    }

    transactionChartObj = new Chart(ctx, {
      type: 'line',
      data: {
        labels: monthsLabels,
        datasets: [
          {
            label: 'Income',
            data: incomesByMonth,
            borderColor: 'rgba(28, 200, 138,1)',
            backgroundColor: 'rgba(28, 200, 138,0.3)',
            fill: true,
            tension: 0.3,
          },
          {
            label: 'Expenses',
            data: expensesByMonth,
            borderColor: 'rgba(231, 74, 59,1)',
            backgroundColor: 'rgba(231, 74, 59,0.3)',
            fill: true,
            tension: 0.3,
          }
        ]
      },
      options: {
        responsive:true,
        plugins: {
          legend: {
            labels: {
              color: 'var(--text-color)'
            }
          }
        },
        scales: {
          y: {
            beginAtZero:true,
            ticks: {
              color: 'var(--text-color)'
            }
          },
          x: {
            ticks: {
              color: 'var(--text-color)'
            }
          }
        }
      }
    });
  }

  // =============================
  // PROFIT & LOSS REPORTS
  // =============================
  const plListEl = document.getElementById('plList');
  const plTotalIncomeEl = document.getElementById('plTotalIncome');
  const plTotalExpenseEl = document.getElementById('plTotalExpense');
  const plNetProfitEl = document.getElementById('plNetProfit');
  const plChartEl = document.getElementById('plChart');
  let plChartObj = null;

  // For demo, segregate transactions by description containing 'blade', 'textile', or else personal
  function getPlData(account) {
    const acc = account.toLowerCase();
    const filtered = transactions.filter(trn => {
      if(acc==='blade') return trn.description.toLowerCase().includes('blade');
      if(acc==='textile') return trn.description.toLowerCase().includes('textile');
      return !trn.description.toLowerCase().includes('blade') && !trn.description.toLowerCase().includes('textile');
    });

    return filtered;
  }
  // Render P&L Table and chart based on view
  function renderPLView() {
    const account = document.getElementById('plViewSelect').value;
    const filtered = getPlData(account);

    plListEl.innerHTML = '';
    let totalIncome = 0, totalExpense = 0;
    filtered.forEach(trn=>{
      const tr = document.createElement('tr');
      let income = 0, expense = 0;
      if(trn.type === 'Income') { income = Number(trn.amount); totalIncome += income; }
      else if(trn.type === 'Expense'){ expense = Number(trn.amount); totalExpense += expense; }
      tr.innerHTML = `
        <td>${trn.date}</td>
        <td>${trn.description}</td>
        <td>${income ? income.toFixed(2) : ''}</td>
        <td>${expense ? expense.toFixed(2) : ''}</td>
      `;
      plListEl.appendChild(tr);
    });
    plTotalIncomeEl.textContent = totalIncome.toFixed(2);
    plTotalExpenseEl.textContent = totalExpense.toFixed(2);
    plNetProfitEl.textContent = (totalIncome - totalExpense).toFixed(2);

    renderPLChart(account, filtered);
  }

  // P&L Chart rendering both line and bar for income/expenses over months
  function renderPLChart(account, transactionsForAccount) {
    const ctx = plChartEl.getContext('2d');
    // Prepare month labels and sums for last 6 months
    const monthsLabels = [];
    const incomesByMonth = [];
    const expensesByMonth = [];
    const now = new Date();
    for(let i=5; i>=0; i--){
      const d = new Date(now.getFullYear(), now.getMonth()-i, 1);
      monthsLabels.push(d.toLocaleString('default', {month: 'short', year: '2-digit'}));
      incomesByMonth.push(
        transactionsForAccount.filter(t => {
          const td = new Date(t.date);
          return t.type==='Income' && td.getMonth()===d.getMonth() && td.getFullYear()===d.getFullYear();
        }).reduce((sum,t)=>sum+Number(t.amount),0)
      );
      expensesByMonth.push(
        transactionsForAccount.filter(t => {
          const td = new Date(t.date);
          return t.type==='Expense' && td.getMonth()===d.getMonth() && td.getFullYear()===d.getFullYear();
        }).reduce((sum,t)=>sum+Number(t.amount),0)
      );
    }
    if(plChartObj){
      plChartObj.data.labels = monthsLabels;
      plChartObj.data.datasets[0].data = incomesByMonth;
      plChartObj.data.datasets[1].data = expensesByMonth;
      plChartObj.update();
      return;
    }

    plChartObj = new Chart(ctx, {
      data: {
        labels: monthsLabels,
        datasets:[
          {
            label: 'Income',
            type: 'line',
            data: incomesByMonth,
            borderColor: 'rgba(28, 200, 138,1)',
            backgroundColor: 'rgba(28, 200, 138,0.5)',
            fill: true,
            tension: 0.3
          },
          {
            label: 'Expenses',
            type: 'bar',
            data: expensesByMonth,
            backgroundColor: 'rgba(231, 74, 59,0.7)',
            borderColor: 'rgba(231, 74, 59,1)',
            borderWidth: 1
          }
        ]
      },
      options: {
        responsive:true,
        interaction: {
          mode: 'index',
          intersect: false
        },
        plugins: {
          legend: {
            labels: {color: 'var(--text-color)'}
          }
        },
        scales: {
          y: {
            beginAtZero:true,
            ticks: {color: 'var(--text-color)'}
          },
          x: {
            ticks: {color: 'var(--text-color)'}
          }
        }
      }
    });
  }

  // =============================
  // MODAL CONTROLS
  // =============================
  function openModal() {
    modalOverlay.classList.add('show');
    modalOverlay.setAttribute('aria-hidden', 'false');
    // Prevent background scroll
    document.body.style.overflow = 'hidden';
  }

  function closeModal() {
    modalOverlay.classList.remove('show');
    modalOverlay.setAttribute('aria-hidden', 'true');
    // Restore background scroll
    document.body.style.overflow = '';
  }

  // =============================
  // EMPLOYEE IMAGE PLACEHOLDER ALT FIX FUNC
  // =============================
  // Fix for default image alt fallback in employee render (done with alt attr)

  // =============================
  // INITIAL FOCUS ON LOGIN USERNAME
  // =============================
  document.getElementById('username').focus();

</script>
</body>
</html>

