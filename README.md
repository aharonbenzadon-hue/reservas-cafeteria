[index.html (3).html](https://github.com/user-attachments/files/27656570/index.html.3.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Reservas — Cafetería</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #FAF8F5;
    --surface: #FFFFFF;
    --surface2: #F3F0EB;
    --border: #E8E2D9;
    --text: #1A1714;
    --text2: #6B6460;
    --text3: #9E9894;
    --accent: #C17C4A;
    --accent-light: #F5EDE3;
    --accent-dark: #8B5530;
    --green: #3D7A5C;
    --green-light: #E3F0EB;
    --amber: #B07D20;
    --amber-light: #FBF3DF;
    --red: #B04040;
    --red-light: #FAEAEA;
    --blue: #3A6EA8;
    --blue-light: #E8F0F8;
    --radius: 10px;
    --shadow: 0 2px 12px rgba(0,0,0,0.07);
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    font-size: 14px;
  }

  /* HEADER */
  header {
    background: var(--text);
    color: #FAF8F5;
    padding: 18px 32px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky;
    top: 0;
    z-index: 100;
  }
  .header-brand {
    display: flex;
    align-items: baseline;
    gap: 10px;
  }
  .header-brand h1 {
    font-family: 'DM Serif Display', serif;
    font-size: 22px;
    font-weight: 400;
    letter-spacing: -0.3px;
    color: #FAF8F5;
  }
  .header-brand span {
    font-size: 12px;
    color: #9E9894;
    text-transform: uppercase;
    letter-spacing: 1.5px;
  }
  .header-actions {
    display: flex;
    gap: 10px;
  }
  .btn-primary {
    background: var(--accent);
    color: white;
    border: none;
    border-radius: 8px;
    padding: 9px 18px;
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    font-weight: 500;
    cursor: pointer;
    transition: background 0.15s;
  }
  .btn-primary:hover { background: var(--accent-dark); }
  .btn-secondary {
    background: transparent;
    color: #FAF8F5;
    border: 1px solid #3A3734;
    border-radius: 8px;
    padding: 9px 18px;
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    cursor: pointer;
    transition: border-color 0.15s;
  }
  .btn-secondary:hover { border-color: #6B6460; }

  /* LAYOUT */
  .app {
    display: grid;
    grid-template-columns: 300px 1fr;
    min-height: calc(100vh - 57px);
  }

  /* SIDEBAR */
  .sidebar {
    background: var(--surface);
    border-right: 1px solid var(--border);
    padding: 20px;
    overflow-y: auto;
  }

  /* MINI CALENDAR */
  .mini-cal {
    margin-bottom: 24px;
  }
  .mini-cal-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 12px;
  }
  .mini-cal-header h3 {
    font-family: 'DM Serif Display', serif;
    font-size: 16px;
    font-weight: 400;
    color: var(--text);
  }
  .cal-nav {
    background: none;
    border: none;
    cursor: pointer;
    color: var(--text2);
    font-size: 16px;
    padding: 4px 8px;
    border-radius: 6px;
    transition: background 0.12s;
  }
  .cal-nav:hover { background: var(--surface2); }
  .cal-grid {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 2px;
  }
  .cal-day-name {
    text-align: center;
    font-size: 10px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    color: var(--text3);
    padding: 4px 0;
  }
  .cal-day {
    aspect-ratio: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 12px;
    border-radius: 6px;
    cursor: pointer;
    color: var(--text);
    transition: background 0.12s;
    position: relative;
  }
  .cal-day:hover { background: var(--surface2); }
  .cal-day.empty { cursor: default; }
  .cal-day.today {
    background: var(--accent-light);
    color: var(--accent);
    font-weight: 600;
  }
  .cal-day.selected {
    background: var(--text);
    color: white;
  }
  .cal-day.has-reservas::after {
    content: '';
    position: absolute;
    bottom: 3px;
    left: 50%;
    transform: translateX(-50%);
    width: 4px;
    height: 4px;
    border-radius: 50%;
    background: var(--accent);
  }
  .cal-day.selected.has-reservas::after {
    background: white;
  }

  /* STATS */
  .stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
    margin-bottom: 24px;
  }
  .stat-card {
    background: var(--surface2);
    border-radius: var(--radius);
    padding: 12px;
  }
  .stat-card .num {
    font-family: 'DM Serif Display', serif;
    font-size: 24px;
    line-height: 1;
    margin-bottom: 3px;
    color: var(--text);
  }
  .stat-card .label {
    font-size: 11px;
    color: var(--text2);
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  /* UPCOMING */
  .sidebar-section h4 {
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: var(--text3);
    margin-bottom: 10px;
  }
  .upcoming-item {
    padding: 10px;
    background: var(--bg);
    border-radius: 8px;
    margin-bottom: 6px;
    cursor: pointer;
    transition: background 0.12s;
    border: 1px solid transparent;
  }
  .upcoming-item:hover { background: var(--accent-light); border-color: var(--border); }
  .upcoming-item .ui-name { font-weight: 500; font-size: 13px; margin-bottom: 2px; }
  .upcoming-item .ui-info { font-size: 11px; color: var(--text2); }
  .upcoming-empty { font-size: 12px; color: var(--text3); padding: 8px 0; }

  /* MAIN */
  .main {
    padding: 24px;
    overflow-y: auto;
  }

  /* TOOLBAR */
  .toolbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
    flex-wrap: wrap;
    gap: 10px;
  }
  .toolbar-left h2 {
    font-family: 'DM Serif Display', serif;
    font-size: 20px;
    font-weight: 400;
    color: var(--text);
  }
  .toolbar-left .sub {
    font-size: 12px;
    color: var(--text2);
    margin-top: 2px;
  }
  .toolbar-right {
    display: flex;
    gap: 8px;
    align-items: center;
  }
  .filter-select {
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 8px 12px;
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    background: var(--surface);
    color: var(--text);
    cursor: pointer;
  }
  .search-input {
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 8px 12px;
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    background: var(--surface);
    color: var(--text);
    width: 200px;
  }
  .search-input::placeholder { color: var(--text3); }
  .search-input:focus, .filter-select:focus { outline: 2px solid var(--accent); outline-offset: 1px; }

  /* TABLA */
  .table-wrap {
    background: var(--surface);
    border-radius: 12px;
    border: 1px solid var(--border);
    overflow: hidden;
    box-shadow: var(--shadow);
  }
  table {
    width: 100%;
    border-collapse: collapse;
  }
  thead th {
    text-align: left;
    padding: 12px 16px;
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.8px;
    color: var(--text3);
    background: var(--bg);
    border-bottom: 1px solid var(--border);
  }
  tbody tr {
    border-bottom: 1px solid var(--border);
    transition: background 0.1s;
    cursor: pointer;
  }
  tbody tr:last-child { border-bottom: none; }
  tbody tr:hover { background: var(--accent-light); }
  tbody td {
    padding: 13px 16px;
    font-size: 13px;
    color: var(--text);
  }
  .td-name { font-weight: 500; }
  .td-date { color: var(--text2); }
  .td-contact { color: var(--text2); font-size: 12px; }

  /* BADGES */
  .badge {
    display: inline-flex;
    align-items: center;
    padding: 3px 9px;
    border-radius: 20px;
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  .badge-confirmed { background: var(--green-light); color: var(--green); }
  .badge-pending { background: var(--amber-light); color: var(--amber); }
  .badge-cancelled { background: var(--red-light); color: var(--red); }
  .badge-paid { background: var(--blue-light); color: var(--blue); }

  .tipo-badge {
    display: inline-flex;
    padding: 3px 9px;
    border-radius: 20px;
    font-size: 11px;
    background: var(--surface2);
    color: var(--text2);
  }

  .actions-cell {
    display: flex;
    gap: 6px;
  }
  .btn-icon {
    background: none;
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 5px 8px;
    cursor: pointer;
    font-size: 13px;
    color: var(--text2);
    transition: all 0.12s;
  }
  .btn-icon:hover { background: var(--surface2); }
  .btn-icon.del:hover { background: var(--red-light); border-color: var(--red); color: var(--red); }

  .empty-state {
    padding: 48px 24px;
    text-align: center;
    color: var(--text3);
  }
  .empty-state .icon { font-size: 32px; margin-bottom: 10px; }
  .empty-state p { font-size: 14px; }

  /* MODAL */
  .modal-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.4);
    z-index: 200;
    align-items: center;
    justify-content: center;
    padding: 20px;
  }
  .modal-overlay.open { display: flex; }
  .modal {
    background: var(--surface);
    border-radius: 14px;
    width: 100%;
    max-width: 520px;
    max-height: 90vh;
    overflow-y: auto;
    box-shadow: 0 8px 40px rgba(0,0,0,0.18);
    animation: modal-in 0.18s ease;
  }
  @keyframes modal-in {
    from { transform: translateY(12px); opacity: 0; }
    to { transform: translateY(0); opacity: 1; }
  }
  .modal-header {
    padding: 20px 24px 16px;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .modal-header h3 {
    font-family: 'DM Serif Display', serif;
    font-size: 18px;
    font-weight: 400;
  }
  .modal-close {
    background: none;
    border: none;
    font-size: 20px;
    cursor: pointer;
    color: var(--text3);
    line-height: 1;
    padding: 4px;
  }
  .modal-body { padding: 20px 24px; }
  .modal-footer {
    padding: 16px 24px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: flex-end;
    gap: 10px;
  }

  /* FORM */
  .form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
    margin-bottom: 14px;
  }
  .form-row.single { grid-template-columns: 1fr; }
  .form-group { display: flex; flex-direction: column; gap: 5px; }
  .form-group label {
    font-size: 12px;
    font-weight: 500;
    color: var(--text2);
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  .form-group input,
  .form-group select,
  .form-group textarea {
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 9px 12px;
    font-family: 'DM Sans', sans-serif;
    font-size: 14px;
    background: var(--surface);
    color: var(--text);
    transition: border-color 0.12s;
  }
  .form-group input:focus,
  .form-group select:focus,
  .form-group textarea:focus {
    outline: none;
    border-color: var(--accent);
  }
  .form-group textarea { resize: vertical; min-height: 70px; }
  .form-separator {
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: var(--text3);
    margin: 18px 0 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .form-separator::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* DETAIL MODAL */
  .detail-section { margin-bottom: 20px; }
  .detail-section h4 {
    font-size: 11px;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.8px;
    color: var(--text3);
    margin-bottom: 10px;
  }
  .detail-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }
  .detail-item { }
  .detail-item .di-label {
    font-size: 11px;
    color: var(--text3);
    text-transform: uppercase;
    letter-spacing: 0.5px;
    margin-bottom: 2px;
  }
  .detail-item .di-value {
    font-size: 14px;
    color: var(--text);
    font-weight: 400;
  }
  .detail-notes {
    background: var(--bg);
    border-radius: 8px;
    padding: 12px;
    font-size: 13px;
    color: var(--text2);
    line-height: 1.6;
  }
  .status-buttons {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
  }
  .status-btn {
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 8px 14px;
    font-family: 'DM Sans', sans-serif;
    font-size: 12px;
    font-weight: 500;
    cursor: pointer;
    background: var(--surface);
    color: var(--text2);
    transition: all 0.12s;
  }
  .status-btn:hover { border-color: var(--accent); color: var(--accent); }
  .status-btn.active { background: var(--text); color: white; border-color: var(--text); }

  /* TOAST */
  .toast {
    position: fixed;
    bottom: 24px;
    right: 24px;
    background: var(--text);
    color: #FAF8F5;
    padding: 12px 18px;
    border-radius: 10px;
    font-size: 13px;
    z-index: 999;
    display: none;
    animation: toast-in 0.2s ease;
    box-shadow: 0 4px 20px rgba(0,0,0,0.2);
  }
  @keyframes toast-in {
    from { transform: translateY(10px); opacity: 0; }
    to { transform: translateY(0); opacity: 1; }
  }

  .no-results { padding: 32px; text-align: center; color: var(--text3); font-size: 13px; }
  @keyframes loadpulse { from { opacity:0.5 } to { opacity:1 } }
</style>
</head>
<body>

<header>
  <div class="header-brand">
    <h1>☕ Mis Reservas</h1>
    <span>Cafetería</span>
  </div>
  <div class="header-actions">
    <button class="btn-secondary" onclick="refreshData()" title="Actualizar">↻ Actualizar</button>
    <button class="btn-secondary" onclick="exportCSV()">↓ Exportar</button>
    <button class="btn-primary" onclick="openNew()">+ Nueva reserva</button>
  </div>
</header>
<div id="loadingBar" style="display:none;height:3px;background:var(--accent);position:sticky;top:57px;z-index:99;animation:loadpulse 1s infinite alternate">
</div>

<div class="app">
  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="mini-cal">
      <div class="mini-cal-header">
        <h3 id="calTitle"></h3>
        <div>
          <button class="cal-nav" onclick="changeMonth(-1)">‹</button>
          <button class="cal-nav" onclick="changeMonth(1)">›</button>
        </div>
      </div>
      <div class="cal-grid" id="calGrid"></div>
    </div>

    <div class="stats-grid">
      <div class="stat-card">
        <div class="num" id="statTotal">0</div>
        <div class="label">Total mes</div>
      </div>
      <div class="stat-card">
        <div class="num" id="statHoy">0</div>
        <div class="label">Hoy</div>
      </div>
      <div class="stat-card">
        <div class="num" id="statPendiente">0</div>
        <div class="label">Pendientes</div>
      </div>
      <div class="stat-card">
        <div class="num" id="statPersonas">0</div>
        <div class="label">Personas mes</div>
      </div>
    </div>

    <div class="sidebar-section">
      <h4>Próximas reservas</h4>
      <div id="upcomingList"></div>
    </div>
  </aside>

  <!-- MAIN -->
  <main class="main">
    <div class="toolbar">
      <div class="toolbar-left">
        <h2 id="mainTitle">Todas las reservas</h2>
        <div class="sub" id="mainSub"></div>
      </div>
      <div class="toolbar-right">
        <input class="search-input" type="text" placeholder="Buscar por nombre..." id="searchInput" oninput="renderTable()">
        <select class="filter-select" id="filterEstado" onchange="renderTable()">
          <option value="">Todos los estados</option>
          <option value="confirmada">Confirmada</option>
          <option value="pendiente">Pendiente</option>
          <option value="cancelada">Cancelada</option>
        </select>
        <select class="filter-select" id="filterTipo" onchange="renderTable()">
          <option value="">Todos los tipos</option>
          <option value="reunion">Reunión</option>
          <option value="cumpleanos">Cumpleaños</option>
          <option value="evento">Evento</option>
          <option value="otro">Otro</option>
        </select>
      </div>
    </div>

    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>Cliente</th>
            <th>Fecha & Horario</th>
            <th>Tipo</th>
            <th>Personas</th>
            <th>Estado</th>
            <th>Acciones</th>
          </tr>
        </thead>
        <tbody id="tableBody"></tbody>
      </table>
      <div id="emptyState" class="empty-state" style="display:none">
        <div class="icon">📋</div>
        <p>No hay reservas. ¡Crea la primera!</p>
      </div>
      <div id="noResults" class="no-results" style="display:none">Sin resultados para esa búsqueda.</div>
    </div>
  </main>
</div>

<!-- MODAL NUEVA/EDITAR -->
<div class="modal-overlay" id="formModal">
  <div class="modal">
    <div class="modal-header">
      <h3 id="modalTitle">Nueva reserva</h3>
      <button class="modal-close" onclick="closeModal('formModal')">×</button>
    </div>
    <div class="modal-body">
      <div class="form-separator">Datos del cliente</div>
      <div class="form-row">
        <div class="form-group">
          <label>Nombre *</label>
          <input type="text" id="fNombre" placeholder="Ej: María González">
        </div>
        <div class="form-group">
          <label>Teléfono / WhatsApp</label>
          <input type="text" id="fTelefono" placeholder="+56 9 ...">
        </div>
      </div>

      <div class="form-separator">Detalles de la reserva</div>
      <div class="form-row">
        <div class="form-group">
          <label>Fecha *</label>
          <input type="date" id="fFecha">
        </div>
        <div class="form-group" style="display:grid;grid-template-columns:1fr 1fr;gap:8px;align-items:end">
          <div>
            <label style="font-size:12px;font-weight:500;color:var(--text2);text-transform:uppercase;letter-spacing:0.5px;display:block;margin-bottom:5px">Hora inicio *</label>
            <div style="display:flex;gap:4px;align-items:center">
              <select id="fHoraH" style="flex:1;border:1px solid var(--border);border-radius:8px;padding:9px 8px;font-family:'DM Sans',sans-serif;font-size:14px;background:var(--surface);color:var(--text)"></select>
              <span style="color:var(--text2);font-weight:600">:</span>
              <select id="fHoraM" style="flex:1;border:1px solid var(--border);border-radius:8px;padding:9px 8px;font-family:'DM Sans',sans-serif;font-size:14px;background:var(--surface);color:var(--text)"></select>
            </div>
          </div>
          <div>
            <label style="font-size:12px;font-weight:500;color:var(--text2);text-transform:uppercase;letter-spacing:0.5px;display:block;margin-bottom:5px">Hora término</label>
            <div style="display:flex;gap:4px;align-items:center">
              <select id="fHoraFinH" style="flex:1;border:1px solid var(--border);border-radius:8px;padding:9px 8px;font-family:'DM Sans',sans-serif;font-size:14px;background:var(--surface);color:var(--text)"></select>
              <span style="color:var(--text2);font-weight:600">:</span>
              <select id="fHoraFinM" style="flex:1;border:1px solid var(--border);border-radius:8px;padding:9px 8px;font-family:'DM Sans',sans-serif;font-size:14px;background:var(--surface);color:var(--text)"></select>
            </div>
          </div>
        </div>
      </div>
      <div class="form-row">
        <div class="form-group">
          <label>Tipo de evento</label>
          <select id="fTipo">
            <option value="reunion">Reunión</option>
            <option value="cumpleanos">Cumpleaños</option>
            <option value="evento">Evento</option>
            <option value="otro">Otro</option>
          </select>
        </div>
        <div class="form-group">
          <label>N° de personas</label>
          <input type="number" id="fPersonas" placeholder="Ej: 10" min="1">
        </div>
      </div>

      <div class="form-separator">Estado</div>
      <div class="form-row">
        <div class="form-group">
          <label>Estado reserva</label>
          <select id="fEstado">
            <option value="pendiente">Pendiente</option>
            <option value="confirmada">Confirmada</option>
            <option value="cancelada">Cancelada</option>
          </select>
        </div>
        <div class="form-group"></div>
      </div>
      <div class="form-row single">
        <div class="form-group">
          <label>Notas adicionales</label>
          <textarea id="fNotas" placeholder="Detalles del evento, preferencias, requerimientos..."></textarea>
        </div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn-secondary" style="color:var(--text);border-color:var(--border)" onclick="closeModal('formModal')">Cancelar</button>
      <button class="btn-primary" onclick="saveReserva()">Guardar reserva</button>
    </div>
  </div>
</div>

<!-- MODAL DETALLE -->
<div class="modal-overlay" id="detailModal">
  <div class="modal">
    <div class="modal-header">
      <h3 id="detailName"></h3>
      <button class="modal-close" onclick="closeModal('detailModal')">×</button>
    </div>
    <div class="modal-body" id="detailBody"></div>
    <div class="modal-footer">
      <button class="btn-secondary" style="color:var(--red);border-color:var(--red)" onclick="deleteFromDetail()">Eliminar</button>
      <button class="btn-secondary" style="color:var(--text);border-color:var(--border)" onclick="closeModal('detailModal')">Cerrar</button>
      <button class="btn-primary" onclick="editFromDetail()">Editar</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
const GS_URL = 'https://script.google.com/macros/s/AKfycbzOqM-SF2iiOjYi8kPfxv_TtipbD6mtAmwT6NggTlIa1XKbKwU2o3OC3K672f1-YXRW/exec';
let reservas = [];
let editingId = null;
let detailId = null;
let calYear, calMonth, selectedDate = null;

const today = new Date();

function buildTimeSelects() {
  const hIds = ['fHoraH','fHoraFinH'];
  const mIds = ['fHoraM','fHoraFinM'];
  hIds.forEach(id => {
    const sel = document.getElementById(id);
    sel.innerHTML = '<option value="">HH</option>';
    for(let h=0;h<24;h++) {
      const v = String(h).padStart(2,'0');
      sel.innerHTML += `<option value="${v}">${v}</option>`;
    }
  });
  mIds.forEach(id => {
    const sel = document.getElementById(id);
    sel.innerHTML = '<option value="">MM</option>';
    ['00','15','30','45'].forEach(m => {
      sel.innerHTML += `<option value="${m}">${m}</option>`;
    });
  });
}

function setTime(hId, mId, timeStr) {
  if(!timeStr) {
    document.getElementById(hId).value = '';
    document.getElementById(mId).value = '';
    return;
  }
  const [h,m] = timeStr.split(':');
  document.getElementById(hId).value = h||'';
  const mSel = document.getElementById(mId);
  const mRound = ['00','15','30','45'].reduce((a,b) => Math.abs(parseInt(b)-parseInt(m||0)) < Math.abs(parseInt(a)-parseInt(m||0)) ? b : a);
  mSel.value = mRound;
}

function getTime(hId, mId) {
  const h = document.getElementById(hId).value;
  const m = document.getElementById(mId).value;
  if(!h || h==='HH') return '';
  return `${h}:${m||'00'}`;
}


async function init() {
  buildTimeSelects();
  calYear = today.getFullYear();
  calMonth = today.getMonth();
  renderCalendar();
  renderTable();
  renderSidebar();
  await loadData();
  renderCalendar();
  renderTable();
  renderSidebar();
}

function normalizeFecha(fecha) {
  if (!fecha) return '';
  const s = String(fecha).trim();
  // Already YYYY-MM-DD
  if (/^\d{4}-\d{2}-\d{2}$/.test(s)) return s;
  // DD-MM-YYYY or DD/MM/YYYY
  const m1 = s.match(/^(\d{1,2})[-\/](\d{1,2})[-\/](\d{4})$/);
  if (m1) return `${m1[3]}-${m1[2].padStart(2,'0')}-${m1[1].padStart(2,'0')}`;
  // MM/DD/YYYY (formato americano)
  const m2 = s.match(/^(\d{1,2})\/(\d{1,2})\/(\d{4})$/);
  if (m2) return `${m2[3]}-${m2[1].padStart(2,'0')}-${m2[2].padStart(2,'0')}`;
  // Try native Date parse as fallback
  try {
    const d = new Date(s);
    if (!isNaN(d)) return d.toISOString().split('T')[0];
  } catch(e) {}
  return s;
}


async function loadData() {
  showLoading(true);
  try {
    const res = await fetch(GS_URL);
    const raw = await res.json();
    if (Array.isArray(raw)) {
      reservas = raw.map(r => ({
        ...r,
        fecha: normalizeFecha(r.fecha),
        personas: parseInt(r.personas)||0,
        deposito: parseInt(r.deposito)||0,
      })).filter(r => r.id);
    }
  } catch(e) {
    showToast('⚠️ No se pudo conectar con Google Sheets.');
  }
  showLoading(false);
}

async function save(reserva) {
  try {
    await fetch(GS_URL, {
      method: 'POST',
      body: JSON.stringify({ action: 'save', data: reserva }),
    });
  } catch(e) {
    showToast('⚠️ Error al guardar. Revisa la conexión.');
  }
}

async function deleteRemote(id) {
  try {
    await fetch(GS_URL, {
      method: 'POST',
      body: JSON.stringify({ action: 'delete', id: String(id) }),
    });
  } catch(e) {
    showToast('⚠️ Error al eliminar. Revisa la conexión.');
  }
}

async function refreshData() {
  await loadData();
  renderCalendar();
  renderTable();
  renderSidebar();
  showToast('🔄 Datos actualizados');
}


function showLoading(on) {
  document.getElementById('loadingBar').style.display = on ? 'block' : 'none';
}

// ====== CALENDAR ======
function renderCalendar() {
  const months = ['Enero','Febrero','Marzo','Abril','Mayo','Junio','Julio','Agosto','Septiembre','Octubre','Noviembre','Diciembre'];
  document.getElementById('calTitle').textContent = `${months[calMonth]} ${calYear}`;
  const grid = document.getElementById('calGrid');
  grid.innerHTML = '';
  const days = ['D','L','M','M','J','V','S'];
  days.forEach(d => { const el = document.createElement('div'); el.className = 'cal-day-name'; el.textContent = d; grid.appendChild(el); });
  const first = new Date(calYear, calMonth, 1).getDay();
  const total = new Date(calYear, calMonth+1, 0).getDate();
  for(let i=0;i<first;i++) { const el = document.createElement('div'); el.className='cal-day empty'; grid.appendChild(el); }
  const reservasDates = new Set(reservas.filter(r=>r.estado!=='cancelada').map(r=>r.fecha));
  for(let d=1;d<=total;d++) {
    const el = document.createElement('div');
    el.className = 'cal-day';
    el.textContent = d;
    const dateStr = `${calYear}-${String(calMonth+1).padStart(2,'0')}-${String(d).padStart(2,'0')}`;
    if(reservasDates.has(dateStr)) el.classList.add('has-reservas');
    if(dateStr === today.toISOString().split('T')[0]) el.classList.add('today');
    if(dateStr === selectedDate) el.classList.add('selected');
    el.addEventListener('click', () => selectDate(dateStr));
    grid.appendChild(el);
  }
}

function changeMonth(dir) {
  calMonth += dir;
  if(calMonth>11){calMonth=0;calYear++;}
  if(calMonth<0){calMonth=11;calYear--;}
  renderCalendar();
}

function selectDate(dateStr) {
  if(selectedDate === dateStr) {
    selectedDate = null;
  } else {
    selectedDate = dateStr;
  }
  renderCalendar();
  renderTable();
  if(selectedDate) {
    const parts = selectedDate.split('-');
    document.getElementById('mainTitle').textContent = `Reservas del ${parseInt(parts[2])} de ${['enero','febrero','marzo','abril','mayo','junio','julio','agosto','septiembre','octubre','noviembre','diciembre'][parseInt(parts[1])-1]}`;
  } else {
    document.getElementById('mainTitle').textContent = 'Todas las reservas';
  }
}

// ====== SIDEBAR ======
function renderSidebar() {
  const todayStr = today.toISOString().split('T')[0];
  const thisMonthStr = `${today.getFullYear()}-${String(today.getMonth()+1).padStart(2,'0')}`;
  const mesReservas = reservas.filter(r => r.fecha.startsWith(thisMonthStr) && r.estado !== 'cancelada');
  document.getElementById('statTotal').textContent = mesReservas.length;
  document.getElementById('statHoy').textContent = reservas.filter(r=>r.fecha===todayStr&&r.estado!=='cancelada').length;
  document.getElementById('statPendiente').textContent = reservas.filter(r=>r.estado==='pendiente').length;
  document.getElementById('statPersonas').textContent = mesReservas.reduce((a,r)=>a+(parseInt(r.personas)||0),0);

  const upcoming = reservas
    .filter(r => r.fecha >= todayStr && r.estado !== 'cancelada')
    .sort((a,b) => (a.fecha+a.hora).localeCompare(b.fecha+b.hora))
    .slice(0,5);
  const ul = document.getElementById('upcomingList');
  if(upcoming.length === 0) {
    ul.innerHTML = '<div class="upcoming-empty">No hay reservas próximas.</div>';
  } else {
    ul.innerHTML = upcoming.map(r => `
      <div class="upcoming-item" onclick="openDetail(${r.id})">
        <div class="ui-name">${r.nombre}</div>
        <div class="ui-info">${formatDate(r.fecha)} · ${r.hora}${r.horaFin?' → '+r.horaFin:''} · ${r.personas||'?'} personas</div>
      </div>
    `).join('');
  }
}

// ====== TABLE ======
function renderTable() {
  const search = document.getElementById('searchInput').value.toLowerCase();
  const filterE = document.getElementById('filterEstado').value;
  const filterT = document.getElementById('filterTipo').value;

  let data = [...reservas];
  if(selectedDate) data = data.filter(r => r.fecha === selectedDate);
  if(search) data = data.filter(r => r.nombre.toLowerCase().includes(search) || (r.telefono||'').includes(search));
  if(filterE) data = data.filter(r => r.estado === filterE);
  if(filterT) data = data.filter(r => r.tipo === filterT);
  data.sort((a,b) => (a.fecha+a.hora).localeCompare(b.fecha+b.hora));

  const sub = document.getElementById('mainSub');
  sub.textContent = data.length === 1 ? '1 reserva' : `${data.length} reservas`;

  const tbody = document.getElementById('tableBody');
  const empty = document.getElementById('emptyState');
  const noRes = document.getElementById('noResults');

  if(reservas.length === 0) {
    tbody.innerHTML = '';
    empty.style.display = 'block';
    noRes.style.display = 'none';
    return;
  }
  empty.style.display = 'none';
  if(data.length === 0) {
    tbody.innerHTML = '';
    noRes.style.display = 'block';
    return;
  }
  noRes.style.display = 'none';

  tbody.innerHTML = data.map(r => `
    <tr onclick="openDetail(${r.id})">
      <td>
        <div class="td-name">${r.nombre}</div>
        <div class="td-contact">${r.telefono||''}</div>
      </td>
      <td class="td-date">${formatDate(r.fecha)}<br><small>${r.hora}${r.horaFin?' → '+r.horaFin:''}</small></td>
      <td><span class="tipo-badge">${tipoLabel(r.tipo)}</span></td>
      <td>${r.personas||'—'}</td>
      <td>${estadoBadge(r.estado)}</td>
      <td onclick="event.stopPropagation()">
        <div class="actions-cell">
          <button class="btn-icon" onclick="openEdit(${r.id})" title="Editar">✏️</button>
          <button class="btn-icon del" onclick="deleteReserva(${r.id})" title="Eliminar">🗑️</button>
        </div>
      </td>
    </tr>
  `).join('');
}

// ====== MODAL FORM ======
function openNew() {
  editingId = null;
  document.getElementById('modalTitle').textContent = 'Nueva reserva';
  document.getElementById('fNombre').value = '';
  document.getElementById('fTelefono').value = '';
  document.getElementById('fFecha').value = selectedDate || today.toISOString().split('T')[0];
  setTime('fHoraH','fHoraM','');
  setTime('fHoraFinH','fHoraFinM','');
  document.getElementById('fTipo').value = 'reunion';
  document.getElementById('fPersonas').value = '';
  document.getElementById('fEstado').value = 'pendiente';
  document.getElementById('fNotas').value = '';
  document.getElementById('formModal').classList.add('open');
}

function openEdit(id) {
  const r = reservas.find(x=>x.id===id);
  if(!r) return;
  editingId = id;
  document.getElementById('modalTitle').textContent = 'Editar reserva';
  document.getElementById('fNombre').value = r.nombre||'';
  document.getElementById('fTelefono').value = r.telefono||'';
  document.getElementById('fFecha').value = r.fecha||'';
  setTime('fHoraH','fHoraM', r.hora||'');
  setTime('fHoraFinH','fHoraFinM', r.horaFin||'');
  document.getElementById('fTipo').value = r.tipo||'reunion';
  document.getElementById('fPersonas').value = r.personas||'';
  document.getElementById('fEstado').value = r.estado||'pendiente';
  document.getElementById('fNotas').value = r.notas||'';
  document.getElementById('formModal').classList.add('open');
}

async function saveReserva() {
  const nombre = document.getElementById('fNombre').value.trim();
  const fecha = document.getElementById('fFecha').value;
  const hora = getTime('fHoraH','fHoraM');
  if(!nombre||!fecha||!hora) { showToast('⚠️ Completa nombre, fecha y hora'); return; }

  const data = {
    nombre, fecha, hora,
    horaFin: getTime('fHoraFinH','fHoraFinM'),
    telefono: document.getElementById('fTelefono').value.trim(),
    tipo: document.getElementById('fTipo').value,
    personas: parseInt(document.getElementById('fPersonas').value)||0,
    deposito: 0,
    estadoPago: '',
    estado: document.getElementById('fEstado').value,
    notas: document.getElementById('fNotas').value.trim(),
  };

  if(editingId) {
    const idx = reservas.findIndex(x=>x.id===editingId);
    reservas[idx] = { ...reservas[idx], ...data };
    showToast('💾 Guardando...');
    await save(reservas[idx]);
    showToast('✅ Reserva actualizada');
  } else {
    data.id = Date.now();
    reservas.push(data);
    showToast('💾 Guardando...');
    await save(data);
    showToast('✅ Reserva guardada');
  }
  closeModal('formModal');
  renderCalendar();
  renderTable();
  renderSidebar();
}

// ====== DETAIL ======
function openDetail(id) {
  const r = reservas.find(x=>x.id===id);
  if(!r) return;
  detailId = id;
  document.getElementById('detailName').textContent = r.nombre;
  const body = document.getElementById('detailBody');
  body.innerHTML = `
    <div class="detail-section">
      <h4>Evento</h4>
      <div class="detail-grid">
        <div class="detail-item"><div class="di-label">Fecha</div><div class="di-value">${formatDate(r.fecha)}</div></div>
        <div class="detail-item"><div class="di-label">Hora inicio</div><div class="di-value">${r.hora}</div></div>
        <div class="detail-item"><div class="di-label">Hora término</div><div class="di-value">${r.horaFin||'—'}</div></div>
        <div class="detail-item"><div class="di-label">Tipo</div><div class="di-value">${tipoLabel(r.tipo)}</div></div>
        <div class="detail-item"><div class="di-label">Personas</div><div class="di-value">${r.personas||'—'}</div></div>
      </div>
    </div>
    <div class="detail-section">
      <h4>Cliente</h4>
      <div class="detail-grid">
        <div class="detail-item"><div class="di-label">Teléfono</div><div class="di-value">${r.telefono||'—'}</div></div>
        <div class="detail-item"></div>
      </div>
    </div>
    ${r.notas?`<div class="detail-section"><h4>Notas</h4><div class="detail-notes">${r.notas}</div></div>`:''}
    <div class="detail-section">
      <h4>Cambiar estado</h4>
      <div class="status-buttons">
        <button class="status-btn ${r.estado==='pendiente'?'active':''}" onclick="changeStatus(${r.id},'pendiente')">Pendiente</button>
        <button class="status-btn ${r.estado==='confirmada'?'active':''}" onclick="changeStatus(${r.id},'confirmada')">Confirmada</button>
        <button class="status-btn ${r.estado==='cancelada'?'active':''}" onclick="changeStatus(${r.id},'cancelada')">Cancelada</button>
      </div>
    </div>
  `;
  document.getElementById('detailModal').classList.add('open');
}

async function changeStatus(id, estado) {
  const r = reservas.find(x=>x.id===id);
  if(r) {
    r.estado = estado;
    await save(r);
    renderCalendar();
    renderTable();
    renderSidebar();
    openDetail(id);
    showToast('Estado actualizado');
  }
}

function editFromDetail() {
  closeModal('detailModal');
  openEdit(detailId);
}

function deleteFromDetail() {
  if(confirm('¿Eliminar esta reserva?')) {
    deleteReserva(detailId);
    closeModal('detailModal');
  }
}

async function deleteReserva(id) {
  reservas = reservas.filter(x=>x.id!==id);
  await deleteRemote(id);
  renderCalendar();
  renderTable();
  renderSidebar();
  showToast('🗑️ Reserva eliminada');
}

// ====== EXPORT ======
function exportCSV() {
  const headers = ['Nombre','Teléfono','Fecha','Hora Inicio','Hora Término','Tipo','Personas','Estado','Notas'];
  const rows = reservas.map(r => [
    r.nombre, r.telefono, r.fecha, r.hora, r.horaFin||'', tipoLabel(r.tipo), r.personas,
    r.estado, r.notas
  ].map(v => `"${(v||'').toString().replace(/"/g,'""')}"`).join(','));
  const csv = [headers.join(','), ...rows].join('\n');
  const a = document.createElement('a');
  a.href = 'data:text/csv;charset=utf-8,\uFEFF'+encodeURIComponent(csv);
  a.download = `reservas_${new Date().toISOString().split('T')[0]}.csv`;
  a.click();
  showToast('📥 Exportado como CSV');
}

// ====== UTILS ======
function closeModal(id) { document.getElementById(id).classList.remove('open'); }

function formatDate(str) {
  if(!str) return '';
  const [y,m,d] = str.split('-');
  const months = ['ene','feb','mar','abr','may','jun','jul','ago','sep','oct','nov','dic'];
  return `${parseInt(d)} ${months[parseInt(m)-1]} ${y}`;
}

function tipoLabel(t) {
  return {reunion:'Reunión',cumpleanos:'Cumpleaños',evento:'Evento',otro:'Otro'}[t]||t||'—';
}

function estadoBadge(e) {
  const map = { confirmada: 'badge-confirmed', pendiente: 'badge-pending', cancelada: 'badge-cancelled' };
  const labels = { confirmada: 'Confirmada', pendiente: 'Pendiente', cancelada: 'Cancelada' };
  return `<span class="badge ${map[e]||''}">${labels[e]||e}</span>`;
}


function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.style.display = 'block';
  setTimeout(()=>{ t.style.display='none'; }, 2500);
}

// Cerrar modal con click fuera
document.querySelectorAll('.modal-overlay').forEach(o => {
  o.addEventListener('click', e => { if(e.target === o) o.classList.remove('open'); });
});

init();
setInterval(async () => {
  await loadData();
  renderCalendar();
  renderTable();
  renderSidebar();
}, 2 * 60 * 1000);
</script>
</body>
</html>
