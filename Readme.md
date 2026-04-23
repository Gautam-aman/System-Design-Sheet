<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>SysDesign.track — Interview Prep Dashboard</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Outfit:wght@400;500;600;700&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #040404;
    --bg2: #080808;
    --bg3: #0c0c0c;
    --surface: #101010;
    --surface2: #161616;
    --surface3: #1e1e1e;
    --green: #3ddc84;
    --green2: #2bbd6e;
    --green3: #1a7a48;
    --green-dim: rgba(61,220,132,0.07);
    --green-glow: 0 0 24px rgba(61,220,132,0.15);
    --amber: #f5a623;
    --amber-dim: rgba(245,166,35,0.08);
    --red: #f06565;
    --red-dim: rgba(240,101,101,0.08);
    --blue: #6eb5ff;
    --blue-dim: rgba(110,181,255,0.08);
    --text: #d4d4d4;
    --text2: #7a7a7a;
    --text3: #444444;
    --border: #181818;
    --border2: #242424;
    --sans: 'Inter', sans-serif;
    --display: 'Outfit', sans-serif;
    --radius: 8px;
    --radius-sm: 5px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    font-size: 13px;
    min-height: 100vh;
    overflow-x: hidden;
    -webkit-font-smoothing: antialiased;
  }

  /* Header */
  .header {
    border-bottom: 1px solid var(--border);
    padding: 14px 32px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: rgba(8,8,8,0.92);
    position: sticky;
    top: 0;
    z-index: 100;
    backdrop-filter: blur(16px);
  }

  .logo {
    display: flex;
    align-items: center;
    gap: 11px;
  }

  .logo-icon {
    width: 32px;
    height: 32px;
    background: var(--green-dim);
    border: 1px solid rgba(61,220,132,0.2);
    border-radius: var(--radius-sm);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 15px;
  }

  .logo-text {
    font-family: var(--display);
    font-size: 17px;
    font-weight: 600;
    color: #e8e8e8;
    letter-spacing: -0.3px;
  }

  .logo-text span { color: var(--green); }

  .logo-sub {
    font-size: 10px;
    color: var(--text3);
    letter-spacing: 1px;
    margin-top: 1px;
  }

  .header-stats {
    display: flex;
    gap: 10px;
    align-items: center;
  }

  .stat-pill {
    display: flex;
    align-items: center;
    gap: 7px;
    background: var(--surface);
    border: 1px solid var(--border2);
    border-radius: 20px;
    padding: 5px 13px;
    font-size: 11px;
    color: var(--text2);
    font-family: var(--sans);
    font-weight: 400;
    transition: border-color 0.2s;
  }

  .stat-pill:hover { border-color: var(--border2); }

  .stat-pill .dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  .dot-green { background: var(--green); }
  .dot-amber { background: var(--amber); }
  .dot-red { background: var(--red); }

  /* Progress Bar */
  .progress-banner {
    background: var(--bg2);
    border-bottom: 1px solid var(--border);
    padding: 10px 32px;
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .progress-label {
    font-size: 10px;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: var(--text3);
    white-space: nowrap;
    font-weight: 500;
  }

  .progress-bar-container {
    flex: 1;
    height: 3px;
    background: var(--surface3);
    border-radius: 2px;
    overflow: hidden;
  }

  .progress-bar-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--green3), var(--green));
    border-radius: 2px;
    transition: width 0.7s cubic-bezier(0.4,0,0.2,1);
  }

  .progress-pct {
    font-family: var(--display);
    font-weight: 600;
    color: var(--green);
    font-size: 13px;
    min-width: 36px;
    text-align: right;
  }

  /* Tabs */
  .tabs {
    display: flex;
    padding: 0 32px;
    border-bottom: 1px solid var(--border);
    background: var(--bg2);
    gap: 2px;
  }

  .tab {
    padding: 12px 18px;
    font-family: var(--sans);
    font-size: 12px;
    font-weight: 400;
    color: var(--text3);
    cursor: pointer;
    border-bottom: 1.5px solid transparent;
    transition: all 0.18s ease;
    letter-spacing: 0.2px;
    display: flex;
    align-items: center;
    gap: 6px;
    white-space: nowrap;
    user-select: none;
    margin-bottom: -1px;
  }

  .tab:hover { color: var(--text2); }

  .tab.active {
    color: var(--text);
    border-bottom-color: var(--green);
    font-weight: 500;
  }

  .tab-icon { font-size: 13px; opacity: 0.8; }

  /* Main */
  .main {
    padding: 24px 32px;
    max-width: 1600px;
    margin: 0 auto;
  }

  /* Panel header */
  .panel-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 16px;
    flex-wrap: wrap;
    gap: 10px;
  }

  .panel-title {
    font-family: var(--display);
    font-size: 16px;
    font-weight: 600;
    color: var(--text);
    letter-spacing: -0.2px;
  }

  .filter-bar {
    display: flex;
    gap: 6px;
    align-items: center;
    flex-wrap: wrap;
  }

  .filter-btn {
    padding: 5px 12px;
    border-radius: var(--radius-sm);
    border: 1px solid var(--border2);
    background: transparent;
    color: var(--text2);
    font-family: var(--sans);
    font-size: 11px;
    cursor: pointer;
    transition: all 0.15s;
    font-weight: 400;
  }

  .filter-btn:hover {
    border-color: var(--border2);
    color: var(--text);
    background: var(--surface2);
  }

  .filter-btn.active {
    border-color: rgba(61,220,132,0.3);
    color: var(--green);
    background: var(--green-dim);
  }

  .search-input {
    background: var(--surface);
    border: 1px solid var(--border2);
    border-radius: var(--radius-sm);
    color: var(--text);
    font-family: var(--sans);
    font-size: 12px;
    padding: 5px 12px;
    outline: none;
    width: 200px;
    transition: border-color 0.2s;
  }

  .search-input:focus { border-color: rgba(61,220,132,0.3); }
  .search-input::placeholder { color: var(--text3); }

  /* Table */
  .table-wrapper {
    border: 1px solid var(--border);
    border-radius: var(--radius);
    overflow: hidden;
    background: var(--surface);
  }

  table {
    width: 100%;
    border-collapse: collapse;
  }

  thead tr {
    background: var(--surface2);
    border-bottom: 1px solid var(--border);
  }

  th {
    padding: 10px 16px;
    text-align: left;
    font-size: 10px;
    letter-spacing: 0.8px;
    text-transform: uppercase;
    color: var(--text3);
    font-weight: 500;
    white-space: nowrap;
    font-family: var(--sans);
  }

  tbody tr {
    border-bottom: 1px solid var(--border);
    transition: background 0.12s;
  }

  tbody tr:last-child { border-bottom: none; }
  tbody tr:hover { background: var(--surface2); }

  td {
    padding: 12px 16px;
    vertical-align: middle;
  }

  /* Topic cell */
  .topic-name {
    font-weight: 500;
    font-size: 13px;
    color: var(--text);
    display: flex;
    align-items: center;
    gap: 8px;
    font-family: var(--sans);
  }

  .topic-category {
    font-size: 11px;
    color: var(--text3);
    margin-top: 2px;
    font-weight: 400;
  }

  /* Category badge */
  .badge {
    display: inline-flex;
    align-items: center;
    padding: 2px 8px;
    border-radius: 4px;
    font-size: 10px;
    letter-spacing: 0.3px;
    font-weight: 500;
    white-space: nowrap;
  }

  .badge-hld { background: rgba(110,181,255,0.08); color: var(--blue); border: 1px solid rgba(110,181,255,0.15); }
  .badge-lld { background: rgba(245,166,35,0.08); color: var(--amber); border: 1px solid rgba(245,166,35,0.15); }

  /* Importance */
  .importance {
    display: flex;
    align-items: center;
    gap: 7px;
  }

  .imp-bar {
    display: flex;
    gap: 2px;
  }

  .imp-seg {
    width: 6px;
    height: 12px;
    border-radius: 2px;
    background: var(--surface3);
  }

  .imp-seg.on-critical { background: var(--red); opacity: 0.85; }
  .imp-seg.on-high { background: var(--amber); opacity: 0.85; }
  .imp-seg.on-medium { background: var(--green2); opacity: 0.85; }

  .imp-label {
    font-size: 11px;
    color: var(--text3);
    min-width: 48px;
    font-weight: 400;
  }

  /* Status dropdown */
  .status-select {
    appearance: none;
    -webkit-appearance: none;
    border-radius: var(--radius-sm);
    padding: 5px 28px 5px 10px;
    font-family: var(--sans);
    font-size: 11px;
    font-weight: 400;
    cursor: pointer;
    outline: none;
    border: 1px solid var(--border2);
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6' viewBox='0 0 10 6'%3E%3Cpath d='M0 0l5 6 5-6z' fill='%23444'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 8px center;
    transition: all 0.15s;
    min-width: 130px;
  }

  .status-select.not-started {
    background-color: transparent;
    color: var(--text3);
    border-color: var(--border2);
  }

  .status-select.active {
    background-color: var(--amber-dim);
    color: var(--amber);
    border-color: rgba(245,166,35,0.2);
  }

  .status-select.completed {
    background-color: var(--green-dim);
    color: var(--green);
    border-color: rgba(61,220,132,0.2);
  }

  /* Companies */
  .companies {
    display: flex;
    flex-wrap: wrap;
    gap: 4px;
  }

  .company-tag {
    padding: 2px 7px;
    border-radius: 4px;
    font-size: 10px;
    border: 1px solid var(--border2);
    color: var(--text3);
    background: transparent;
    white-space: nowrap;
    font-weight: 400;
  }

  /* Links cell */
  .links-cell {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
    align-items: center;
  }

  .link-chip {
    display: inline-flex;
    align-items: center;
    gap: 4px;
    padding: 3px 9px;
    border-radius: 4px;
    font-size: 10px;
    background: var(--blue-dim);
    border: 1px solid rgba(110,181,255,0.12);
    color: var(--blue);
    text-decoration: none;
    transition: all 0.15s;
    cursor: pointer;
    white-space: nowrap;
    font-weight: 400;
  }

  .link-chip:hover { background: rgba(110,181,255,0.13); border-color: rgba(110,181,255,0.25); }

  .add-link-btn {
    display: inline-flex;
    align-items: center;
    gap: 4px;
    padding: 3px 9px;
    border-radius: 4px;
    font-size: 10px;
    background: transparent;
    border: 1px dashed var(--border2);
    color: var(--text3);
    cursor: pointer;
    transition: all 0.15s;
    font-family: var(--sans);
  }

  .add-link-btn:hover {
    border-color: rgba(61,220,132,0.3);
    color: var(--green);
  }

  /* Interview Q section */
  .questions-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(380px, 1fr));
    gap: 12px;
  }

  .question-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 18px;
    transition: border-color 0.2s, box-shadow 0.2s;
    cursor: default;
  }

  .question-card:hover {
    border-color: var(--border2);
    box-shadow: 0 4px 24px rgba(0,0,0,0.3);
  }

  .question-card-header {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    gap: 10px;
    margin-bottom: 12px;
  }

  .question-num {
    font-size: 10px;
    color: var(--text3);
    font-weight: 500;
    letter-spacing: 0.5px;
    white-space: nowrap;
    margin-top: 2px;
    font-family: var(--sans);
  }

  .question-text {
    font-size: 13px;
    font-weight: 400;
    color: var(--text);
    line-height: 1.6;
    flex: 1;
    font-family: var(--sans);
  }

  .question-freq {
    display: flex;
    gap: 3px;
    margin-top: 2px;
  }

  .freq-dot {
    width: 5px; height: 5px;
    border-radius: 50%;
    background: var(--surface3);
  }

  .freq-dot.on { background: var(--green); opacity: 0.9; }

  .question-meta {
    display: flex;
    gap: 5px;
    flex-wrap: wrap;
    margin-top: 10px;
  }

  .q-tag {
    padding: 2px 7px;
    border-radius: 4px;
    font-size: 10px;
    font-weight: 400;
  }

  .q-tag-topic { background: var(--green-dim); color: var(--green2); border: 1px solid rgba(61,220,132,0.15); }
  .q-tag-company { background: transparent; color: var(--text3); border: 1px solid var(--border2); }

  .toggle-answer {
    font-size: 11px;
    color: var(--text3);
    cursor: pointer;
    background: none;
    border: none;
    font-family: var(--sans);
    padding: 0;
    transition: color 0.15s;
    margin-top: 12px;
    display: block;
    font-weight: 400;
  }

  .toggle-answer:hover { color: var(--green); }

  .answer-box {
    margin-top: 10px;
    padding: 12px 14px;
    background: var(--bg3);
    border-radius: var(--radius-sm);
    border-left: 2px solid rgba(61,220,132,0.3);
    font-size: 12px;
    color: var(--text2);
    line-height: 1.75;
    display: none;
    font-family: var(--sans);
  }

  .answer-box.open { display: block; }

  /* Frequency tab */
  .freq-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 10px;
  }

  .freq-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 16px;
    transition: border-color 0.2s;
  }

  .freq-card:hover { border-color: var(--border2); }

  .freq-card-name {
    font-weight: 500;
    font-size: 13px;
    color: var(--text);
    margin-bottom: 3px;
    font-family: var(--sans);
  }

  .freq-card-type {
    font-size: 10px;
    color: var(--text3);
    margin-bottom: 14px;
    letter-spacing: 0.3px;
    font-weight: 400;
  }

  .freq-meter {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 10px;
  }

  .freq-meter-label {
    font-size: 10px;
    color: var(--text3);
    width: 66px;
    letter-spacing: 0.3px;
    flex-shrink: 0;
    font-weight: 400;
  }

  .freq-meter-bar {
    flex: 1;
    height: 3px;
    background: var(--surface3);
    border-radius: 2px;
    overflow: hidden;
  }

  .freq-meter-fill {
    height: 100%;
    border-radius: 2px;
    transition: width 0.6s ease;
  }

  .fill-critical { background: var(--red); opacity: 0.8; }
  .fill-high { background: var(--amber); opacity: 0.8; }
  .fill-medium { background: var(--green2); opacity: 0.8; }
  .fill-low { background: var(--surface3); }

  .freq-pct {
    font-size: 11px;
    font-weight: 500;
    min-width: 30px;
    text-align: right;
    color: var(--text2);
  }

  .freq-companies-label {
    font-size: 10px;
    color: var(--text3);
    letter-spacing: 0.3px;
    margin-bottom: 6px;
    font-weight: 400;
  }

  /* Modal */
  .modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.6);
    z-index: 999;
    display: none;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(4px);
  }

  .modal-overlay.open { display: flex; }

  .modal {
    background: var(--surface);
    border: 1px solid var(--border2);
    border-radius: 10px;
    padding: 24px;
    width: 440px;
    max-width: 95vw;
    box-shadow: 0 24px 64px rgba(0,0,0,0.5);
  }

  .modal-title {
    font-family: var(--display);
    font-size: 15px;
    font-weight: 600;
    color: var(--text);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .modal-label {
    font-size: 11px;
    color: var(--text2);
    letter-spacing: 0.3px;
    margin-bottom: 6px;
    font-weight: 400;
  }

  .modal-input {
    width: 100%;
    background: var(--bg3);
    border: 1px solid var(--border2);
    border-radius: var(--radius-sm);
    color: var(--text);
    font-family: var(--sans);
    font-size: 12px;
    padding: 9px 12px;
    outline: none;
    margin-bottom: 14px;
    transition: border-color 0.15s;
  }

  .modal-input:focus { border-color: rgba(61,220,132,0.3); }
  .modal-input::placeholder { color: var(--text3); }

  .modal-buttons {
    display: flex;
    gap: 8px;
    justify-content: flex-end;
    margin-top: 4px;
  }

  .btn {
    padding: 7px 18px;
    border-radius: var(--radius-sm);
    font-family: var(--sans);
    font-size: 12px;
    font-weight: 500;
    cursor: pointer;
    border: 1px solid transparent;
    transition: all 0.15s;
  }

  .btn-primary {
    background: var(--green-dim);
    color: var(--green);
    border-color: rgba(61,220,132,0.25);
  }

  .btn-primary:hover { background: rgba(61,220,132,0.12); }

  .btn-ghost {
    background: transparent;
    color: var(--text2);
    border-color: var(--border2);
  }

  .btn-ghost:hover { color: var(--text); background: var(--surface2); }

  /* Section dividers */
  .section-divider {
    display: flex;
    align-items: center;
    gap: 12px;
    margin: 22px 0 14px;
  }

  .section-divider-label {
    font-size: 10px;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: var(--text3);
    white-space: nowrap;
    font-weight: 500;
  }

  .section-divider-line {
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* Empty state */
  .empty {
    text-align: center;
    padding: 52px;
    color: var(--text3);
    font-size: 12px;
    font-weight: 400;
  }

  /* Scrollbar */
  ::-webkit-scrollbar { width: 5px; height: 5px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: var(--surface3); border-radius: 3px; }

  /* Tooltip */
  [data-tooltip] { position: relative; cursor: help; }
  [data-tooltip]::after {
    content: attr(data-tooltip);
    position: absolute;
    bottom: 125%;
    left: 50%;
    transform: translateX(-50%);
    background: var(--surface2);
    border: 1px solid var(--border2);
    color: var(--text);
    padding: 5px 10px;
    border-radius: 4px;
    font-size: 11px;
    white-space: nowrap;
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.15s;
    z-index: 10;
  }
  [data-tooltip]:hover::after { opacity: 1; }

  .tab-content { display: none; }
  .tab-content.active { display: block; }

  .section-header-sticky {
    position: sticky;
    top: 0;
    background: var(--surface2);
    z-index: 10;
  }

  .topic-icon {
    font-size: 15px;
    width: 26px;
    flex-shrink: 0;
    opacity: 0.85;
  }
</style>
</head>
<body>

<!-- Header -->
<header class="header">
  <div class="logo">
    <div class="logo-icon">⬡</div>
    <div>
      <div class="logo-text">SysDesign.track</div>
      <div class="logo-sub">Interview Prep Dashboard</div>
    </div>
  </div>
  <div class="header-stats" id="headerStats">
    <div class="stat-pill"><span class="dot dot-green"></span><span id="completedCount">0</span> Completed</div>
    <div class="stat-pill"><span class="dot dot-amber"></span><span id="activeCount">0</span> In Progress</div>
    <div class="stat-pill"><span class="dot dot-red"></span><span id="notStartedCount">0</span> Not Started</div>
  </div>
</header>

<!-- Progress Banner -->
<div class="progress-banner">
  <span class="progress-label">Overall Progress</span>
  <div class="progress-bar-container">
    <div class="progress-bar-fill" id="progressFill" style="width:0%"></div>
  </div>
  <span class="progress-pct" id="progressPct">0%</span>
</div>

<!-- Tabs -->
<nav class="tabs">
  <div class="tab active" onclick="switchTab('topics')" data-tab="topics">
    <span class="tab-icon">📋</span> All Topics
  </div>
  <div class="tab" onclick="switchTab('hld')" data-tab="hld">
    <span class="tab-icon">🏗️</span> High Level Design
  </div>
  <div class="tab" onclick="switchTab('lld')" data-tab="lld">
    <span class="tab-icon">⚙️</span> Low Level Design
  </div>
  <div class="tab" onclick="switchTab('frequency')" data-tab="frequency">
    <span class="tab-icon">📊</span> Frequency & Importance
  </div>
  <div class="tab" onclick="switchTab('questions')" data-tab="questions">
    <span class="tab-icon">❓</span> Interview Questions
  </div>
</nav>

<div class="main">

  <!-- ALL TOPICS TAB -->
  <div class="tab-content active" id="tab-topics">
    <div class="panel-header">
      <div class="panel-title">System Design Topics</div>
      <div class="filter-bar">
        <input class="search-input" type="text" placeholder="🔍  Search topics..." oninput="filterTopics(this.value)" />
        <button class="filter-btn active" onclick="filterByStatus('all', this)">All</button>
        <button class="filter-btn" onclick="filterByStatus('not-started', this)">Not Started</button>
        <button class="filter-btn" onclick="filterByStatus('active', this)">Active</button>
        <button class="filter-btn" onclick="filterByStatus('completed', this)">Completed</button>
        <button class="filter-btn" onclick="filterByType('all', this)">HLD+LLD</button>
        <button class="filter-btn" onclick="filterByType('HLD', this)">HLD Only</button>
        <button class="filter-btn" onclick="filterByType('LLD', this)">LLD Only</button>
      </div>
    </div>
    <div class="table-wrapper">
      <table id="topicsTable">
        <thead>
          <tr>
            <th style="width:32px">#</th>
            <th style="min-width:220px">Topic</th>
            <th>Type</th>
            <th>Importance</th>
            <th style="min-width:140px">Status</th>
            <th>Asked At</th>
            <th style="min-width:260px">Resources</th>
          </tr>
        </thead>
        <tbody id="topicsBody"></tbody>
      </table>
    </div>
  </div>

  <!-- HLD TAB -->
  <div class="tab-content" id="tab-hld">
    <div class="panel-header">
      <div class="panel-title">High Level Design</div>
    </div>
    <div class="table-wrapper">
      <table>
        <thead>
          <tr>
            <th style="width:32px">#</th>
            <th style="min-width:220px">Topic</th>
            <th>Importance</th>
            <th style="min-width:140px">Status</th>
            <th>Asked At</th>
            <th style="min-width:260px">Resources</th>
          </tr>
        </thead>
        <tbody id="hldBody"></tbody>
      </table>
    </div>
  </div>

  <!-- LLD TAB -->
  <div class="tab-content" id="tab-lld">
    <div class="panel-header">
      <div class="panel-title">Low Level Design</div>
    </div>
    <div class="table-wrapper">
      <table>
        <thead>
          <tr>
            <th style="width:32px">#</th>
            <th style="min-width:220px">Topic</th>
            <th>Importance</th>
            <th style="min-width:140px">Status</th>
            <th>Asked At</th>
            <th style="min-width:260px">Resources</th>
          </tr>
        </thead>
        <tbody id="lldBody"></tbody>
      </table>
    </div>
  </div>

  <!-- FREQUENCY TAB -->
  <div class="tab-content" id="tab-frequency">
    <div class="panel-header">
      <div class="panel-title">Topic Frequency & Importance</div>
    </div>
    <div class="freq-grid" id="freqGrid"></div>
  </div>

  <!-- QUESTIONS TAB -->
  <div class="tab-content" id="tab-questions">
    <div class="panel-header">
      <div class="panel-title">Most Asked Interview Questions</div>
      <div class="filter-bar">
        <input class="search-input" type="text" placeholder="🔍  Search questions..." oninput="filterQuestions(this.value)" />
        <button class="filter-btn active" onclick="filterQByType('all', this)">All</button>
        <button class="filter-btn" onclick="filterQByType('HLD', this)">HLD</button>
        <button class="filter-btn" onclick="filterQByType('LLD', this)">LLD</button>
      </div>
    </div>
    <div class="questions-grid" id="questionsGrid"></div>
  </div>

</div>

<!-- Add Link Modal -->
<div class="modal-overlay" id="addLinkModal">
  <div class="modal">
    <div class="modal-title">⊕ Add Resource Link</div>
    <div id="modalTopicName" style="font-size:12px;color:var(--text2);margin-bottom:16px;padding-bottom:12px;border-bottom:1px solid var(--border)"></div>
    <div class="modal-label">Link Title</div>
    <input class="modal-input" type="text" id="linkTitle" placeholder="e.g. System Design Primer — Scaling"/>
    <div class="modal-label">URL</div>
    <input class="modal-input" type="text" id="linkUrl" placeholder="https://medium.com/..."/>
    <div class="modal-buttons">
      <button class="btn btn-ghost" onclick="closeModal()">Cancel</button>
      <button class="btn btn-primary" onclick="saveLink()">Add Link</button>
    </div>
  </div>
</div>

<script>
// ===================== DATA =====================
const topicsData = [
  // ---- HLD ----
  { id:1,  name:"URL Shortener (Bit.ly)", type:"HLD", icon:"🔗", importance:"critical", companies:["Amazon","Google","Microsoft","Uber"],
    links:[{title:"Designing TinyURL",url:"https://www.educative.io/courses/grokking-the-system-design-interview/m2ygV4E81AR"}],
    desc:"Scalable URL shortening service" },
  { id:2,  name:"Twitter / Social Feed", type:"HLD", icon:"🐦", importance:"critical", companies:["Twitter","Facebook","LinkedIn","Snap"],
    links:[{title:"Designing Twitter",url:"https://www.educative.io/courses/grokking-the-system-design-interview/m2G48X18NDO"}],
    desc:"News feed, fanout, timeline" },
  { id:3,  name:"YouTube / Netflix (Video Streaming)", type:"HLD", icon:"▶️", importance:"critical", companies:["Netflix","YouTube","Amazon","Microsoft"],
    links:[{title:"Designing YouTube",url:"https://www.educative.io/courses/grokking-the-system-design-interview/xV26VjZ7yMl"}],
    desc:"Video upload, CDN, transcoding" },
  { id:4,  name:"WhatsApp / Chat System", type:"HLD", icon:"💬", importance:"critical", companies:["WhatsApp","Slack","Discord","Microsoft"],
    links:[{title:"Designing a Chat App",url:"https://medium.com/swlh/design-a-chat-system-f20a9e0ff1e3"}],
    desc:"Real-time messaging, WebSockets" },
  { id:5,  name:"Uber / Ride Sharing", type:"HLD", icon:"🚗", importance:"critical", companies:["Uber","Lyft","Ola","DoorDash"],
    links:[{title:"Uber System Design",url:"https://medium.com/@narengowda/uber-system-design-8b2bc95e2cfe"}],
    desc:"Geo-indexing, matching, surge" },
  { id:6,  name:"Google Search", type:"HLD", icon:"🔍", importance:"critical", companies:["Google","Bing","Amazon"],
    links:[{title:"Search Autocomplete Design",url:"https://www.educative.io/courses/grokking-the-system-design-interview/mE2XkgGRnmp"}],
    desc:"Crawling, indexing, ranking" },
  { id:7,  name:"Instagram / Photo Sharing", type:"HLD", icon:"📸", importance:"high", companies:["Meta","Pinterest","Snap","Twitter"],
    links:[{title:"Designing Instagram",url:"https://www.educative.io/courses/grokking-the-system-design-interview/m22LWKgXOEm"}],
    desc:"Media storage, CDN, feed" },
  { id:8,  name:"Amazon / E-Commerce", type:"HLD", icon:"🛒", importance:"high", companies:["Amazon","Flipkart","Shopify","eBay"],
    links:[{title:"E-Commerce System Design",url:"https://medium.com/nerd-for-tech/system-design-of-e-commerce-platform-like-amazon-9d2f3e6b82f"}],
    desc:"Product catalog, cart, orders, payments" },
  { id:9,  name:"Rate Limiter", type:"HLD", icon:"🚦", importance:"critical", companies:["Stripe","Cloudflare","Google","Amazon"],
    links:[{title:"System Design Rate Limiter",url:"https://medium.com/@saurabh.codes/system-design-rate-limiter-1e89a4a66a32"}],
    desc:"Token bucket, leaky bucket, sliding window" },
  { id:10, name:"Distributed Cache (Redis)", type:"HLD", icon:"⚡", importance:"critical", companies:["Amazon","Google","Meta","Netflix"],
    links:[{title:"Design a Distributed Cache",url:"https://medium.com/system-design-blog/distributed-cache-system-design-9a8b4d19e9b3"}],
    desc:"Eviction policies, consistency, sharding" },
  { id:11, name:"CDN (Content Delivery Network)", type:"HLD", icon:"🌐", importance:"high", companies:["Cloudflare","Amazon","Netflix","Akamai"],
    links:[{title:"How CDN Works",url:"https://medium.com/netflix-techblog/open-connect-overview-7c23e0e8c5f0"}],
    desc:"Edge caching, PoPs, cache invalidation" },
  { id:12, name:"Message Queue (Kafka)", type:"HLD", icon:"📨", importance:"critical", companies:["LinkedIn","Uber","Netflix","Airbnb"],
    links:[{title:"Kafka System Design",url:"https://medium.com/@pankaj.itdeveloper/apache-kafka-architecture-and-design-2c5b3b4e1f8d"}],
    desc:"Pub/sub, partitions, consumer groups" },
  { id:13, name:"Notification System", type:"HLD", icon:"🔔", importance:"high", companies:["Apple","Google","Meta","Slack"],
    links:[{title:"Design Notification System",url:"https://medium.com/nerd-for-tech/system-design-notification-system-9d0e0f73a4e2"}],
    desc:"Push, SMS, email, fanout" },
  { id:14, name:"Google Maps / Location Service", type:"HLD", icon:"📍", importance:"high", companies:["Google","Uber","DoorDash","Lyft"],
    links:[{title:"Designing Google Maps",url:"https://medium.com/@narengowda/designing-google-maps-a66e24e3e3c0"}],
    desc:"Geo-spatial indexing, routing, ETA" },
  { id:15, name:"Distributed File Storage (S3)", type:"HLD", icon:"🗄️", importance:"high", companies:["Amazon","Google","Dropbox","Box"],
    links:[{title:"Design Dropbox",url:"https://www.educative.io/courses/grokking-the-system-design-interview/gxMDOe16mql"}],
    desc:"Object storage, replication, deduplication" },
  { id:16, name:"Search Autocomplete / Typeahead", type:"HLD", icon:"✏️", importance:"high", companies:["Google","Amazon","Twitter","LinkedIn"],
    links:[{title:"Typeahead Search Design",url:"https://www.educative.io/courses/grokking-the-system-design-interview/mE2XkgGRnmp"}],
    desc:"Trie, prefix search, caching" },
  { id:17, name:"Ticketmaster / Event Booking", type:"HLD", icon:"🎟️", importance:"high", companies:["Ticketmaster","BookMyShow","Amazon"],
    links:[{title:"Design Ticketmaster",url:"https://medium.com/@liamchzh/system-design-ticketmaster-9c4e85e02d7c"}],
    desc:"Seat selection, concurrency, payments" },
  { id:18, name:"Google Docs / Collaborative Editor", type:"HLD", icon:"📄", importance:"high", companies:["Google","Microsoft","Notion","Atlassian"],
    links:[{title:"Collaborative Editing Design",url:"https://medium.com/@saurabh.codes/google-docs-system-design-real-time-collaboration-97e3c0c0a0e5"}],
    desc:"OT, CRDT, conflict resolution" },
  { id:19, name:"Payment System / Stripe", type:"HLD", icon:"💳", importance:"high", companies:["Stripe","PayPal","Razorpay","Square"],
    links:[{title:"Design a Payment System",url:"https://medium.com/system-design-blog/payment-system-design-3f3b2e2e0f6d"}],
    desc:"Idempotency, double-spend, ledger" },
  { id:20, name:"Recommendation Engine", type:"HLD", icon:"🎯", importance:"medium", companies:["Netflix","Spotify","Amazon","YouTube"],
    links:[{title:"Recommendation System Design",url:"https://medium.com/netflix-techblog/system-architectures-for-personalization-and-recommendation-e081aa94b5d8"}],
    desc:"Collaborative filtering, ML pipeline" },
  { id:21, name:"API Gateway / Load Balancer", type:"HLD", icon:"🔀", importance:"critical", companies:["Amazon","Netflix","Uber","Cloudflare"],
    links:[{title:"API Gateway Design",url:"https://medium.com/system-design-blog/api-gateway-design-6b2c8d1f3e9a"}],
    desc:"L4/L7 load balancing, reverse proxy" },
  { id:22, name:"Log / Metrics Aggregation", type:"HLD", icon:"📈", importance:"medium", companies:["Datadog","Splunk","Netflix","Uber"],
    links:[{title:"Distributed Logging Design",url:"https://medium.com/@pankaj.itdeveloper/distributed-logging-system-design-4e3f2c1b0d7a"}],
    desc:"Time-series data, aggregation, alerting" },
  { id:23, name:"Web Crawler", type:"HLD", icon:"🕷️", importance:"medium", companies:["Google","Amazon","Bing"],
    links:[{title:"Design a Web Crawler",url:"https://www.educative.io/courses/grokking-the-system-design-interview/NE5LpPrWrKv"}],
    desc:"BFS, politeness, deduplication" },
  { id:24, name:"Distributed ID Generator", type:"HLD", icon:"🆔", importance:"high", companies:["Twitter","Instagram","Uber","Discord"],
    links:[{title:"Snowflake ID Design",url:"https://medium.com/@pankaj.itdeveloper/twitter-snowflake-unique-id-generator-2c3f4e5b1a9d"}],
    desc:"Snowflake, UUID, monotonic IDs" },
  { id:25, name:"Consistent Hashing", type:"HLD", icon:"🔄", importance:"critical", companies:["Amazon","Google","Cassandra","Redis"],
    links:[{title:"Consistent Hashing Explained",url:"https://medium.com/system-design-blog/consistent-hashing-a296b46e9c7f"}],
    desc:"Virtual nodes, ring topology" },
  { id:26, name:"CAP Theorem / BASE / ACID", type:"HLD", icon:"📐", importance:"critical", companies:["All FAANG","Stripe","Cloudflare"],
    links:[{title:"CAP Theorem Deep Dive",url:"https://medium.com/system-design-blog/cap-theorem-in-depth-e2b3c4d5f6a7"}],
    desc:"Consistency vs Availability trade-offs" },
  { id:27, name:"Database Sharding & Partitioning", type:"HLD", icon:"🗃️", importance:"critical", companies:["Amazon","Google","Uber","Airbnb"],
    links:[{title:"Database Sharding Guide",url:"https://medium.com/system-design-blog/database-sharding-9c3f2d1e5b8a"}],
    desc:"Horizontal scaling, hot spots, rebalancing" },
  { id:28, name:"Circuit Breaker / Resiliency", type:"HLD", icon:"⚠️", importance:"high", companies:["Netflix","Amazon","Uber","Microsoft"],
    links:[{title:"Circuit Breaker Pattern",url:"https://medium.com/@pankaj.itdeveloper/circuit-breaker-design-pattern-1a2b3c4d5e6f"}],
    desc:"Retry, timeout, bulkhead patterns" },
  // ---- LLD ----
  { id:29, name:"Parking Lot System", type:"LLD", icon:"🅿️", importance:"high", companies:["Amazon","Microsoft","Uber"],
    links:[{title:"Parking Lot LLD",url:"https://medium.com/nerd-for-tech/low-level-design-of-a-parking-lot-system-58e2a34e05c4"}],
    desc:"OOP design, slots, billing" },
  { id:30, name:"Elevator / Lift System", type:"LLD", icon:"🛗", importance:"high", companies:["Amazon","Google","Microsoft"],
    links:[{title:"Elevator System LLD",url:"https://medium.com/nerd-for-tech/object-oriented-design-of-an-elevator-system-in-java-ef21f47df69f"}],
    desc:"Scheduling algorithms, states" },
  { id:31, name:"Library Management System", type:"LLD", icon:"📚", importance:"medium", companies:["Amazon","Google","Microsoft"],
    links:[{title:"Library System LLD",url:"https://medium.com/nerd-for-tech/low-level-design-library-management-system-7e2a3f4b5c9d"}],
    desc:"Books, members, lending, fines" },
  { id:32, name:"Hotel Booking System", type:"LLD", icon:"🏨", importance:"high", companies:["Booking.com","Airbnb","Expedia","Google"],
    links:[{title:"Hotel Booking LLD",url:"https://medium.com/nerd-for-tech/low-level-design-hotel-booking-9f3a2c1b8e7d"}],
    desc:"Rooms, reservations, availability" },
  { id:33, name:"Chess / Board Game", type:"LLD", icon:"♟️", importance:"high", companies:["Amazon","Google","Microsoft"],
    links:[{title:"Chess Game LLD",url:"https://medium.com/nerd-for-tech/low-level-design-of-chess-game-using-object-oriented-design-7b1e8f4c3a5d"}],
    desc:"Pieces, moves, turns, game state" },
  { id:34, name:"ATM System", type:"LLD", icon:"🏧", importance:"high", companies:["Amazon","Google","IBM"],
    links:[{title:"ATM System LLD",url:"https://medium.com/nerd-for-tech/low-level-design-atm-machine-2c3f1a9b8e7d"}],
    desc:"Cards, accounts, transactions, states" },
  { id:35, name:"LRU Cache", type:"LLD", icon:"💾", importance:"critical", companies:["Google","Amazon","Meta","Microsoft"],
    links:[{title:"LRU Cache Design",url:"https://medium.com/@pankaj.itdeveloper/lru-cache-implementation-2a3f4c5b1d8e"}],
    desc:"HashMap + DLL, O(1) ops" },
  { id:36, name:"Logger / Logging Framework", type:"LLD", icon:"📝", importance:"medium", companies:["Amazon","Google","Microsoft"],
    links:[{title:"Logger System LLD",url:"https://medium.com/nerd-for-tech/low-level-design-logger-system-3e4f2c1b9a8d"}],
    desc:"Log levels, appenders, formatters" },
  { id:37, name:"Vending Machine", type:"LLD", icon:"🥤", importance:"high", companies:["Amazon","Google","Uber"],
    links:[{title:"Vending Machine LLD",url:"https://medium.com/nerd-for-tech/low-level-design-vending-machine-7a2c3f1e9b8d"}],
    desc:"State machine, inventory, payments" },
  { id:38, name:"Snake & Ladder / Board Game", type:"LLD", icon:"🎲", importance:"medium", companies:["Amazon","Microsoft"],
    links:[{title:"Snake & Ladder LLD",url:"https://medium.com/nerd-for-tech/design-snake-and-ladder-game-1c2f3a9b8e7d"}],
    desc:"Board, dice, players, moves" },
  { id:39, name:"Splitwise / Expense Sharing", type:"LLD", icon:"💰", importance:"high", companies:["Amazon","Airbnb","Uber"],
    links:[{title:"Splitwise LLD",url:"https://medium.com/nerd-for-tech/low-level-design-splitwise-2f3a1c9b8e7d"}],
    desc:"Groups, expenses, simplify debts" },
  { id:40, name:"Food Delivery App (Swiggy/Zomato)", type:"LLD", icon:"🍕", importance:"high", companies:["Swiggy","Zomato","DoorDash","Uber Eats"],
    links:[{title:"Food Delivery LLD",url:"https://medium.com/nerd-for-tech/low-level-design-food-delivery-3c4f2a1b9e8d"}],
    desc:"Restaurants, orders, delivery, tracking" },
  { id:41, name:"Movie Ticket Booking (BookMyShow)", type:"LLD", icon:"🎬", importance:"high", companies:["BookMyShow","Ticketmaster","Fandango"],
    links:[{title:"BookMyShow LLD",url:"https://medium.com/nerd-for-tech/design-bookmyshow-low-level-design-4e3f2c1a9b8d"}],
    desc:"Theatres, shows, seats, payments" },
  { id:42, name:"Observer / Pub-Sub Pattern", type:"LLD", icon:"📡", importance:"high", companies:["All FAANG","Stripe","Salesforce"],
    links:[{title:"Observer Pattern",url:"https://medium.com/nerd-for-tech/observer-design-pattern-5e4c3b2a1f9d"}],
    desc:"Event system, decoupling, callbacks" },
  { id:43, name:"Strategy / Factory Design Patterns", type:"LLD", icon:"🏭", importance:"critical", companies:["All FAANG","Stripe","Atlassian"],
    links:[{title:"Design Patterns Guide",url:"https://medium.com/nerd-for-tech/design-patterns-every-developer-should-know-6e5c4b3a2f1d"}],
    desc:"GoF patterns, SOLID principles" },
  { id:44, name:"Cricinfo / Live Sports Score", type:"LLD", icon:"🏏", importance:"medium", companies:["Amazon","Google","ESPN"],
    links:[{title:"Cricket Score System LLD",url:"https://medium.com/nerd-for-tech/low-level-design-cricinfo-7a3c2f1b8e9d"}],
    desc:"Match, innings, players, live updates" },
  { id:45, name:"SOLID Principles", type:"LLD", icon:"🔩", importance:"critical", companies:["All FAANG","Microsoft","Atlassian"],
    links:[{title:"SOLID Principles in Depth",url:"https://medium.com/nerd-for-tech/solid-principles-explained-2a3f4c5b1d8e"}],
    desc:"SRP, OCP, LSP, ISP, DIP" },
];

const interviewQuestions = [
  { id:1, text:"Design a URL shortener like bit.ly. How would you handle 1 billion URLs?", type:"HLD", freq:5, topic:"URL Shortener", companies:["Amazon","Google","Uber"] },
  { id:2, text:"How would you design Twitter's home timeline? How do you handle celebrity accounts with millions of followers?", type:"HLD", freq:5, topic:"Social Feed", companies:["Twitter","Meta","LinkedIn"] },
  { id:3, text:"Design a distributed cache. How do you handle cache invalidation and eviction?", type:"HLD", freq:5, topic:"Caching", companies:["Amazon","Google","Meta"] },
  { id:4, text:"How would you design WhatsApp? How does message delivery work offline?", type:"HLD", freq:5, topic:"Chat System", companies:["Meta","Microsoft","Slack"] },
  { id:5, text:"Design Netflix's video streaming service. How do you ensure low latency globally?", type:"HLD", freq:5, topic:"Video Streaming", companies:["Netflix","YouTube","Amazon"] },
  { id:6, text:"How do you design a rate limiter? Explain token bucket vs sliding window algorithms.", type:"HLD", freq:5, topic:"Rate Limiting", companies:["Stripe","Cloudflare","Google"] },
  { id:7, text:"Design Uber's ride-matching system. How do you find nearby drivers efficiently?", type:"HLD", freq:5, topic:"Uber / Geo", companies:["Uber","Lyft","DoorDash"] },
  { id:8, text:"How would you design a notification system to send 1 million push notifications per second?", type:"HLD", freq:4, topic:"Notifications", companies:["Apple","Google","Meta"] },
  { id:9, text:"Explain consistent hashing. Why is it used in distributed systems?", type:"HLD", freq:5, topic:"Consistent Hashing", companies:["Amazon","Google","Cassandra"] },
  { id:10, text:"How does a message queue like Kafka work? When would you use it vs a database?", type:"HLD", freq:5, topic:"Message Queue", companies:["LinkedIn","Uber","Netflix"] },
  { id:11, text:"Design Google Search's autocomplete feature. How do you handle real-time suggestions?", type:"HLD", freq:4, topic:"Typeahead Search", companies:["Google","Amazon","Twitter"] },
  { id:12, text:"How would you design a payment system? How do you prevent double charges?", type:"HLD", freq:4, topic:"Payment System", companies:["Stripe","PayPal","Amazon"] },
  { id:13, text:"What is the CAP theorem? Give real-world examples of each trade-off.", type:"HLD", freq:5, topic:"CAP / Distributed", companies:["All FAANG","Stripe"] },
  { id:14, text:"How do you shard a database? What is the difference between range-based and hash-based sharding?", type:"HLD", freq:5, topic:"Database Sharding", companies:["Amazon","Uber","Airbnb"] },
  { id:15, text:"Design Google Docs with real-time collaboration. How do you handle conflicting edits?", type:"HLD", freq:4, topic:"Collaborative Editor", companies:["Google","Microsoft","Notion"] },
  { id:16, text:"Design an LRU Cache. Implement it with O(1) get and put operations.", type:"LLD", freq:5, topic:"LRU Cache", companies:["Google","Amazon","Meta"] },
  { id:17, text:"Design a parking lot system. What classes and relationships would you model?", type:"LLD", freq:5, topic:"Parking Lot", companies:["Amazon","Microsoft","Uber"] },
  { id:18, text:"Explain SOLID principles with code examples. How does Dependency Inversion work?", type:"LLD", freq:5, topic:"SOLID", companies:["All FAANG","Atlassian"] },
  { id:19, text:"Design an elevator scheduling system. How do you minimize wait time?", type:"LLD", freq:4, topic:"Elevator System", companies:["Amazon","Google","Microsoft"] },
  { id:20, text:"Design a vending machine. How do you model the state transitions?", type:"LLD", freq:4, topic:"Vending Machine", companies:["Amazon","Uber","Google"] },
  { id:21, text:"How would you design the Splitwise app? How do you simplify debts in a group?", type:"LLD", freq:4, topic:"Splitwise", companies:["Airbnb","Uber","Amazon"] },
  { id:22, text:"Design the Observer pattern. How is it different from a message queue?", type:"LLD", freq:4, topic:"Design Patterns", companies:["All FAANG","Salesforce"] },
  { id:23, text:"Design a Chess game. How do you validate moves and detect checkmate?", type:"LLD", freq:3, topic:"Chess", companies:["Amazon","Google","Microsoft"] },
  { id:24, text:"What is the difference between a process and a thread? How do you handle concurrency in LLD?", type:"LLD", freq:4, topic:"Concurrency", companies:["All FAANG","Microsoft"] },
  { id:25, text:"Design BookMyShow's seat booking. How do you prevent two users from booking the same seat?", type:"LLD", freq:4, topic:"Ticket Booking", companies:["BookMyShow","Ticketmaster","Amazon"] },
];

// ===================== STATE =====================
let progress = {};
let customLinks = {};
let currentFilterStatus = 'all';
let currentFilterType = 'all';
let currentSearch = '';
let currentQType = 'all';
let currentQSearch = '';
let addLinkTarget = null;

// Load from localStorage
function loadState() {
  try {
    const saved = localStorage.getItem('sysdesign-progress');
    if (saved) progress = JSON.parse(saved);
    const savedLinks = localStorage.getItem('sysdesign-links');
    if (savedLinks) customLinks = JSON.parse(savedLinks);
  } catch(e) {}
}

function saveState() {
  try {
    localStorage.setItem('sysdesign-progress', JSON.stringify(progress));
    localStorage.setItem('sysdesign-links', JSON.stringify(customLinks));
  } catch(e) {}
}

// ===================== TAB SWITCHING =====================
function switchTab(tab) {
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
  document.querySelector(`[data-tab="${tab}"]`).classList.add('active');
  document.getElementById(`tab-${tab}`).classList.add('active');

  if (tab === 'hld') renderSubTable('hldBody', topicsData.filter(t => t.type === 'HLD'));
  if (tab === 'lld') renderSubTable('lldBody', topicsData.filter(t => t.type === 'LLD'));
  if (tab === 'frequency') renderFrequency();
  if (tab === 'questions') renderQuestions();
}

// ===================== TABLE RENDERING =====================
function renderTopicsTable() {
  let filtered = topicsData.filter(t => {
    const statusMatch = currentFilterStatus === 'all' || (progress[t.id] || 'not-started') === currentFilterStatus;
    const typeMatch = currentFilterType === 'all' || t.type === currentFilterType;
    const searchMatch = !currentSearch || t.name.toLowerCase().includes(currentSearch.toLowerCase()) || t.desc.toLowerCase().includes(currentSearch.toLowerCase());
    return statusMatch && typeMatch && searchMatch;
  });

  const tbody = document.getElementById('topicsBody');
  tbody.innerHTML = '';

  if (filtered.length === 0) {
    tbody.innerHTML = `<tr><td colspan="7" class="empty">// no topics match current filters</td></tr>`;
    return;
  }

  filtered.forEach((topic, idx) => renderTopicRow(tbody, topic, idx + 1, true));
  updateStats();
}

function renderSubTable(bodyId, topics) {
  const tbody = document.getElementById(bodyId);
  tbody.innerHTML = '';
  topics.forEach((topic, idx) => renderTopicRow(tbody, topic, idx + 1, false));
}

function renderTopicRow(tbody, topic, idx, showType) {
  const status = progress[topic.id] || 'not-started';
  const allLinks = [...topic.links, ...(customLinks[topic.id] || [])];

  const tr = document.createElement('tr');
  tr.dataset.topicId = topic.id;

  const impSegs = ['','','','',''].map((_, i) => {
    const levels = { critical:5, high:4, medium:3, low:1 };
    const filled = i < levels[topic.importance];
    return `<div class="imp-seg ${filled ? 'on-'+topic.importance : ''}"></div>`;
  }).join('');

  const impLabel = { critical:'Critical', high:'High', medium:'Medium', low:'Low' }[topic.importance];
  const impLabelColor = { critical:'var(--red)', high:'var(--amber)', medium:'var(--green2)', low:'var(--text3)' }[topic.importance];

  const typeBadge = showType ? `<td><span class="badge badge-${topic.type.toLowerCase()}">${topic.type}</span></td>` : '';

  const linksHtml = allLinks.map(l =>
    `<a class="link-chip" href="${l.url}" target="_blank" rel="noopener">📖 ${l.title}</a>`
  ).join('') + `<button class="add-link-btn" onclick="openAddLink(${topic.id})">+ Add</button>`;

  tr.innerHTML = `
    <td style="color:var(--text3);font-size:11px">${String(idx).padStart(2,'0')}</td>
    <td>
      <div class="topic-name"><span class="topic-icon">${topic.icon}</span>${topic.name}</div>
      <div class="topic-category">${topic.desc}</div>
    </td>
    ${typeBadge}
    <td>
      <div class="importance">
        <div class="imp-bar">${impSegs}</div>
        <span class="imp-label" style="color:${impLabelColor}">${impLabel}</span>
      </div>
    </td>
    <td>
      <select class="status-select ${status}" onchange="updateStatus(${topic.id}, this)">
        <option value="not-started" ${status==='not-started'?'selected':''}>⬜ Not Started</option>
        <option value="active" ${status==='active'?'selected':''}>🔄 Active</option>
        <option value="completed" ${status==='completed'?'selected':''}>✅ Completed</option>
      </select>
    </td>
    <td>
      <div class="companies">
        ${topic.companies.map(c => `<span class="company-tag">${c}</span>`).join('')}
      </div>
    </td>
    <td>
      <div class="links-cell">${linksHtml}</div>
    </td>
  `;

  tbody.appendChild(tr);
}

// ===================== STATUS UPDATE =====================
function updateStatus(topicId, selectEl) {
  const val = selectEl.value;
  selectEl.className = `status-select ${val}`;
  progress[topicId] = val;
  saveState();
  updateStats();
}

function updateStats() {
  const values = topicsData.map(t => progress[t.id] || 'not-started');
  const completed = values.filter(v => v === 'completed').length;
  const active = values.filter(v => v === 'active').length;
  const notStarted = values.filter(v => v === 'not-started').length;

  document.getElementById('completedCount').textContent = completed;
  document.getElementById('activeCount').textContent = active;
  document.getElementById('notStartedCount').textContent = notStarted;

  const pct = Math.round((completed / topicsData.length) * 100);
  document.getElementById('progressFill').style.width = pct + '%';
  document.getElementById('progressPct').textContent = pct + '%';
}

// ===================== FILTERS =====================
function filterTopics(val) {
  currentSearch = val;
  renderTopicsTable();
}

function filterByStatus(status, btn) {
  currentFilterStatus = status;
  document.querySelectorAll('.filter-btn').forEach(b => {
    if (['all','not-started','active','completed'].includes(b.textContent.trim().toLowerCase().replace(' ','-'))) b.classList.remove('active');
  });
  // reset status filter buttons only
  const statusBtns = document.querySelectorAll('#tab-topics .filter-bar .filter-btn');
  statusBtns.forEach(b => {
    if (['All','Not Started','Active','Completed'].includes(b.textContent.trim())) b.classList.remove('active');
  });
  btn.classList.add('active');
  renderTopicsTable();
}

function filterByType(type, btn) {
  currentFilterType = type;
  const typeBtns = ['HLD+LLD','HLD Only','LLD Only'];
  document.querySelectorAll('#tab-topics .filter-bar .filter-btn').forEach(b => {
    if (typeBtns.includes(b.textContent.trim())) b.classList.remove('active');
  });
  btn.classList.add('active');
  renderTopicsTable();
}

// ===================== ADD LINK =====================
function openAddLink(topicId) {
  addLinkTarget = topicId;
  const topic = topicsData.find(t => t.id === topicId);
  document.getElementById('modalTopicName').textContent = topic.icon + '  ' + topic.name;
  document.getElementById('linkTitle').value = '';
  document.getElementById('linkUrl').value = '';
  document.getElementById('addLinkModal').classList.add('open');
  setTimeout(() => document.getElementById('linkTitle').focus(), 100);
}

function closeModal() {
  document.getElementById('addLinkModal').classList.remove('open');
  addLinkTarget = null;
}

function saveLink() {
  const title = document.getElementById('linkTitle').value.trim();
  const url = document.getElementById('linkUrl').value.trim();
  if (!title || !url) return;

  if (!customLinks[addLinkTarget]) customLinks[addLinkTarget] = [];
  customLinks[addLinkTarget].push({ title, url });
  saveState();
  closeModal();
  renderTopicsTable();
}

// ===================== FREQUENCY TAB =====================
function renderFrequency() {
  const grid = document.getElementById('freqGrid');
  grid.innerHTML = '';

  const sorted = [...topicsData].sort((a, b) => {
    const order = { critical:0, high:1, medium:2, low:3 };
    return order[a.importance] - order[b.importance];
  });

  sorted.forEach(topic => {
    const pctMap = { critical:95, high:78, medium:55, low:30 };
    const pct = pctMap[topic.importance];
    const colorMap = { critical:'fill-critical', high:'fill-high', medium:'fill-medium', low:'fill-low' };
    const labelMap = { critical:'Must Know', high:'Very Common', medium:'Common', low:'Occasional' };

    const card = document.createElement('div');
    card.className = 'freq-card';
    card.innerHTML = `
      <div class="freq-card-name">${topic.icon} ${topic.name}</div>
      <div class="freq-card-type">${topic.type} · ${labelMap[topic.importance]}</div>
      <div class="freq-meter">
        <span class="freq-meter-label">Ask freq.</span>
        <div class="freq-meter-bar">
          <div class="freq-meter-fill ${colorMap[topic.importance]}" style="width:${pct}%"></div>
        </div>
        <span class="freq-pct" style="color:${pct>75?'var(--red)':pct>55?'var(--amber)':'var(--green2)'}">${pct}%</span>
      </div>
      <div class="freq-companies-label">Asked at:</div>
      <div class="companies">${topic.companies.map(c => `<span class="company-tag">${c}</span>`).join('')}</div>
    `;
    grid.appendChild(card);
  });
}

// ===================== QUESTIONS TAB =====================
function renderQuestions() {
  let filtered = interviewQuestions.filter(q => {
    const typeMatch = currentQType === 'all' || q.type === currentQType;
    const searchMatch = !currentQSearch || q.text.toLowerCase().includes(currentQSearch.toLowerCase()) || q.topic.toLowerCase().includes(currentQSearch.toLowerCase());
    return typeMatch && searchMatch;
  });

  const grid = document.getElementById('questionsGrid');
  grid.innerHTML = '';

  filtered.forEach((q, idx) => {
    const freqDots = [1,2,3,4,5].map(i =>
      `<div class="freq-dot ${i <= q.freq ? 'on' : ''}"></div>`
    ).join('');

    const card = document.createElement('div');
    card.className = 'question-card';
    card.innerHTML = `
      <div class="question-card-header">
        <span class="question-num">Q${String(idx+1).padStart(3,'0')}</span>
        <span class="question-text">${q.text}</span>
        <div class="question-freq" title="Frequency: ${q.freq}/5">${freqDots}</div>
      </div>
      <div class="question-meta">
        <span class="q-tag q-tag-topic">${q.type} · ${q.topic}</span>
        ${q.companies.map(c => `<span class="q-tag q-tag-company">${c}</span>`).join('')}
      </div>
      <button class="toggle-answer" onclick="toggleAnswer(this)">▶ Show hint</button>
      <div class="answer-box">${getHint(q.id)}</div>
    `;
    grid.appendChild(card);
  });
}

function toggleAnswer(btn) {
  const box = btn.nextElementSibling;
  box.classList.toggle('open');
  btn.textContent = box.classList.contains('open') ? '▼ Hide hint' : '▶ Show hint';
}

function filterQByType(type, btn) {
  currentQType = type;
  document.querySelectorAll('#tab-questions .filter-bar .filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  renderQuestions();
}

function filterQuestions(val) {
  currentQSearch = val;
  renderQuestions();
}

function getHint(id) {
  const hints = {
    1: "Key ideas: Base62 encoding, hash function collision handling. Use a KV store (Redis) for redirect. Short code → long URL mapping. Consider expiry, analytics, custom aliases. Estimate ~100:1 read:write ratio.",
    2: "Fanout on write (push) vs fanout on read (pull). Use a separate timeline cache per user. Handle celebrities with hybrid approach — read heavy timelines pull from a celebrity feed cache. Redis sorted sets for timeline.",
    3: "Write-through vs write-back vs write-around cache. LRU/LFU eviction. Use consistent hashing for distributed cache nodes. Cache stampede: use mutex locks or probabilistic early expiration.",
    4: "WebSockets for real-time. Use last-seen timestamp for offline delivery. Messages stored in Cassandra (write-heavy). Use message queue for async delivery. End-to-end encryption with Signal Protocol.",
    5: "Chunk video into segments (HLS/DASH). CDN for edge delivery. Adaptive bitrate streaming. Use S3 for storage, transcoding workers. Client chooses quality based on bandwidth.",
    6: "Token bucket: tokens added at constant rate, consumed per request. Sliding window: count requests in rolling time window. Redis + Lua script for atomic check-and-set. Return 429 when exceeded.",
    7: "Geospatial indexing using S2 cells or geohash. WebSockets for real-time driver location updates. Matching algorithm: find k nearest drivers, rank by ETA. Use Kafka for location event stream.",
    8: "Fan-out service with priority queues. Device token registry. Platform-specific gateways (APNs, FCM). Retry with exponential backoff. Separate high-priority (OTP) from low-priority (marketing).",
    9: "Place servers on a hash ring. Each server owns a segment. Virtual nodes for even distribution. On server add/remove, only adjacent segment migrated. Used in DynamoDB, Cassandra, Redis Cluster.",
    10: "Producers write to partitions. Consumers in groups read from partitions. Ordered within partition, not across. Retention period. Kafka vs SQS: Kafka is pull-based, replays events; SQS deletes after consume.",
    11: "Trie for prefix matching. Cache top-k suggestions per prefix. Use DFS with pruning. Filter by recency, popularity. Redis sorted sets per prefix. Debounce on client side.",
    12: "Idempotency key per payment request. Ledger as append-only log. Two-phase commit for distributed transactions. Use saga pattern for rollbacks. PCI-DSS compliance considerations.",
    13: "C: all nodes see same data. A: every request gets a response. P: system works despite network partition. Partition always possible → choose C or A. CP: MongoDB. AP: Cassandra. CA: single-node.",
    14: "Hash-based: even distribution, hard to range query. Range-based: natural ordering, can have hot spots. Consistent hashing for rebalancing. Cross-shard transactions need 2PC or saga.",
    15: "Operational Transformation (OT) or CRDT for conflict resolution. Each operation is transformed against concurrent ops. Vector clocks for causality. WebSockets + operational log broadcast.",
    16: "HashMap<key, Node> + Doubly LinkedList. get: O(1) lookup, move to front. put: O(1) insert at front, evict tail if full. Thread-safe: ReentrantLock or ConcurrentHashMap.",
    17: "Classes: ParkingLot, Floor, ParkingSpot (Compact/Large/Handicapped), Vehicle, Ticket, PricingStrategy. State: spot.isFree(). Singleton ParkingLot. Strategy pattern for pricing.",
    18: "S: one reason to change. O: open for extension, closed for modification. L: subclass usable as base class. I: no fat interfaces. D: depend on abstractions not concretions. Demo with PaymentProcessor example.",
    19: "LOOK/SCAN algorithm: serve requests in current direction, reverse at end. Classes: Elevator, ElevatorController, Request, Floor. State machine: IDLE/UP/DOWN/MAINTENANCE. Min-heap for request scheduling.",
    20: "States: IDLE, HAS_MONEY, DISPENSE, OUT_OF_STOCK. Transitions driven by coin insert, select product, dispense. Use State pattern. Classes: VendingMachine, Coin, Product, Inventory.",
    21: "Graph of debts between users. Greedy simplification: net out debts, match creditors/debtors. Classes: User, Group, Expense, Split (Equal/Exact/Percentage), Balance. Use Heap for O(n log n) simplification.",
    22: "Subject maintains observer list. notify() calls update() on all observers. Decouples producer and consumer. vs Message Queue: queue is async, durable, distributed. Observer is in-process, synchronous.",
    23: "Classes: Board, Square, Piece (King/Queen/Rook/Bishop/Knight/Pawn), Player, Move, Game. Piece.isValidMove() polymorphism. Check detection: after move, is king in attack path? Checkmate: no valid moves.",
    24: "Thread: lightweight, shared memory. Process: isolated. Race conditions → use locks (synchronized, ReentrantLock). Deadlock avoidance: lock ordering, tryLock with timeout. ThreadLocal for request context.",
    25: "Optimistic locking: version field, fail if version mismatch. Pessimistic: SELECT FOR UPDATE. Two-phase: hold seat in PENDING for 10 min. Use distributed lock (Redis SETNX) for high-concurrency seat holds.",
  };
  return hints[id] || "Key concepts: Identify requirements → estimate scale → component design → data model → API → identify bottlenecks → iterate.";
}

// ===================== KEYBOARD SHORTCUTS =====================
document.addEventListener('keydown', e => {
  if (e.key === 'Escape') closeModal();
});

document.getElementById('addLinkModal').addEventListener('click', e => {
  if (e.target === document.getElementById('addLinkModal')) closeModal();
});

// Enter to save
document.getElementById('linkUrl').addEventListener('keydown', e => {
  if (e.key === 'Enter') saveLink();
});

// ===================== INIT =====================
loadState();
renderTopicsTable();
updateStats();
</script>
</body>
</html>