[index.html](https://github.com/user-attachments/files/28529547/index.html)
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>Innova Clean - Sistema de Control</title>
  <style>
    /* VARIABLES DE DISEÑO & CONFIGURACIÓN */
    :root {
      --primary: #00A3D7;
      --primary-hover: #0084B0;
      --primary-light: #e0f2fe;
      --primary-light-hover: #bae6fd;
      --text: #0f172a;
      --text-light: #475569;
      --bg: #f8fafc;
      --card-bg: #ffffff;
      --border: #cbd5e1;
      --border-focus: #00A3D7;
      --success: #10b981;
      --success-hover: #059669;
      --danger: #ef4444;
      --danger-hover: #dc2626;
      --warning: #f59e0b;
      --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
      --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.1);
      --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.1);
      --radius: 12px;
      --radius-lg: 16px;
    }

    /* RESET & ESTILOS GENERALES */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      background-color: var(--bg);
      color: var(--text);
      line-height: 1.5;
      padding: 16px;
      padding-bottom: 80px; /* Espacio para botones táctiles inferiores */
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
    }

    /* HEADER */
    header {
      background: linear-gradient(135deg, var(--primary) 0%, #00779d 100%);
      color: white;
      padding: 20px;
      border-radius: var(--radius-lg);
      margin-bottom: 20px;
      box-shadow: var(--shadow-md);
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .logo-container {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .logo-icon {
      width: 44px;
      height: 44px;
      background-color: rgba(255, 255, 255, 0.2);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 24px;
      box-shadow: var(--shadow-sm);
    }

    .logo-text h1 {
      font-size: 22px;
      font-weight: 800;
      letter-spacing: 0.5px;
      line-height: 1.1;
    }

    .logo-text span {
      font-size: 12px;
      opacity: 0.9;
    }

    .app-status {
      background-color: rgba(255, 255, 255, 0.15);
      padding: 6px 12px;
      border-radius: 20px;
      font-size: 12px;
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .app-status::before {
      content: '';
      display: inline-block;
      width: 8px;
      height: 8px;
      background-color: #4ade80;
      border-radius: 50%;
    }

    /* MENÚ DE PESTAÑAS (TABS) */
    .tabs-nav {
      display: flex;
      background-color: var(--card-bg);
      border-radius: var(--radius);
      padding: 6px;
      gap: 6px;
      margin-bottom: 20px;
      box-shadow: var(--shadow-sm);
      overflow-x: auto;
      white-space: nowrap;
      -webkit-overflow-scrolling: touch;
    }

    .tab-btn {
      flex: 1;
      min-width: 100px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      padding: 12px 16px;
      border: none;
      background-color: transparent;
      color: var(--text-light);
      font-weight: 600;
      font-size: 14px;
      border-radius: 8px;
      cursor: pointer;
      transition: all 0.2s ease;
      min-height: 48px;
    }

    .tab-btn:hover {
      background-color: var(--bg);
      color: var(--primary);
    }

    .tab-btn.active {
      background-color: var(--primary);
      color: white;
      box-shadow: var(--shadow-sm);
    }

    /* CONTENIDO DE PESTAÑAS */
    .tab-content {
      display: none;
    }

    .tab-content.active {
      display: block;
    }

    /* TARJETAS & CONTENEDORES */
    .card {
      background-color: var(--card-bg);
      border-radius: var(--radius);
      padding: 20px;
      box-shadow: var(--shadow-sm);
      margin-bottom: 20px;
      border: 1px solid rgba(226, 232, 240, 0.8);
    }

    .card-title {
      font-size: 16px;
      font-weight: 700;
      margin-bottom: 16px;
      color: var(--text);
      display: flex;
      align-items: center;
      gap: 8px;
      border-bottom: 2px solid var(--bg);
      padding-bottom: 8px;
    }

    /* GRID LAYOUTS */
    .grid-2 {
      display: grid;
      grid-template-columns: 1fr;
      gap: 20px;
    }

    @media (min-width: 768px) {
      .grid-2 {
        grid-template-columns: 1fr 1fr;
      }
    }

    .generator-layout {
      display: grid;
      grid-template-columns: 1fr;
      gap: 20px;
    }

    @media (min-width: 1024px) {
      .generator-layout {
        grid-template-columns: 360px 1fr;
      }
    }

    /* ALERTA DE MODO EDICIÓN */
    .edit-mode-alert {
      background-color: var(--primary-light);
      border: 1px solid var(--primary);
      color: var(--primary-hover);
      padding: 12px 16px;
      border-radius: var(--radius);
      margin-bottom: 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-weight: 600;
    }

    .btn-exit-edit {
      background-color: var(--primary);
      color: white;
      border: none;
      padding: 4px 8px;
      border-radius: 4px;
      cursor: pointer;
      font-size: 12px;
      font-weight: 700;
    }

    /* FORMULARIOS e INPUTS */
    .form-group {
      margin-bottom: 16px;
      position: relative;
    }

    .form-group label {
      display: block;
      font-size: 13px;
      font-weight: 600;
      color: var(--text-light);
      margin-bottom: 6px;
    }

    .input-control {
      width: 100%;
      padding: 12px 14px;
      border: 1px solid var(--border);
      border-radius: 8px;
      font-size: 14px;
      color: var(--text);
      background-color: var(--card-bg);
      outline: none;
      transition: all 0.2s ease;
      min-height: 48px;
    }

    .input-control:focus {
      border-color: var(--border-focus);
      box-shadow: 0 0 0 3px rgba(0, 163, 215, 0.15);
    }

    .input-control[readonly] {
      background-color: var(--bg);
      cursor: not-allowed;
    }

    textarea.input-control {
      min-height: 80px;
      resize: vertical;
    }

    /* AUTOCOMPLETE / DROPDOWNS */
    .autocomplete-container {
      position: relative;
    }

    .autocomplete-dropdown {
      position: absolute;
      top: 100%;
      left: 0;
      right: 0;
      background-color: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: 8px;
      max-height: 200px;
      overflow-y: auto;
      z-index: 100;
      box-shadow: var(--shadow-lg);
      margin-top: 4px;
    }

    .autocomplete-item {
      padding: 12px 14px;
      cursor: pointer;
      font-size: 14px;
      border-bottom: 1px solid var(--bg);
      transition: background-color 0.15s ease;
    }

    .autocomplete-item:last-child {
      border-bottom: none;
    }

    .autocomplete-item:hover {
      background-color: var(--primary-light);
      color: var(--primary-hover);
      font-weight: 600;
    }

    /* TABLA EDITABLE DE PRODUCTOS */
    .table-container {
      overflow-x: auto;
      margin-bottom: 20px;
      border-radius: 8px;
      border: 1px solid var(--border);
    }

    .doc-table {
      width: 100%;
      border-collapse: collapse;
      text-align: left;
      font-size: 14px;
    }

    .doc-table th {
      background-color: var(--bg);
      color: var(--text-light);
      font-weight: 700;
      padding: 12px;
      border-bottom: 2px solid var(--border);
      white-space: nowrap;
    }

    .doc-table td {
      padding: 8px 12px;
      border-bottom: 1px solid var(--border);
      vertical-align: middle;
    }

    .doc-table tbody tr:last-child td {
      border-bottom: none;
    }

    .doc-table th.col-qty, .doc-table td.col-qty {
      width: 80px;
    }

    .doc-table th.col-price, .doc-table td.col-price {
      width: 120px;
    }

    .doc-table th.col-total, .doc-table td.col-total {
      width: 120px;
      font-weight: 700;
    }

    .doc-table th.col-actions, .doc-table td.col-actions {
      width: 60px;
      text-align: center;
    }

    .col-qty input {
      text-align: center;
    }

    /* BOTONES */
    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      padding: 12px 20px;
      font-size: 14px;
      font-weight: 700;
      border-radius: 8px;
      border: none;
      cursor: pointer;
      transition: all 0.2s ease;
      min-height: 48px;
      text-decoration: none;
      box-shadow: var(--shadow-sm);
    }

    .btn:active {
      transform: scale(0.98);
    }

    .btn-block {
      display: flex;
      width: 100%;
    }

    .btn-primary {
      background-color: var(--primary);
      color: white;
    }

    .btn-primary:hover {
      background-color: var(--primary-hover);
    }

    .btn-secondary {
      background-color: var(--primary-light);
      color: var(--primary-hover);
    }

    .btn-secondary:hover {
      background-color: var(--primary-light-hover);
    }

    .btn-success {
      background-color: var(--success);
      color: white;
    }

    .btn-success:hover {
      background-color: var(--success-hover);
    }

    .btn-danger {
      background-color: var(--danger);
      color: white;
    }

    .btn-danger:hover {
      background-color: var(--danger-hover);
    }

    .btn-sm {
      min-height: 36px;
      padding: 6px 12px;
      font-size: 12px;
      border-radius: 6px;
    }

    .btn-action-delete {
      background-color: transparent;
      color: var(--danger);
      font-size: 18px;
      border: none;
      cursor: pointer;
      width: 36px;
      height: 36px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      transition: background-color 0.2s ease;
    }

    .btn-action-delete:hover {
      background-color: #fee2e2;
    }

    .btn-action-edit {
      background-color: transparent;
      color: var(--primary);
      font-size: 16px;
      border: none;
      cursor: pointer;
      width: 36px;
      height: 36px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      transition: background-color 0.2s ease;
    }

    .btn-action-edit:hover {
      background-color: var(--primary-light);
    }

    .action-buttons-group {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      margin-top: 20px;
    }

    .action-buttons-group .btn {
      flex: 1;
      min-width: 140px;
    }

    /* SECCIÓN DE TOTALES */
    .totals-box {
      margin-left: auto;
      max-width: 320px;
      background-color: var(--bg);
      border-radius: 8px;
      padding: 16px;
      border: 1px solid var(--border);
    }

    .total-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 12px;
      font-size: 14px;
    }

    .total-row:last-child {
      margin-bottom: 0;
      border-top: 2px solid var(--border);
      padding-top: 12px;
      font-weight: 800;
      font-size: 18px;
      color: var(--text);
    }

    .total-row input {
      width: 100px;
      text-align: right;
      min-height: 36px;
      padding: 6px;
    }

    /* BUSQUEDA / FILTROS */
    .search-bar {
      display: flex;
      gap: 12px;
      margin-bottom: 20px;
      flex-wrap: wrap;
    }

    .search-input {
      flex: 1;
      min-width: 200px;
    }

    /* HISTORIAL & LISTAS */
    .history-filters {
      display: grid;
      grid-template-columns: 1fr;
      gap: 12px;
      margin-bottom: 20px;
    }

    @media (min-width: 768px) {
      .history-filters {
        grid-template-columns: 2fr 1fr 1fr;
      }
    }

    .item-list-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 14px 16px;
      border-bottom: 1px solid var(--border);
      transition: background-color 0.15s ease;
    }

    .item-list-row:last-child {
      border-bottom: none;
    }

    .item-list-row:hover {
      background-color: var(--bg);
    }

    .item-info {
      flex: 1;
      margin-right: 12px;
    }

    .item-title {
      font-weight: 700;
      font-size: 15px;
      color: var(--text);
    }

    .item-subtitle {
      font-size: 13px;
      color: var(--text-light);
    }

    .item-actions {
      display: flex;
      gap: 6px;
    }

    /* ETIQUETAS */
    .badge {
      display: inline-block;
      padding: 4px 8px;
      font-size: 11px;
      font-weight: 700;
      border-radius: 4px;
      text-transform: uppercase;
    }

    .badge-quote {
      background-color: #dbeafe;
      color: #1e40af;
    }

    .badge-invoice {
      background-color: #d1fae5;
      color: #065f46;
    }

    /* MODAL DE VERSIONES Y CONFIRMACIONES */
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(15, 23, 42, 0.6);
      display: none;
      align-items: center;
      justify-content: center;
      padding: 20px;
      z-index: 1000;
      backdrop-filter: blur(4px);
    }

    .modal-overlay.active {
      display: flex;
    }

    .modal {
      background-color: var(--card-bg);
      border-radius: var(--radius-lg);
      width: 100%;
      max-width: 480px;
      box-shadow: var(--shadow-lg);
      overflow: hidden;
      animation: modalSlideUp 0.3s ease;
    }

    @keyframes modalSlideUp {
      from {
        transform: translateY(20px);
        opacity: 0;
      }
      to {
        transform: translateY(0);
        opacity: 1;
      }
    }

    .modal-header {
      background-color: var(--bg);
      padding: 16px 20px;
      font-weight: 700;
      font-size: 16px;
      border-bottom: 1px solid var(--border);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .modal-body {
      padding: 20px;
      font-size: 14px;
      color: var(--text-light);
    }

    .modal-body strong {
      color: var(--text);
    }

    .modal-footer {
      padding: 16px 20px;
      background-color: var(--bg);
      border-top: 1px solid var(--border);
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    /* NOTIFICACIONES TOAST */
    .toast-container {
      position: fixed;
      bottom: 24px;
      right: 24px;
      z-index: 1100;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .toast {
      background-color: #1e293b;
      color: white;
      padding: 14px 20px;
      border-radius: 8px;
      font-size: 14px;
      font-weight: 600;
      box-shadow: var(--shadow-lg);
      display: flex;
      align-items: center;
      gap: 10px;
      min-width: 250px;
      max-width: 380px;
      animation: toastSlideIn 0.3s ease, toastFadeOut 0.3s ease 2.7s forwards;
    }

    .toast.toast-success {
      border-left: 4px solid var(--success);
    }

    .toast.toast-error {
      border-left: 4px solid var(--danger);
    }

    @keyframes toastSlideIn {
      from {
        transform: translateX(100%);
        opacity: 0;
      }
      to {
        transform: translateX(0);
        opacity: 1;
      }
    }

    @keyframes toastFadeOut {
      from {
        opacity: 1;
      }
      to {
        opacity: 0;
      }
    }

    /* IMPRESIÓN SENSATA */
    .print-only {
      display: none;
    }

    @media print {
      body * {
        visibility: hidden;
      }
      
      .print-only, .print-only * {
        visibility: visible;
      }

      .print-only {
        display: block !important;
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
      }

      /* TAMAÑO CARTA */
      .print-letter {
        font-family: Arial, sans-serif;
        color: #000;
        padding: 40px 20px;
      }

      .print-letter .p-header {
        display: flex;
        justify-content: space-between;
        border-bottom: 3px solid #00A3D7;
        padding-bottom: 20px;
        margin-bottom: 30px;
      }

      .print-letter .p-logo {
        font-size: 28px;
        font-weight: 800;
        color: #00A3D7;
      }

      .print-letter .p-meta-title {
        font-size: 20px;
        font-weight: 800;
        text-align: right;
        margin-bottom: 4px;
      }

      .print-letter .p-meta-folio {
        font-size: 16px;
        font-weight: 700;
        text-align: right;
      }

      .print-letter .p-details-grid {
        display: grid;
        grid-template-columns: 2fr 1fr;
        gap: 40px;
        margin-bottom: 30px;
      }

      .print-letter .p-section-title {
        font-size: 12px;
        text-transform: uppercase;
        font-weight: 700;
        color: #64748b;
        margin-bottom: 6px;
        border-bottom: 1px solid #cbd5e1;
        padding-bottom: 4px;
      }

      .print-letter .p-table {
        width: 100%;
        border-collapse: collapse;
        margin-bottom: 30px;
      }

      .print-letter .p-table th {
        background-color: #f1f5f9;
        font-weight: 700;
        border-bottom: 2px solid #cbd5e1;
        padding: 10px;
        text-align: left;
      }

      .print-letter .p-table td {
        padding: 10px;
        border-bottom: 1px solid #cbd5e1;
      }

      .print-letter .p-totals {
        margin-left: auto;
        width: 250px;
        margin-bottom: 40px;
      }

      .print-letter .p-total-row {
        display: flex;
        justify-content: space-between;
        padding: 6px 0;
        font-size: 14px;
      }

      .print-letter .p-total-row.grand-total {
        font-size: 18px;
        font-weight: 800;
        border-top: 2px solid #00A3D7;
        padding-top: 8px;
      }

      /* TAMAÑO TICKET (80mm) */
      .print-ticket {
        font-family: 'Courier New', Courier, monospace;
        font-size: 12px;
        width: 76mm;
        margin: 0 auto;
        color: #000;
        padding: 5px;
      }

      .print-ticket .pt-center {
        text-align: center;
      }

      .print-ticket .pt-title {
        font-size: 18px;
        font-weight: 800;
        margin-bottom: 2px;
      }

      .print-ticket .pt-divider {
        border-top: 1px dashed #000;
        margin: 10px 0;
      }

      .print-ticket .pt-table {
        width: 100%;
        border-collapse: collapse;
        margin: 10px 0;
      }

      .print-ticket .pt-table th {
        border-bottom: 1px dashed #000;
        padding: 4px 0;
        text-align: left;
        font-size: 11px;
      }

      .print-ticket .pt-table td {
        padding: 4px 0;
        font-size: 11px;
      }

      .print-ticket .pt-totals {
        margin-left: auto;
        width: 180px;
        font-weight: 700;
      }

      .print-ticket .pt-total-row {
        display: flex;
        justify-content: space-between;
        padding: 2px 0;
      }
    }
  </style>
</head>
<body>

  <div class="container">
    
    <!-- HEADER -->
    <header>
      <div class="logo-container">
        <div class="logo-icon">✨</div>
        <div class="logo-text">
          <h1>INNOVA CLEAN</h1>
          <span>Control Administrativo Offline</span>
        </div>
      </div>
      <div class="app-status">Modo Local</div>
    </header>

    <!-- NAVEGACIÓN DE PESTAÑAS -->
    <nav class="tabs-nav">
      <button class="tab-btn active" onclick="switchTab('tab-generator')">📝 Documento</button>
      <button class="tab-btn" onclick="switchTab('tab-clients')">👥 Clientes</button>
      <button class="tab-btn" onclick="switchTab('tab-products')">📦 Productos</button>
      <button class="tab-btn" onclick="switchTab('tab-history')">📜 Historial</button>
    </nav>

    <!-- CONTENIDOS -->
    
    <!-- 1. PESTAÑA: GENERADOR -->
    <section id="tab-generator" class="tab-content active">
      
      <!-- Alerta Modo Edición -->
      <div id="edit-indicator" class="edit-mode-alert" style="display: none;">
        <span>⚠️ Editando documento guardado (Folio: <span id="edit-folio-text"></span>)</span>
        <button class="btn-exit-edit" onclick="exitEditMode()">Salir de edición</button>
      </div>

      <div class="generator-layout">
        
        <!-- Columna de Datos de Cabecera -->
        <div class="card">
          <h2 class="card-title">📝 Datos del Documento</h2>
          
          <div class="form-group">
            <label>Tipo de Documento</label>
            <div style="display: flex; gap: 10px;">
              <label style="flex: 1; display: flex; align-items: center; justify-content: center; gap: 8px; border: 1px solid var(--border); padding: 10px; border-radius: 8px; cursor: pointer; font-weight: 600;" id="label-type-cot">
                <input type="radio" name="doc-type" value="Cotización" checked onchange="updateDocTypeUI()"> Cotización
              </label>
              <label style="flex: 1; display: flex; align-items: center; justify-content: center; gap: 8px; border: 1px solid var(--border); padding: 10px; border-radius: 8px; cursor: pointer; font-weight: 600;" id="label-type-rem">
                <input type="radio" name="doc-type" value="Remisión" onchange="updateDocTypeUI()"> Remisión
              </label>
            </div>
          </div>

          <div class="form-group">
            <label>Folio Consecutivo</label>
            <input type="text" id="doc-folio" class="input-control" readonly>
          </div>

          <div class="form-group">
            <label>Fecha y Hora</label>
            <input type="text" id="doc-date" class="input-control" readonly>
          </div>

          <div style="border-top: 1px solid var(--border); padding-top: 16px; margin-top: 16px;">
            <h3 style="font-size: 14px; font-weight: 700; margin-bottom: 12px; color: var(--primary);">👤 Buscar o Registrar Cliente</h3>
            
            <div class="form-group autocomplete-container">
              <label>Cliente (Escribe para buscar)</label>
              <input type="text" id="doc-client" class="input-control" placeholder="Buscar o ingresar nombre..." autocomplete="off">
              <div id="client-autocomplete" class="autocomplete-dropdown" style="display: none;"></div>
            </div>

            <div class="form-group">
              <label>Teléfono</label>
              <input type="tel" id="doc-phone" class="input-control" placeholder="Teléfono del cliente">
            </div>

            <div class="form-group">
              <label>Dirección</label>
              <textarea id="doc-address" class="input-control" placeholder="Dirección del cliente"></textarea>
            </div>

            <button type="button" class="btn btn-secondary btn-block btn-sm" onclick="saveClientFromDoc()" style="margin-top: 4px;">
              💾 Guardar Cliente en Directorio
            </button>
          </div>

          <div class="form-group" style="margin-top: 16px; border-top: 1px solid var(--border); padding-top: 16px;">
            <label>Observaciones del Documento</label>
            <textarea id="doc-observations" class="input-control" placeholder="Ej. entrega a domicilio, pago contra entrega..."></textarea>
          </div>

        </div>

        <!-- Columna de Tabla de Productos -->
        <div class="card">
          <h2 class="card-title">📦 Conceptos del Documento</h2>
          
          <div class="table-container">
            <table class="doc-table" id="items-table">
              <thead>
                <tr>
                  <th class="col-qty">Cant.</th>
                  <th>Producto</th>
                  <th class="col-price">P. Unit. ($)</th>
                  <th class="col-total">Importe ($)</th>
                  <th class="col-actions"></th>
                </tr>
              </thead>
              <tbody id="items-tbody">
                <!-- Se inyectarán las filas dinámicamente -->
              </tbody>
            </table>
          </div>

          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px;">
            <button class="btn btn-secondary btn-sm" onclick="addTableRow()">➕ Agregar Fila</button>
            
            <!-- Selector de Formato de Impresión -->
            <div style="display: flex; align-items: center; gap: 8px;">
              <label style="font-size: 13px; font-weight: 600; color: var(--text-light);">Formato:</label>
              <select id="print-format" class="input-control" style="min-height: 36px; padding: 4px 10px; width: 110px; font-size: 13px;">
                <option value="carta">📄 Carta</option>
                <option value="ticket">🎫 Ticket</option>
              </select>
            </div>
          </div>

          <!-- Totales -->
          <div class="totals-box">
            <div class="total-row">
              <span>Subtotal:</span>
              <span id="label-subtotal">$0.00</span>
            </div>
            <div class="total-row">
              <span>Descuento ($):</span>
              <input type="number" id="input-discount" class="input-control" value="0" min="0" step="any" oninput="calculateTotals()">
            </div>
            <div class="total-row">
              <span>Total:</span>
              <span id="label-total">$0.00</span>
            </div>
          </div>

          <!-- Acciones principales -->
          <div class="action-buttons-group">
            <button class="btn btn-primary" onclick="triggerSaveDocument()">
              💾 Guardar
            </button>
            <button class="btn btn-success" onclick="sendWhatsApp()">
              📲 Enviar WhatsApp
            </button>
            <button class="btn btn-secondary" onclick="printDocFromGen()">
              🖨️ Imprimir
            </button>
            <button class="btn btn-danger" onclick="confirmResetForm()">
              🧹 Limpiar Formulario
            </button>
          </div>

        </div>

      </div>

    </section>

    <!-- 2. PESTAÑA: CLIENTES -->
    <section id="tab-clients" class="tab-content">
      <div class="grid-2">
        
        <!-- Formulario Clientes -->
        <div class="card">
          <h2 class="card-title" id="client-form-title">👥 Registrar Cliente</h2>
          <form id="client-form" onsubmit="handleClientSubmit(event)">
            <input type="hidden" id="client-editing-id">
            <div class="form-group">
              <label>Nombre Completo</label>
              <input type="text" id="client-name" class="input-control" required placeholder="Nombre del cliente">
            </div>
            <div class="form-group">
              <label>Teléfono</label>
              <input type="tel" id="client-phone" class="input-control" required placeholder="Teléfono a 10 dígitos">
            </div>
            <div class="form-group">
              <label>Dirección</label>
              <textarea id="client-address" class="input-control" required placeholder="Dirección completa"></textarea>
            </div>
            <div style="display: flex; gap: 10px;">
              <button type="submit" class="btn btn-primary style-flex" style="flex: 1;">💾 Guardar Cliente</button>
              <button type="button" class="btn btn-secondary" id="btn-cancel-client" onclick="resetClientForm()" style="display: none;">Cancelar</button>
            </div>
          </form>
        </div>

        <!-- Directorio Clientes -->
        <div class="card">
          <h2 class="card-title">🔍 Directorio de Clientes</h2>
          <div class="search-bar">
            <input type="text" id="search-client" class="input-control search-input" placeholder="Buscar por nombre o teléfono..." oninput="renderClientsList()">
          </div>
          <div id="clients-list" style="max-height: 400px; overflow-y: auto; border: 1px solid var(--border); border-radius: 8px;">
            <!-- Renderizado de Clientes -->
          </div>
        </div>

      </div>
    </section>

    <!-- 3. PESTAÑA: PRODUCTOS -->
    <section id="tab-products" class="tab-content">
      <div class="grid-2">
        
        <!-- Formulario Productos -->
        <div class="card">
          <h2 class="card-title" id="product-form-title">📦 Registrar Producto</h2>
          <form id="product-form" onsubmit="handleProductSubmit(event)">
            <input type="hidden" id="product-editing-id">
            <div class="form-group">
              <label>Nombre del Producto</label>
              <input type="text" id="product-name" class="input-control" required placeholder="Nombre comercial">
            </div>
            <div class="form-group">
              <label>Precio Unitario por Defecto ($)</label>
              <input type="number" id="product-price" class="input-control" required step="any" min="0" placeholder="Precio sugerido">
            </div>
            <div style="display: flex; gap: 10px;">
              <button type="submit" class="btn btn-primary" style="flex: 1;">💾 Guardar Producto</button>
              <button type="button" class="btn btn-secondary" id="btn-cancel-product" onclick="resetProductForm()" style="display: none;">Cancelar</button>
            </div>
          </form>
        </div>

        <!-- Catálogo de Productos -->
        <div class="card">
          <h2 class="card-title">🔍 Catálogo de Productos</h2>
          <div class="search-bar">
            <input type="text" id="search-product" class="input-control search-input" placeholder="Buscar producto por nombre..." oninput="renderProductsList()">
          </div>
          <div id="products-list" style="max-height: 400px; overflow-y: auto; border: 1px solid var(--border); border-radius: 8px;">
            <!-- Renderizado de Productos -->
          </div>
        </div>

      </div>
    </section>

    <!-- 4. PESTAÑA: HISTORIAL -->
    <section id="tab-history" class="tab-content">
      <div class="card">
        <h2 class="card-title">📜 Historial de Documentos</h2>
        
        <!-- Filtros del Historial -->
        <div class="history-filters">
          <div class="form-group">
            <label>Filtrar por Cliente</label>
            <input type="text" id="filter-hist-client" class="input-control" placeholder="Nombre del cliente..." oninput="renderHistory()">
          </div>
          <div class="form-group">
            <label>Tipo de Documento</label>
            <select id="filter-hist-type" class="input-control" onchange="renderHistory()">
              <option value="todos">Todos</option>
              <option value="Cotización">Cotización</option>
              <option value="Remisión">Remisión</option>
            </select>
          </div>
          <div class="form-group">
            <label>Filtrar por Fecha</label>
            <input type="date" id="filter-hist-date" class="input-control" onchange="renderHistory()">
          </div>
        </div>

        <button class="btn btn-secondary btn-sm" onclick="clearHistoryFilters()" style="margin-bottom: 20px;">🧹 Limpiar Filtros</button>

        <div class="table-container">
          <table class="doc-table">
            <thead>
              <tr>
                <th>Folio</th>
                <th>Tipo</th>
                <th>Fecha</th>
                <th>Cliente</th>
                <th style="text-align: right;">Total ($)</th>
                <th style="text-align: center; width: 180px;">Acciones</th>
              </tr>
            </thead>
            <tbody id="history-tbody">
              <!-- Renderizado de Historial -->
            </tbody>
          </table>
        </div>
      </div>
    </section>

  </div>

  <!-- MODAL: CONTROL DE VERSIONES (ACTUALIZAR VS NUEVO) -->
  <div id="modal-version" class="modal-overlay">
    <div class="modal">
      <div class="modal-header">
        <span>Guardar Documento</span>
        <button type="button" onclick="closeVersionModal()" style="border:none; background:none; font-size: 20px; cursor:pointer;">&times;</button>
      </div>
      <div class="modal-body">
        <p>El documento que está editando ya existe en el historial. Elija una opción:</p>
        <p style="margin-top: 10px;">
          <strong>Opción A:</strong> Actualizar el documento existente conservando el folio original.
        </p>
        <p style="margin-top: 10px;">
          <strong>Opción B:</strong> Guardar como un nuevo documento (generando un folio consecutivo).
        </p>
      </div>
      <div class="modal-footer">
        <button class="btn btn-primary" onclick="saveDocumentFromModal(true)">A) Actualizar Documento Existente</button>
        <button class="btn btn-secondary" onclick="saveDocumentFromModal(false)">B) Guardar como Nuevo Documento</button>
        <button class="btn btn-danger" onclick="closeVersionModal()" style="background-color: #64748b; color: white;">Cancelar</button>
      </div>
    </div>
  </div>

  <!-- CONTENEDOR DE NOTIFICACIONES TOAST -->
  <div class="toast-container" id="toast-container"></div>

  <!-- AREA DE IMPRESIÓN DINÁMICA -->
  <div id="print-area" class="print-only"></div>

  <!-- LOGICA DE LA APLICACIÓN (JAVASCRIPT) -->
  <script>
    // ESTADO DE LA APLICACIÓN
    let currentDocumentId = null;
    let currentDocumentFolio = null;
    let editingClientId = null;
    let editingProductId = null;

    // AL CARGAR LA PÁGINA
    window.addEventListener('DOMContentLoaded', () => {
      initDatabase();
      resetGeneratorForm();
      renderClientsList();
      renderProductsList();
      renderHistory();
      
      // Actualizar fecha cada minuto
      setInterval(updateCurrentTime, 60000);
    });

    // INICIALIZACIÓN DE LA BASE DE DATOS (LOCALSTORAGE)
    function initDatabase() {
      // Catálogo inicial obligatorio de 15 productos
      const initialProducts = [
        { name: "Cloro", price: 12.00 },
        { name: "Pino", price: 15.00 },
        { name: "Mas Color", price: 35.00 },
        { name: "Downy", price: 38.00 },
        { name: "Salvo", price: 25.00 },
        { name: "Axion", price: 22.00 },
        { name: "Suave Sol", price: 18.00 },
        { name: "Carisma Suavizante", price: 24.00 },
        { name: "Carisma Detergente", price: 28.00 },
        { name: "Zote", price: 20.00 },
        { name: "Roma", price: 22.00 },
        { name: "Insecticida", price: 45.00 },
        { name: "Detercon", price: 15.00 },
        { name: "Almorol", price: 35.00 },
        { name: "Desengrasante de Motor", price: 50.00 }
      ];

      if (!localStorage.getItem('innovaclean_products')) {
        const productsList = initialProducts.map((p, idx) => ({
          id: Date.now() + idx,
          name: p.name,
          price: p.price
        }));
        localStorage.setItem('innovaclean_products', JSON.stringify(productsList));
      }

      if (!localStorage.getItem('innovaclean_clients')) {
        localStorage.setItem('innovaclean_clients', JSON.stringify([]));
      }

      if (!localStorage.getItem('innovaclean_documents')) {
        localStorage.setItem('innovaclean_documents', JSON.stringify([]));
      }

      if (!localStorage.getItem('innovaclean_config')) {
        localStorage.setItem('innovaclean_config', JSON.stringify({ nextFolio: 1001 }));
      }
    }

    // MANEJO DE NOTIFICACIONES (TOAST)
    function showToast(message, type = 'success') {
      const container = document.getElementById('toast-container');
      const toast = document.createElement('div');
      toast.className = `toast toast-${type}`;
      toast.innerHTML = `<span>${type === 'success' ? '✅' : '❌'}</span> <span>${message}</span>`;
      container.appendChild(toast);
      
      setTimeout(() => {
        toast.remove();
      }, 3000);
    }

    // NAVEGACIÓN ENTRE PESTAÑAS
    function switchTab(tabId) {
      document.querySelectorAll('.tab-content').forEach(tab => {
        tab.classList.remove('active');
      });
      document.querySelectorAll('.tab-btn').forEach(btn => {
        btn.classList.remove('active');
      });

      document.getElementById(tabId).classList.add('active');
      
      // Encontrar el botón correspondiente
      const btn = Array.from(document.querySelectorAll('.tab-btn')).find(b => {
        if (tabId === 'tab-generator') return b.innerText.includes('Documento');
        if (tabId === 'tab-clients') return b.innerText.includes('Clientes');
        if (tabId === 'tab-products') return b.innerText.includes('Productos');
        if (tabId === 'tab-history') return b.innerText.includes('Historial');
      });
      if (btn) btn.classList.add('active');

      // Actualizaciones al entrar a pestañas
      if (tabId === 'tab-history') {
        renderHistory();
      } else if (tabId === 'tab-clients') {
        renderClientsList();
      } else if (tabId === 'tab-products') {
        renderProductsList();
      } else if (tabId === 'tab-generator') {
        updateCurrentTime();
        if (currentDocumentId === null) {
          updateNextFolioUI();
        }
      }
    }

    // -------------------------------------------------------------
    // SECCIÓN 1: GENERADOR DE DOCUMENTOS
    // -------------------------------------------------------------

    function updateCurrentTime() {
      if (currentDocumentId === null) {
        const now = new Date();
        const year = now.getFullYear();
        const month = String(now.getMonth() + 1).padStart(2, '0');
        const day = String(now.getDate()).padStart(2, '0');
        const hours = String(now.getHours()).padStart(2, '0');
        const minutes = String(now.getMinutes()).padStart(2, '0');
        document.getElementById('doc-date').value = `${day}/${month}/${year} ${hours}:${minutes}`;
      }
    }

    function updateNextFolioUI() {
      const config = JSON.parse(localStorage.getItem('innovaclean_config'));
      document.getElementById('doc-folio').value = config.nextFolio;
    }

    function updateDocTypeUI() {
      const type = document.querySelector('input[name="doc-type"]:checked').value;
      const labelCot = document.getElementById('label-type-cot');
      const labelRem = document.getElementById('label-type-rem');
      
      if (type === 'Cotización') {
        labelCot.style.borderColor = 'var(--primary)';
        labelCot.style.backgroundColor = 'var(--primary-light)';
        labelCot.style.color = 'var(--primary-hover)';
        
        labelRem.style.borderColor = 'var(--border)';
        labelRem.style.backgroundColor = 'transparent';
        labelRem.style.color = 'var(--text-light)';
      } else {
        labelRem.style.borderColor = 'var(--primary)';
        labelRem.style.backgroundColor = 'var(--primary-light)';
        labelRem.style.color = 'var(--primary-hover)';
        
        labelCot.style.borderColor = 'var(--border)';
        labelCot.style.backgroundColor = 'transparent';
        labelCot.style.color = 'var(--text-light)';
      }
    }

    // AUTOCOMPLETADO DE CLIENTE
    const clientInput = document.getElementById('doc-client');
    const clientDropdown = document.getElementById('client-autocomplete');

    clientInput.addEventListener('input', (e) => {
      const val = e.target.value.toLowerCase();
      const clients = JSON.parse(localStorage.getItem('innovaclean_clients') || '[]');
      
      if (!val) {
        clientDropdown.style.display = 'none';
        return;
      }

      const filtered = clients.filter(c => c.name.toLowerCase().includes(val) || c.phone.includes(val));
      
      if (filtered.length === 0) {
        clientDropdown.style.display = 'none';
        return;
      }

      clientDropdown.innerHTML = '';
      filtered.forEach(c => {
        const item = document.createElement('div');
        item.className = 'autocomplete-item';
        item.innerText = `${c.name} - 📱 ${c.phone}`;
        item.addEventListener('click', () => {
          clientInput.value = c.name;
          document.getElementById('doc-phone').value = c.phone;
          document.getElementById('doc-address').value = c.address;
          clientDropdown.style.display = 'none';
        });
        clientDropdown.appendChild(item);
      });
      clientDropdown.style.display = 'block';
    });

    // Cerrar dropdown al hacer click fuera
    document.addEventListener('click', (e) => {
      if (e.target !== clientInput && e.target !== clientDropdown) {
        clientDropdown.style.display = 'none';
      }
    });

    // GUARDAR CLIENTE DESDE DOCUMENTO
    function saveClientFromDoc() {
      const name = clientInput.value.trim();
      const phone = document.getElementById('doc-phone').value.trim();
      const address = document.getElementById('doc-address').value.trim();

      if (!name || !phone || !address) {
        showToast("Llene todos los datos del cliente para registrarlo", "error");
        return;
      }

      const clients = JSON.parse(localStorage.getItem('innovaclean_clients') || '[]');
      
      // Evitar duplicados por nombre
      const exists = clients.some(c => c.name.toLowerCase() === name.toLowerCase());
      if (exists) {
        showToast("Ya existe un cliente con ese nombre", "error");
        return;
      }

      const newClient = {
        id: Date.now(),
        name,
        phone,
        address
      };

      clients.push(newClient);
      localStorage.setItem('innovaclean_clients', JSON.stringify(clients));
      showToast("Cliente guardado en el directorio");
      renderClientsList();
    }

    // MANEJO DE FILAS DE CONCEPTOS
    function addTableRow(productName = '', qty = 1, price = 0) {
      const tbody = document.getElementById('items-tbody');
      const rowId = Date.now() + Math.random().toString(36).substr(2, 5);
      
      const tr = document.createElement('tr');
      tr.id = `row-${rowId}`;
      
      tr.innerHTML = `
        <td class="col-qty">
          <input type="number" class="input-control qty-input" value="${qty}" min="0.1" step="any" oninput="calculateRow('${rowId}')" style="min-height:36px; padding: 4px 8px;">
        </td>
        <td>
          <div class="autocomplete-container">
            <input type="text" class="input-control product-input" value="${productName}" placeholder="Escriba el producto..." autocomplete="off" oninput="handleProductAutocomplete('${rowId}', this)" style="min-height:36px; padding: 4px 8px;">
            <div id="dropdown-${rowId}" class="autocomplete-dropdown" style="display: none;"></div>
          </div>
        </td>
        <td class="col-price">
          <input type="number" class="input-control price-input" value="${price}" min="0" step="any" oninput="calculateRow('${rowId}')" style="min-height:36px; padding: 4px 8px;">
        </td>
        <td class="col-total">
          $<span class="row-total-val">${(qty * price).toFixed(2)}</span>
        </td>
        <td class="col-actions">
          <button class="btn-action-delete" type="button" onclick="deleteTableRow('${rowId}')">&times;</button>
        </td>
      `;
      
      tbody.appendChild(tr);
      calculateTotals();
    }

    function deleteTableRow(rowId) {
      const row = document.getElementById(`row-${rowId}`);
      if (row) {
        row.remove();
        calculateTotals();
      }
    }

    // AUTOCOMPLETADO DE PRODUCTOS EN LA FILA
    function handleProductAutocomplete(rowId, inputEl) {
      const dropdown = document.getElementById(`dropdown-${rowId}`);
      const val = inputEl.value.toLowerCase();
      const products = JSON.parse(localStorage.getItem('innovaclean_products') || '[]');

      if (!val) {
        dropdown.style.display = 'none';
        return;
      }

      const filtered = products.filter(p => p.name.toLowerCase().includes(val));

      if (filtered.length === 0) {
        dropdown.style.display = 'none';
        return;
      }

      dropdown.innerHTML = '';
      filtered.forEach(p => {
        const item = document.createElement('div');
        item.className = 'autocomplete-item';
        item.innerText = `${p.name} ($${parseFloat(p.price).toFixed(2)})`;
        item.addEventListener('click', () => {
          inputEl.value = p.name;
          const tr = document.getElementById(`row-${rowId}`);
          tr.querySelector('.price-input').value = p.price;
          dropdown.style.display = 'none';
          calculateRow(rowId);
        });
        dropdown.appendChild(item);
      });
      dropdown.style.display = 'block';

      // Cerrar dropdown al hacer click fuera
      document.addEventListener('click', function closeDrop(e) {
        if (e.target !== inputEl && e.target !== dropdown) {
          dropdown.style.display = 'none';
          document.removeEventListener('click', closeDrop);
        }
      });
    }

    // CÁLCULO DE LA FILA
    function calculateRow(rowId) {
      const tr = document.getElementById(`row-${rowId}`);
      if (!tr) return;
      const qty = parseFloat(tr.querySelector('.qty-input').value) || 0;
      const price = parseFloat(tr.querySelector('.price-input').value) || 0;
      const totalSpan = tr.querySelector('.row-total-val');
      totalSpan.innerText = (qty * price).toFixed(2);
      calculateTotals();
    }

    // CÁLCULO DE TOTALES GENERALES
    function calculateTotals() {
      let subtotal = 0;
      document.querySelectorAll('.row-total-val').forEach(span => {
        subtotal += parseFloat(span.innerText) || 0;
      });

      const discount = parseFloat(document.getElementById('input-discount').value) || 0;
      const total = Math.max(0, subtotal - discount);

      document.getElementById('label-subtotal').innerText = `$${subtotal.toFixed(2)}`;
      document.getElementById('label-total').innerText = `$${total.toFixed(2)}`;
    }

    // INICIAR GUARDADO DE DOCUMENTO
    function triggerSaveDocument() {
      const client = clientInput.value.trim();
      const phone = document.getElementById('doc-phone').value.trim();
      const address = document.getElementById('doc-address').value.trim();
      const rows = document.querySelectorAll('#items-tbody tr');

      if (!client || !phone || !address) {
        showToast("Debe llenar todos los datos del cliente", "error");
        return;
      }

      if (rows.length === 0) {
        showToast("Debe agregar al menos un producto al documento", "error");
        return;
      }

      // Validar productos sin nombre o vacíos
      let invalidProduct = false;
      rows.forEach(tr => {
        const prodVal = tr.querySelector('.product-input').value.trim();
        if (!prodVal) invalidProduct = true;
      });

      if (invalidProduct) {
        showToast("Todos los conceptos agregados deben tener nombre de producto", "error");
        return;
      }

      // Si estamos editando un documento existente
      if (currentDocumentId !== null) {
        openVersionModal();
      } else {
        // Guardar como nuevo de forma directa
        saveDocument(false);
      }
    }

    // CONTROL DE MODAL DE VERSIONES
    function openVersionModal() {
      document.getElementById('modal-version').classList.add('active');
    }

    function closeVersionModal() {
      document.getElementById('modal-version').classList.remove('active');
    }

    function saveDocumentFromModal(updateExisting) {
      closeVersionModal();
      saveDocument(updateExisting);
    }

    // LOGICA CENTRAL DE GUARDAR DOCUMENTO
    function saveDocument(updateExisting) {
      const type = document.querySelector('input[name="doc-type"]:checked').value;
      const client = clientInput.value.trim();
      const phone = document.getElementById('doc-phone').value.trim();
      const address = document.getElementById('doc-address').value.trim();
      const observations = document.getElementById('doc-observations').value.trim();
      const discount = parseFloat(document.getElementById('input-discount').value) || 0;
      
      const products = [];
      let subtotal = 0;
      document.querySelectorAll('#items-tbody tr').forEach(tr => {
        const qty = parseFloat(tr.querySelector('.qty-input').value) || 0;
        const prod = tr.querySelector('.product-input').value.trim();
        const price = parseFloat(tr.querySelector('.price-input').value) || 0;
        const imp = qty * price;
        subtotal += imp;
        products.push({
          cantidad: qty,
          producto: prod,
          precioUnitario: price,
          importe: imp
        });
      });

      const total = Math.max(0, subtotal - discount);
      const docs = JSON.parse(localStorage.getItem('innovaclean_documents') || '[]');
      
      let finalFolio;
      let finalId;
      let finalDate;

      if (updateExisting && currentDocumentId !== null) {
        // Encontrar índice existente
        const index = docs.findIndex(d => d.id === currentDocumentId);
        if (index === -1) {
          showToast("No se encontró el documento original para actualizar", "error");
          return;
        }
        
        finalId = currentDocumentId;
        finalFolio = currentDocumentFolio;
        
        // Conservamos fecha anterior o ponemos la actual. De acuerdo a la especificación de "fecha y hora automática",
        // podemos actualizar con la fecha actual del guardado.
        const now = new Date();
        const year = now.getFullYear();
        const month = String(now.getMonth() + 1).padStart(2, '0');
        const day = String(now.getDate()).padStart(2, '0');
        const hours = String(now.getHours()).padStart(2, '0');
        const minutes = String(now.getMinutes()).padStart(2, '0');
        finalDate = `${day}/${month}/${year} ${hours}:${minutes}`;

        docs[index] = {
          id: finalId,
          folio: finalFolio,
          tipo: type,
          fecha: finalDate,
          cliente: { name: client, phone, address },
          observaciones,
          productos: products,
          descuento: discount,
          total: total
        };

        showToast(`Documento ${type} Folio #${finalFolio} actualizado correctamente`);
      } else {
        // Generar nuevo folio y nuevo ID
        const config = JSON.parse(localStorage.getItem('innovaclean_config'));
        finalFolio = config.nextFolio;
        finalId = Date.now();
        
        const now = new Date();
        const year = now.getFullYear();
        const month = String(now.getMonth() + 1).padStart(2, '0');
        const day = String(now.getDate()).padStart(2, '0');
        const hours = String(now.getHours()).padStart(2, '0');
        const minutes = String(now.getMinutes()).padStart(2, '0');
        finalDate = `${day}/${month}/${year} ${hours}:${minutes}`;

        // Incrementar folio en config
        config.nextFolio = finalFolio + 1;
        localStorage.setItem('innovaclean_config', JSON.stringify(config));

        docs.push({
          id: finalId,
          folio: finalFolio,
          tipo: type,
          fecha: finalDate,
          cliente: { name: client, phone, address },
          observaciones,
          productos: products,
          descuento: discount,
          total: total
        });

        showToast(`Documento ${type} Folio #${finalFolio} guardado correctamente`);
      }

      localStorage.setItem('innovaclean_documents', JSON.stringify(docs));
      
      // Limpiar y salir del modo edición
      exitEditMode();
      resetGeneratorForm();
      renderHistory();
    }

    // SALIR DE MODO EDICIÓN
    function exitEditMode() {
      currentDocumentId = null;
      currentDocumentFolio = null;
      document.getElementById('edit-indicator').style.display = 'none';
    }

    // LIMPIAR GENERADOR
    function confirmResetForm() {
      if (confirm("¿Está seguro de limpiar el generador de documentos? Perderá los cambios no guardados.")) {
        exitEditMode();
        resetGeneratorForm();
      }
    }

    function resetGeneratorForm() {
      // Inputs de texto
      clientInput.value = '';
      document.getElementById('doc-phone').value = '';
      document.getElementById('doc-address').value = '';
      document.getElementById('doc-observations').value = '';
      document.getElementById('input-discount').value = '0';

      // Tipo por defecto (Cotización)
      document.querySelector('input[name="doc-type"][value="Cotización"]').checked = true;
      updateDocTypeUI();

      // Limpiar conceptos
      document.getElementById('items-tbody').innerHTML = '';
      
      // Agregar dos filas vacías sugeridas
      addTableRow();
      addTableRow();

      // Recalcular
      updateCurrentTime();
      updateNextFolioUI();
      calculateTotals();
    }

    // INTEGRACIÓN CON WHATSAPP
    function sendWhatsApp() {
      const type = document.querySelector('input[name="doc-type"]:checked').value;
      const client = clientInput.value.trim();
      const phone = document.getElementById('doc-phone').value.trim();
      const address = document.getElementById('doc-address').value.trim();
      const observations = document.getElementById('doc-observations').value.trim();
      const discount = parseFloat(document.getElementById('input-discount').value) || 0;
      const folio = document.getElementById('doc-folio').value;

      if (!client || !phone) {
        showToast("Se requiere al menos Nombre y Teléfono del cliente para enviar WhatsApp", "error");
        return;
      }

      // Limpiar teléfono
      const cleanPhone = phone.replace(/\D/g, '');
      if (cleanPhone.length < 10) {
        showToast("El teléfono debe contener al menos 10 dígitos numéricos", "error");
        return;
      }

      let subtotal = 0;
      const itemsText = [];
      
      document.querySelectorAll('#items-tbody tr').forEach(tr => {
        const qty = parseFloat(tr.querySelector('.qty-input').value) || 0;
        const prod = tr.querySelector('.product-input').value.trim();
        const price = parseFloat(tr.querySelector('.price-input').value) || 0;
        const imp = qty * price;
        
        if (prod) {
          subtotal += imp;
          itemsText.push(`${qty} x ${prod} = $${imp.toFixed(2)}`);
        }
      });

      if (itemsText.length === 0) {
        showToast("Agregue al menos un producto con descripción para enviar", "error");
        return;
      }

      const total = Math.max(0, subtotal - discount);

      // Formato estricto solicitado
      let msg = `INNOVA CLEAN\n\n`;
      msg += `${type.toUpperCase()}\n`;
      msg += `FOLIO #${folio}\n\n`;
      msg += `Cliente: ${client}\n`;
      msg += `Teléfono: ${phone}\n`;
      msg += `Dirección: ${address}\n\n`;
      msg += `PRODUCTOS\n\n`;
      
      itemsText.forEach(line => {
        msg += `${line}\n`;
      });
      
      if (discount > 0) {
        msg += `\nDescuento: $${discount.toFixed(2)}\n`;
      }
      
      msg += `\nTOTAL: $${total.toFixed(2)}\n\n`;
      
      if (observations) {
        msg += `Observaciones:\n${observations}\n\n`;
      }
      
      msg += `Gracias por su preferencia.`;

      // Enlace universal wa.me
      const waUrl = `https://wa.me/52${cleanPhone}?text=${encodeURIComponent(msg)}`;
      window.open(waUrl, '_blank');
    }

    // IMPRESIÓN DESDE EL GENERADOR
    function printDocFromGen() {
      const type = document.querySelector('input[name="doc-type"]:checked').value;
      const client = clientInput.value.trim();
      const phone = document.getElementById('doc-phone').value.trim();
      const address = document.getElementById('doc-address').value.trim();
      const observations = document.getElementById('doc-observations').value.trim();
      const discount = parseFloat(document.getElementById('input-discount').value) || 0;
      const folio = document.getElementById('doc-folio').value;
      const date = document.getElementById('doc-date').value;

      if (!client) {
        showToast("Es obligatorio ingresar un cliente antes de imprimir", "error");
        return;
      }

      const products = [];
      let subtotal = 0;
      document.querySelectorAll('#items-tbody tr').forEach(tr => {
        const qty = parseFloat(tr.querySelector('.qty-input').value) || 0;
        const prod = tr.querySelector('.product-input').value.trim();
        const price = parseFloat(tr.querySelector('.price-input').value) || 0;
        const imp = qty * price;
        
        if (prod) {
          subtotal += imp;
          products.push({
            cantidad: qty,
            producto: prod,
            precioUnitario: price,
            importe: imp
          });
        }
      });

      if (products.length === 0) {
        showToast("Debe agregar al menos un producto para poder imprimir", "error");
        return;
      }

      const total = Math.max(0, subtotal - discount);
      const doc = {
        folio,
        tipo: type,
        fecha: date,
        cliente: { name: client, phone, address },
        observaciones,
        productos: products,
        descuento: discount,
        total: total
      };

      const format = document.getElementById('print-format').value;
      executePrint(doc, format);
    }

    // GENERACIÓN E INVOCACIÓN DE VISTA DE IMPRESIÓN
    function executePrint(doc, format) {
      const printContainer = document.getElementById('print-area');
      printContainer.innerHTML = ''; // Limpiar previo

      if (format === 'carta') {
        // ESTRUCTURA CARTA
        printContainer.innerHTML = `
          <div class="print-letter">
            <div class="p-header">
              <div>
                <div class="p-logo">✨ INNOVA CLEAN</div>
                <div style="font-size: 13px; color: #475569; margin-top: 4px;">Soluciones de Limpieza e Higiene Profesional</div>
              </div>
              <div>
                <div class="p-meta-title">${doc.tipo.toUpperCase()}</div>
                <div class="p-meta-folio">FOLIO: #${doc.folio}</div>
                <div style="font-size: 13px; text-align: right; color: #475569; margin-top: 4px;">Fecha: ${doc.fecha}</div>
              </div>
            </div>

            <div class="p-details-grid">
              <div>
                <div class="p-section-title">Datos del Cliente</div>
                <strong>Cliente:</strong> ${doc.cliente.name}<br>
                <strong>Dirección:</strong> ${doc.cliente.address}<br>
                <strong>Teléfono:</strong> ${doc.cliente.phone}
              </div>
              <div>
                <div class="p-section-title">Validez del Documento</div>
                <strong>Tipo:</strong> Original<br>
                <strong>Formato:</strong> Control Administrativo Offline<br>
                <strong>Estado:</strong> Vigente
              </div>
            </div>

            <div class="p-section-title">Conceptos del Servicio / Pedido</div>
            <table class="p-table">
              <thead>
                <tr>
                  <th style="width: 80px;">Cant.</th>
                  <th>Producto / Concepto</th>
                  <th style="width: 150px; text-align: right;">P. Unitario</th>
                  <th style="width: 150px; text-align: right;">Importe</th>
                </tr>
              </thead>
              <tbody>
                ${doc.productos.map(p => `
                  <tr>
                    <td>${p.cantidad}</td>
                    <td>${p.producto}</td>
                    <td style="text-align: right;">$${p.precioUnitario.toFixed(2)}</td>
                    <td style="text-align: right;">$${p.importe.toFixed(2)}</td>
                  </tr>
                `).join('')}
              </tbody>
            </table>

            <div style="display: grid; grid-template-columns: 1fr 250px; gap: 20px; align-items: start;">
              <div style="border: 1px solid #cbd5e1; padding: 15px; border-radius: 8px; font-size: 13px; color: #334155;">
                <strong style="display:block; margin-bottom: 6px;">Observaciones:</strong>
                ${doc.observaciones || 'Sin observaciones adicionales.'}
              </div>
              <div class="p-totals">
                <div class="p-total-row">
                  <span>Subtotal:</span>
                  <span>$${(doc.total + doc.descuento).toFixed(2)}</span>
                </div>
                <div class="p-total-row">
                  <span>Descuento:</span>
                  <span>-$$${doc.descuento.toFixed(2)}</span>
                </div>
                <div class="p-total-row grand-total">
                  <span>Total:</span>
                  <span>$${doc.total.toFixed(2)}</span>
                </div>
              </div>
            </div>

            <div style="margin-top: 60px; text-align: center; font-size: 14px; border-top: 1px solid #cbd5e1; padding-top: 20px; color: #475569;">
              ¡Gracias por su preferencia! Innovando en limpieza para su negocio u hogar.
            </div>
          </div>
        `;
      } else {
        // ESTRUCTURA TICKET (80mm)
        printContainer.innerHTML = `
          <div class="print-ticket">
            <div class="pt-center">
              <div class="pt-title">✨ INNOVA CLEAN</div>
              <div>PRODUCTOS DE LIMPIEZA</div>
              <div class="pt-divider"></div>
              <div style="font-weight: bold; font-size: 13px;">${doc.tipo.toUpperCase()}</div>
              <div>FOLIO: #${doc.folio}</div>
              <div>Fecha: ${doc.fecha}</div>
            </div>
            
            <div class="pt-divider"></div>
            
            <div>
              <strong>Cliente:</strong> ${doc.cliente.name}<br>
              <strong>Tel:</strong> ${doc.cliente.phone}<br>
              <strong>Dir:</strong> ${doc.cliente.address}
            </div>

            <div class="pt-divider"></div>

            <table class="pt-table">
              <thead>
                <tr>
                  <th style="width: 35px;">Cant</th>
                  <th>Desc</th>
                  <th style="width: 55px; text-align: right;">Total</th>
                </tr>
              </thead>
              <tbody>
                ${doc.productos.map(p => `
                  <tr>
                    <td>${p.cantidad}</td>
                    <td>${p.producto} <br><small>1x $${p.precioUnitario.toFixed(2)}</small></td>
                    <td style="text-align: right;">$${p.importe.toFixed(2)}</td>
                  </tr>
                `).join('')}
              </tbody>
            </table>

            <div class="pt-divider"></div>

            <div class="pt-totals">
              <div class="pt-total-row">
                <span>Subtotal:</span>
                <span>$${(doc.total + doc.descuento).toFixed(2)}</span>
              </div>
              <div class="pt-total-row">
                <span>Desc:</span>
                <span>-$${doc.descuento.toFixed(2)}</span>
              </div>
              <div class="pt-total-row" style="font-size: 14px; border-top: 1px dashed #000; padding-top: 4px;">
                <span>TOTAL:</span>
                <span>$${doc.total.toFixed(2)}</span>
              </div>
            </div>

            <div class="pt-divider"></div>

            ${doc.observaciones ? `
              <div style="margin-bottom: 10px;">
                <strong>Obs:</strong> ${doc.observaciones}
              </div>
              <div class="pt-divider"></div>
            ` : ''}

            <div class="pt-center" style="margin-top: 15px; font-size: 10px;">
              ¡GRACIAS POR SU PREFERENCIA!
            </div>
          </div>
        `;
      }

      window.print();
    }

    // -------------------------------------------------------------
    // SECCIÓN 2: MÓDULO DE CLIENTES (DIRECTORIO)
    // -------------------------------------------------------------

    function handleClientSubmit(e) {
      e.preventDefault();
      const id = document.getElementById('client-editing-id').value;
      const name = document.getElementById('client-name').value.trim();
      const phone = document.getElementById('client-phone').value.trim();
      const address = document.getElementById('client-address').value.trim();

      const clients = JSON.parse(localStorage.getItem('innovaclean_clients') || '[]');

      if (id) {
        // EDITAR CLIENTE EXISTENTE
        const index = clients.findIndex(c => c.id === parseInt(id));
        if (index !== -1) {
          clients[index] = { id: parseInt(id), name, phone, address };
          showToast("Cliente actualizado en el catálogo");
        }
      } else {
        // AGREGAR NUEVO
        const exists = clients.some(c => c.name.toLowerCase() === name.toLowerCase());
        if (exists) {
          showToast("Ya existe un cliente con este nombre en el catálogo", "error");
          return;
        }

        clients.push({
          id: Date.now(),
          name,
          phone,
          address
        });
        showToast("Nuevo cliente agregado correctamente");
      }

      localStorage.setItem('innovaclean_clients', JSON.stringify(clients));
      resetClientForm();
      renderClientsList();
    }

    function renderClientsList() {
      const clients = JSON.parse(localStorage.getItem('innovaclean_clients') || '[]');
      const search = document.getElementById('search-client').value.toLowerCase();
      const listContainer = document.getElementById('clients-list');
      
      listContainer.innerHTML = '';

      const filtered = clients.filter(c => 
        c.name.toLowerCase().includes(search) || 
        c.phone.includes(search) || 
        c.address.toLowerCase().includes(search)
      );

      if (filtered.length === 0) {
        listContainer.innerHTML = '<div style="padding:20px; text-align:center; color:var(--text-light); font-size:14px;">Ningún cliente encontrado</div>';
        return;
      }

      filtered.forEach(c => {
        const row = document.createElement('div');
        row.className = 'item-list-row';
        row.innerHTML = `
          <div class="item-info">
            <div class="item-title">${c.name}</div>
            <div class="item-subtitle">📱 ${c.phone} | 📍 ${c.address}</div>
          </div>
          <div class="item-actions">
            <button class="btn-action-edit" title="Editar" onclick="editClient(${c.id})">✏️</button>
            <button class="btn-action-delete" title="Eliminar" onclick="deleteClient(${c.id})">🗑️</button>
          </div>
        `;
        listContainer.appendChild(row);
      });
    }

    function editClient(id) {
      const clients = JSON.parse(localStorage.getItem('innovaclean_clients') || '[]');
      const c = clients.find(item => item.id === id);
      if (!c) return;

      document.getElementById('client-editing-id').value = c.id;
      document.getElementById('client-name').value = c.name;
      document.getElementById('client-phone').value = c.phone;
      document.getElementById('client-address').value = c.address;

      document.getElementById('client-form-title').innerText = "✏️ Editar Datos de Cliente";
      document.getElementById('btn-cancel-client').style.display = 'inline-flex';
    }

    function deleteClient(id) {
      if (confirm("¿Está seguro de eliminar este cliente? Se quitará de la lista de búsquedas.")) {
        let clients = JSON.parse(localStorage.getItem('innovaclean_clients') || '[]');
        clients = clients.filter(c => c.id !== id);
        localStorage.setItem('innovaclean_clients', JSON.stringify(clients));
        showToast("Cliente eliminado correctamente");
        
        if (document.getElementById('client-editing-id').value == id) {
          resetClientForm();
        }
        renderClientsList();
      }
    }

    function resetClientForm() {
      document.getElementById('client-form').reset();
      document.getElementById('client-editing-id').value = '';
      document.getElementById('client-form-title').innerText = "👥 Registrar Cliente";
      document.getElementById('btn-cancel-client').style.display = 'none';
      editingClientId = null;
    }

    // -------------------------------------------------------------
    // SECCIÓN 3: MÓDULO DE PRODUCTOS (CATÁLOGO SUGERIDO)
    // -------------------------------------------------------------

    function handleProductSubmit(e) {
      e.preventDefault();
      const id = document.getElementById('product-editing-id').value;
      const name = document.getElementById('product-name').value.trim();
      const price = parseFloat(document.getElementById('product-price').value) || 0;

      const products = JSON.parse(localStorage.getItem('innovaclean_products') || '[]');

      if (id) {
        // EDITAR
        const index = products.findIndex(p => p.id === parseInt(id));
        if (index !== -1) {
          products[index] = { id: parseInt(id), name, price };
          showToast("Producto actualizado en el catálogo");
        }
      } else {
        // AGREGAR NUEVO
        const exists = products.some(p => p.name.toLowerCase() === name.toLowerCase());
        if (exists) {
          showToast("Ya existe un producto con este nombre en el catálogo", "error");
          return;
        }

        products.push({
          id: Date.now(),
          name,
          price
        });
        showToast("Nuevo producto agregado al catálogo");
      }

      localStorage.setItem('innovaclean_products', JSON.stringify(products));
      resetProductForm();
      renderProductsList();
    }

    function renderProductsList() {
      const products = JSON.parse(localStorage.getItem('innovaclean_products') || '[]');
      const search = document.getElementById('search-product').value.toLowerCase();
      const listContainer = document.getElementById('products-list');
      
      listContainer.innerHTML = '';

      const filtered = products.filter(p => p.name.toLowerCase().includes(search));

      if (filtered.length === 0) {
        listContainer.innerHTML = '<div style="padding:20px; text-align:center; color:var(--text-light); font-size:14px;">Ningún producto encontrado</div>';
        return;
      }

      filtered.forEach(p => {
        const row = document.createElement('div');
        row.className = 'item-list-row';
        row.innerHTML = `
          <div class="item-info">
            <div class="item-title">${p.name}</div>
            <div class="item-subtitle">Precio sugerido: <strong>$${parseFloat(p.price).toFixed(2)}</strong></div>
          </div>
          <div class="item-actions">
            <button class="btn-action-edit" title="Editar" onclick="editProduct(${p.id})">✏️</button>
            <button class="btn-action-delete" title="Eliminar" onclick="deleteProduct(${p.id})">🗑️</button>
          </div>
        `;
        listContainer.appendChild(row);
      });
    }

    function editProduct(id) {
      const products = JSON.parse(localStorage.getItem('innovaclean_products') || '[]');
      const p = products.find(item => item.id === id);
      if (!p) return;

      document.getElementById('product-editing-id').value = p.id;
      document.getElementById('product-name').value = p.name;
      document.getElementById('product-price').value = p.price;

      document.getElementById('product-form-title').innerText = "✏️ Editar Producto";
      document.getElementById('btn-cancel-product').style.display = 'inline-flex';
    }

    function deleteProduct(id) {
      if (confirm("¿Está seguro de eliminar este producto del catálogo sugerido?")) {
        let products = JSON.parse(localStorage.getItem('innovaclean_products') || '[]');
        products = products.filter(p => p.id !== id);
        localStorage.setItem('innovaclean_products', JSON.stringify(products));
        showToast("Producto eliminado del catálogo correctamente");
        
        if (document.getElementById('product-editing-id').value == id) {
          resetProductForm();
        }
        renderProductsList();
      }
    }

    function resetProductForm() {
      document.getElementById('product-form').reset();
      document.getElementById('product-editing-id').value = '';
      document.getElementById('product-form-title').innerText = "📦 Registrar Producto";
      document.getElementById('btn-cancel-product').style.display = 'none';
      editingProductId = null;
    }

    // -------------------------------------------------------------
    // SECCIÓN 4: HISTORIAL DE DOCUMENTOS
    // -------------------------------------------------------------

    function clearHistoryFilters() {
      document.getElementById('filter-hist-client').value = '';
      document.getElementById('filter-hist-type').value = 'todos';
      document.getElementById('filter-hist-date').value = '';
      renderHistory();
    }

    function renderHistory() {
      const docs = JSON.parse(localStorage.getItem('innovaclean_documents') || '[]');
      const filterClient = document.getElementById('filter-hist-client').value.toLowerCase();
      const filterType = document.getElementById('filter-hist-type').value;
      const filterDate = document.getElementById('filter-hist-date').value; // Formato YYYY-MM-DD
      
      const tbody = document.getElementById('history-tbody');
      tbody.innerHTML = '';

      // Filtrado
      const filtered = docs.filter(d => {
        // Filtro Cliente
        const matchClient = d.cliente.name.toLowerCase().includes(filterClient);
        
        // Filtro Tipo
        const matchType = filterType === 'todos' || d.tipo === filterType;
        
        // Filtro Fecha (d.fecha viene como DD/MM/YYYY HH:MM)
        let matchDate = true;
        if (filterDate) {
          const [fYear, fMonth, fDay] = filterDate.split('-');
          const formattedFilterDate = `${fDay}/${fMonth}/${fYear}`;
          matchDate = d.fecha.startsWith(formattedFilterDate);
        }

        return matchClient && matchType && matchDate;
      });

      // Ordenar por ID de documento (el timestamp más reciente primero)
      filtered.sort((a, b) => b.id - a.id);

      if (filtered.length === 0) {
        tbody.innerHTML = '<tr><td colspan="6" style="text-align:center; padding: 24px; color: var(--text-light);">No se encontraron documentos en el historial</td></tr>';
        return;
      }

      filtered.forEach(d => {
        const tr = document.createElement('tr');
        const badgeClass = d.tipo === 'Cotización' ? 'badge-quote' : 'badge-invoice';
        
        tr.innerHTML = `
          <td><strong>#${d.folio}</strong></td>
          <td><span class="badge ${badgeClass}">${d.tipo}</span></td>
          <td style="white-space: nowrap;">${d.fecha}</td>
          <td>
            <strong>${d.cliente.name}</strong><br>
            <small style="color: var(--text-light);">📱 ${d.cliente.phone}</small>
          </td>
          <td style="text-align: right; font-weight: 700;">$${d.total.toFixed(2)}</td>
          <td>
            <div style="display:flex; gap: 4px; justify-content: center;">
              <button class="btn btn-secondary btn-sm" onclick="openDocumentFromHistory(${d.id})" style="min-height:36px; padding:0 8px;" title="Abrir y Editar">📂 Abrir</button>
              <button class="btn btn-success btn-sm" onclick="sendWhatsAppFromHistory(${d.id})" style="min-height:36px; padding:0 8px;" title="Enviar por WhatsApp">📲</button>
              <button class="btn btn-secondary btn-sm" onclick="printFromHistory(${d.id})" style="min-height:36px; padding:0 8px;" title="Imprimir">🖨️</button>
              <button class="btn btn-danger btn-sm" onclick="deleteHistoryDoc(${d.id})" style="min-height:36px; padding:0 8px;" title="Eliminar">🗑️</button>
            </div>
          </td>
        `;
        tbody.appendChild(tr);
      });
    }

    // CARGAR UN DOCUMENTO DESDE EL HISTORIAL AL GENERADOR
    function openDocumentFromHistory(id) {
      const docs = JSON.parse(localStorage.getItem('innovaclean_documents') || '[]');
      const doc = docs.find(d => d.id === id);
      
      if (!doc) {
        showToast("No se encontró el documento solicitado", "error");
        return;
      }

      // Cambiar estado a Modo Edición
      currentDocumentId = doc.id;
      currentDocumentFolio = doc.folio;

      // Configurar Alerta de indicador
      document.getElementById('edit-folio-text').innerText = doc.folio;
      document.getElementById('edit-indicator').style.display = 'flex';

      // Llenar campos de cabecera
      document.getElementById('doc-folio').value = doc.folio;
      document.getElementById('doc-date').value = doc.fecha;
      clientInput.value = doc.cliente.name;
      document.getElementById('doc-phone').value = doc.cliente.phone;
      document.getElementById('doc-address').value = doc.cliente.address;
      document.getElementById('doc-observations').value = doc.observaciones || '';
      document.getElementById('input-discount').value = doc.descuento;

      // Seleccionar Tipo de documento
      document.querySelector(`input[name="doc-type"][value="${doc.tipo}"]`).checked = true;
      updateDocTypeUI();

      // Rellenar tabla
      const tbody = document.getElementById('items-tbody');
      tbody.innerHTML = '';
      
      doc.productos.forEach(p => {
        addTableRow(p.producto, p.cantidad, p.precioUnitario);
      });

      calculateTotals();
      
      // Ir a la pestaña Generador
      switchTab('tab-generator');
      showToast(`Documento Folio #${doc.folio} cargado en el editor`);
    }

    // ELIMINAR DOCUMENTO DE HISTORIAL
    function deleteHistoryDoc(id) {
      if (confirm("¿Está seguro de eliminar definitivamente este documento del historial? Esta acción no se puede deshacer.")) {
        let docs = JSON.parse(localStorage.getItem('innovaclean_documents') || '[]');
        
        // Si eliminamos el documento que actualmente editamos, salimos de modo edición
        if (currentDocumentId === id) {
          exitEditMode();
          resetGeneratorForm();
        }

        docs = docs.filter(d => d.id !== id);
        localStorage.setItem('innovaclean_documents', JSON.stringify(docs));
        
        showToast("Documento eliminado del historial");
        renderHistory();
      }
    }

    // ACCIONES RÁPIDAS DESDE HISTORIAL
    function printFromHistory(id) {
      const docs = JSON.parse(localStorage.getItem('innovaclean_documents') || '[]');
      const doc = docs.find(d => d.id === id);
      if (doc) {
        const format = document.getElementById('print-format').value;
        executePrint(doc, format);
      }
    }

    function sendWhatsAppFromHistory(id) {
      const docs = JSON.parse(localStorage.getItem('innovaclean_documents') || '[]');
      const doc = docs.find(d => d.id === id);
      
      if (!doc) return;

      const cleanPhone = doc.cliente.phone.replace(/\D/g, '');
      if (cleanPhone.length < 10) {
        showToast("El cliente no tiene un número telefónico válido", "error");
        return;
      }

      let msg = `INNOVA CLEAN\n\n`;
      msg += `${doc.tipo.toUpperCase()}\n`;
      msg += `FOLIO #${doc.folio}\n\n`;
      msg += `Cliente: ${doc.cliente.name}\n`;
      msg += `Teléfono: ${doc.cliente.phone}\n`;
      msg += `Dirección: ${doc.cliente.address}\n\n`;
      msg += `PRODUCTOS\n\n`;
      
      doc.productos.forEach(p => {
        msg += `${p.cantidad} x ${p.producto} = $${p.importe.toFixed(2)}\n`;
      });
      
      if (doc.descuento > 0) {
        msg += `\nDescuento: $${doc.descuento.toFixed(2)}\n`;
      }
      
      msg += `\nTOTAL: $${doc.total.toFixed(2)}\n\n`;
      
      if (doc.observaciones) {
        msg += `Observaciones:\n${doc.observaciones}\n\n`;
      }
      
      msg += `Gracias por su preferencia.`;

      const waUrl = `https://wa.me/52${cleanPhone}?text=${encodeURIComponent(msg)}`;
      window.open(waUrl, '_blank');
    }
  </script>
</body>
</html>
