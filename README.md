<!DOCTYPE html>
<html lang="id">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Smart Cafe - Kantin Kampus</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <link href="https://fonts.googleapis.com/css2?family=Work+Sans:wght@300;400;500;600;700&display=swap"
    rel="stylesheet">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.0/font/bootstrap-icons.css">
  <style>
    * {
      font-family: 'Work Sans', sans-serif;
    }

    :root {
      --primary-color: #001BB7;
      --secondary-color: #0026E8;
      --light-bg: #F5F7FF;
    }

    body {
      background-color: var(--light-bg);
      padding-bottom: 80px;
    }

    .navbar {
      background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
      box-shadow: 0 2px 10px rgba(0, 27, 183, 0.2);
    }

    .navbar-brand {
      font-weight: 700;
      color: white !important;
      font-size: 1.5rem;
    }

    .carousel-item {
      height: 300px;
      border-radius: 15px;
      overflow: hidden;
    }

    .carousel-item img {
      object-fit: cover;
      height: 100%;
      width: 100%;
      filter: brightness(0.8);
    }

    .carousel-caption {
      background: rgba(0, 27, 183, 0.8);
      padding: 15px;
      border-radius: 10px;
      bottom: 20px;
    }

    .search-box {
      border-radius: 25px;
      border: 2px solid var(--primary-color);
      padding: 12px 20px;
      font-size: 1rem;
    }

    .search-box:focus {
      box-shadow: 0 0 0 0.25rem rgba(0, 27, 183, 0.25);
      border-color: var(--primary-color);
    }

    .category-card {
      background: white;
      border-radius: 15px;
      padding: 20px;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s;
      border: 2px solid transparent;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
    }

    .category-card:hover {
      transform: translateY(-5px);
      border-color: var(--primary-color);
      box-shadow: 0 5px 20px rgba(0, 27, 183, 0.2);
    }

    .category-icon {
      font-size: 3rem;
      color: var(--primary-color);
      margin-bottom: 10px;
    }

    .menu-card {
      background: white;
      border-radius: 15px;
      overflow: hidden;
      cursor: pointer;
      transition: all 0.3s;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
      height: 100%;
    }

    .menu-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 5px 20px rgba(0, 27, 183, 0.2);
    }

    .menu-card img {
      height: 200px;
      object-fit: cover;
      width: 100%;
    }

    .menu-card-body {
      padding: 15px;
    }

    .badge-terlaris {
      background-color: #FF6B6B;
      position: absolute;
      top: 10px;
      right: 10px;
      padding: 5px 15px;
      border-radius: 20px;
      font-size: 0.8rem;
    }

    .btn-primary {
      background: var(--primary-color);
      border: none;
      border-radius: 25px;
      padding: 10px 30px;
      font-weight: 600;
      transition: all 0.3s;
    }

    .btn-primary:hover {
      background: var(--secondary-color);
      transform: scale(1.05);
    }

    .bottom-nav {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      background: white;
      box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.1);
      padding: 10px 0;
      z-index: 1000;
    }

    .nav-item-custom {
      text-align: center;
      flex: 1;
      cursor: pointer;
      padding: 5px;
      color: #666;
      transition: all 0.3s;
    }

    .nav-item-custom.active {
      color: var(--primary-color);
    }

    .nav-item-custom i {
      font-size: 1.5rem;
      display: block;
      margin-bottom: 5px;
    }

    .nav-item-custom span {
      font-size: 0.75rem;
      display: block;
    }

    .qr-container {
      background: white;
      padding: 30px;
      border-radius: 15px;
      text-align: center;
      box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
    }

    .qr-code {
      width: 250px;
      height: 250px;
      margin: 20px auto;
      border: 5px solid var(--primary-color);
      border-radius: 15px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: white;
    }

    .order-card {
      background: white;
      border-radius: 15px;
      padding: 20px;
      margin-bottom: 15px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
    }

    .status-badge {
      padding: 5px 15px;
      border-radius: 20px;
      font-size: 0.85rem;
      font-weight: 600;
    }

    .status-pending {
      background: #FFF3CD;
      color: #856404;
    }

    .status-completed {
      background: #D1E7DD;
      color: #0A3622;
    }

    .modal-content {
      border-radius: 20px;
      border: none;
    }

    .modal-header {
      background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
      color: white;
      border-radius: 20px 20px 0 0;
    }

    .quantity-control {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 15px;
    }

    .quantity-btn {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      border: 2px solid var(--primary-color);
      background: white;
      color: var(--primary-color);
      font-size: 1.2rem;
      cursor: pointer;
      transition: all 0.3s;
    }

    .quantity-btn:hover {
      background: var(--primary-color);
      color: white;
    }

    .section-title {
      font-weight: 700;
      color: var(--primary-color);
      margin-bottom: 20px;
      font-size: 1.5rem;
    }

    .page-content {
      display: none;
    }

    .page-content.active {
      display: block;
    }

    .empty-state {
      text-align: center;
      padding: 50px 20px;
      color: #666;
    }

    .empty-state i {
      font-size: 5rem;
      color: #ddd;
      margin-bottom: 20px;
    }

    @media (max-width: 768px) {
      .carousel-item {
        height: 200px;
      }

      .section-title {
        font-size: 1.2rem;
      }
    }
  </style>
</head>

<body>

  <!-- Navbar -->
  <nav class="navbar navbar-dark sticky-top">
    <div class="container">
      <span class="navbar-brand">
        <i class="bi bi-shop"></i> Smart Cafe
      </span>
      <div class="text-white">
        <i class="bi bi-person-circle" style="font-size: 1.5rem;"></i>
      </div>
    </div>
  </nav>

  <!-- Main Content -->
  <div class="container mt-4">

    <!-- Beranda Page -->
    <div id="berandaPage" class="page-content active">
      <!-- Carousel Kantin -->
      <div id="kantinCarousel" class="carousel slide mb-4" data-bs-ride="carousel">
        <div class="carousel-indicators">
          <button type="button" data-bs-target="#kantinCarousel" data-bs-slide-to="0" class="active"></button>
          <button type="button" data-bs-target="#kantinCarousel" data-bs-slide-to="1"></button>
          <button type="button" data-bs-target="#kantinCarousel" data-bs-slide-to="2"></button>
        </div>
        <div class="carousel-inner">
          <div class="carousel-item active">
            <img src="https://images.unsplash.com/photo-1555396273-367ea4eb4db5?w=800" class="d-block w-100"
              alt="Kantin A">
            <div class="carousel-caption">
              <h5>Kantin A - Gedung Utama</h5>
              <p>Menu Spesial: Ayam Geprek, Nasi Goreng</p>
            </div>
          </div>
          <div class="carousel-item">
            <img src="https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?w=800" class="d-block w-100"
              alt="Kantin B">
            <div class="carousel-caption">
              <h5>Kantin B - Fakultas Teknik</h5>
              <p>Menu Spesial: Mie Goreng, Soto Ayam</p>
            </div>
          </div>
          <div class="carousel-item">
            <img src="https://images.unsplash.com/photo-1466978913421-dad2ebd01d17?w=800" class="d-block w-100"
              alt="Kantin C">
            <div class="carousel-caption">
              <h5>Kantin C - Gedung Rektorat</h5>
              <p>Menu Spesial: Nasi Kuning, Pecel Lele</p>
            </div>
          </div>
        </div>
        <button class="carousel-control-prev" type="button" data-bs-target="#kantinCarousel" data-bs-slide="prev">
          <span class="carousel-control-prev-icon"></span>
        </button>
        <button class="carousel-control-next" type="button" data-bs-target="#kantinCarousel" data-bs-slide="next">
          <span class="carousel-control-next-icon"></span>
        </button>
      </div>

      <!-- Search Box -->
      <div class="mb-4">
        <input type="text" id="searchInput" class="form-control search-box" placeholder="🔍 Cari menu favorit kamu...">
      </div>

      <!-- Menu Rekomendasi Terlaris -->
      <h2 class="section-title">🔥 Menu Terlaris</h2>
      <div class="row mb-4" id="menuTerlaris">
        <!-- Menu cards akan ditambahkan via JavaScript -->
      </div>

      <!-- Kategori Kantin -->
      <h2 class="section-title">🏪 Pilih Kantin</h2>
      <div class="row mb-4">
        <div class="col-4 mb-3">
          <div class="category-card" onclick="filterByKantin('Kantin A')">
            <div class="category-icon">🍗</div>
            <h6>Kantin A</h6>
          </div>
        </div>
        <div class="col-4 mb-3">
          <div class="category-card" onclick="filterByKantin('Kantin B')">
            <div class="category-icon">🍜</div>
            <h6>Kantin B</h6>
          </div>
        </div>
        <div class="col-4 mb-3">
          <div class="category-card" onclick="filterByKantin('Kantin C')">
            <div class="category-icon">🍛</div>
            <h6>Kantin C</h6>
          </div>
        </div>
      </div>

      <!-- Semua Menu -->
      <h2 class="section-title">📋 Semua Menu</h2>
      <div class="row" id="allMenu">
        <!-- Menu cards akan ditambahkan via JavaScript -->
      </div>
    </div>

    <!-- Transaksi Page -->
    <div id="transaksiPage" class="page-content">
      <h2 class="section-title">📦 Riwayat Pesanan</h2>
      <div id="orderHistory">
        <!-- Order history akan ditambahkan via JavaScript -->
      </div>
    </div>

  </div>

  <!-- Bottom Navigation -->
  <div class="bottom-nav">
    <div class="container">
      <div class="row g-0">
        <div class="col">
          <div class="nav-item-custom active" onclick="switchPage('beranda')">
            <i class="bi bi-house-door-fill"></i>
            <span>Beranda</span>
          </div>
        </div>
        <div class="col">
          <div class="nav-item-custom" onclick="switchPage('transaksi')">
            <i class="bi bi-clock-history"></i>
            <span>Transaksi</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Modal Detail Menu -->
  <div class="modal fade" id="menuModal" tabindex="-1">
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="modalMenuTitle"></h5>
          <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button>
        </div>
        <div class="modal-body">
          <img id="modalMenuImage" src="" class="img-fluid rounded mb-3"
            style="width: 100%; height: 250px; object-fit: cover;">
          <p id="modalMenuDesc"></p>
          <h5 class="text-primary mb-3" id="modalMenuPrice"></h5>
          <div class="quantity-control mb-3">
            <button class="quantity-btn" onclick="changeQuantity(-1)">-</button>
            <span style="font-size: 1.5rem; font-weight: 600;" id="quantityDisplay">1</span>
            <button class="quantity-btn" onclick="changeQuantity(1)">+</button>
          </div>
          <p class="text-muted mb-3"><strong>Kantin:</strong> <span id="modalMenuKantin"></span></p>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-primary w-100" onclick="processOrder()">
            <i class="bi bi-cart-check"></i> Pesan Sekarang
          </button>
        </div>
      </div>
    </div>
  </div>

  <!-- Modal QR Payment -->
  <div class="modal fade" id="paymentModal" tabindex="-1">
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">💳 Pembayaran</h5>
          <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button>
        </div>
        <div class="modal-body">
          <div class="qr-container">
            <h6 class="mb-3">Scan QR Code untuk Pembayaran</h6>
            <div class="qr-code" id="paymentQR">
              <i class="bi bi-qr-code" style="font-size: 150px; color: var(--primary-color);"></i>
            </div>
            <h5 class="text-primary mt-3" id="totalPayment"></h5>
            <p class="text-muted">Order ID: <span id="orderIdPayment"></span></p>
            <button class="btn btn-primary mt-3" onclick="confirmPayment()">
              <i class="bi bi-check-circle"></i> Konfirmasi Pembayaran
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Modal QR Confirmation -->
  <div class="modal fade" id="confirmationModal" tabindex="-1">
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">✅ Konfirmasi Pesanan</h5>
          <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button>
        </div>
        <div class="modal-body">
          <div class="qr-container">
            <div class="alert alert-success">
              <i class="bi bi-check-circle-fill"></i> Pesanan Berhasil!
            </div>
            <h6 class="mb-3">Tunjukkan QR Code ini saat mengambil pesanan</h6>
            <div class="qr-code" id="confirmationQR">
              <i class="bi bi-qr-code-scan" style="font-size: 150px; color: var(--primary-color);"></i>
            </div>
            <p class="text-muted">Order ID: <span id="orderIdConfirmation"></span></p>
            <p><strong id="orderDetails"></strong></p>
            <button class="btn btn-primary mt-3" data-bs-dismiss="modal">
              <i class="bi bi-house-door"></i> Kembali ke Beranda
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
  <script>
    // Data Menu
    const menuData = [
      {
        id: 1,
        name: 'Ayam Geprek',
        price: 15000,
        image: 'https://images.unsplash.com/photo-1633945274309-7ae5f85b63b0?w=400',
        kantin: 'Kantin A',
        description: 'Ayam goreng crispy dengan sambal geprek pedas',
        terlaris: true
      },
      {
        id: 2,
        name: 'Nasi Goreng',
        price: 12000,
        image: 'https://images.unsplash.com/photo-1603133872878-684f208fb84b?w=400',
        kantin: 'Kantin A',
        description: 'Nasi goreng spesial dengan telur dan ayam',
        terlaris: true
      },
      {
        id: 3,
        name: 'Mie Goreng',
        price: 10000,
        image: 'https://images.unsplash.com/photo-1585032226651-759b368d7246?w=400',
        kantin: 'Kantin B',
        description: 'Mie goreng dengan sayuran segar',
        terlaris: true
      },
      {
        id: 4,
        name: 'Soto Ayam',
        price: 13000,
        image: 'https://images.unsplash.com/photo-1604908815461-7a3c6ff6f1b3?w=400',
        kantin: 'Kantin B',
        description: 'Soto ayam kuah bening dengan nasi',
        terlaris: false
      },
      {
        id: 5,
        name: 'Nasi Kuning',
        price: 14000,
        image: 'https://images.unsplash.com/photo-1612528443702-f6741f70a049?w=400',
        kantin: 'Kantin C',
        description: 'Nasi kuning dengan ayam dan telur',
        terlaris: false
      },
      {
        id: 6,
        name: 'Pecel Lele',
        price: 16000,
        image: 'https://images.unsplash.com/photo-1626200419199-391ae4be7a41?w=400',
        kantin: 'Kantin C',
        description: 'Lele goreng dengan sambal pecel',
        terlaris: true
      }
    ];

    let selectedMenu = null;
    let quantity = 1;
    let currentOrder = null;

    // Initialize App
    function initApp() {
      renderMenuTerlaris();
      renderAllMenu();
      loadOrderHistory();
      setupSearch();
      animateElements();
    }

    // Render Menu Terlaris
    function renderMenuTerlaris() {
      const container = document.getElementById('menuTerlaris');
      const terlaris = menuData.filter(menu => menu.terlaris);

      container.innerHTML = terlaris.map(menu => `
                <div class="col-md-4 col-6 mb-3 menu-item" data-name="${menu.name.toLowerCase()}" data-kantin="${menu.kantin}">
                    <div class="menu-card" onclick="showMenuDetail(${menu.id})">
                        <div style="position: relative;">
                            <img src="${menu.image}" alt="${menu.name}">
                            <span class="badge badge-terlaris">⭐ Terlaris</span>
                        </div>
                        <div class="menu-card-body">
                            <h6 class="mb-2">${menu.name}</h6>
                            <p class="text-muted small mb-2">${menu.kantin}</p>
                            <div class="d-flex justify-content-between align-items-center">
                                <h6 class="text-primary mb-0">Rp ${menu.price.toLocaleString()}</h6>
                                <button class="btn btn-sm btn-primary">
                                    <i class="bi bi-plus"></i>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            `).join('');
    }

    // Render All Menu
    function renderAllMenu() {
      const container = document.getElementById('allMenu');

      container.innerHTML = menuData.map(menu => `
                <div class="col-md-4 col-6 mb-3 menu-item" data-name="${menu.name.toLowerCase()}" data-kantin="${menu.kantin}">
                    <div class="menu-card" onclick="showMenuDetail(${menu.id})">
                        <div style="position: relative;">
                            <img src="${menu.image}" alt="${menu.name}">
                            ${menu.terlaris ? '<span class="badge badge-terlaris">⭐ Terlaris</span>' : ''}
                        </div>
                        <div class="menu-card-body">
                            <h6 class="mb-2">${menu.name}</h6>
                            <p class="text-muted small mb-2">${menu.kantin}</p>
                            <div class="d-flex justify-content-between align-items-center">
                                <h6 class="text-primary mb-0">Rp ${menu.price.toLocaleString()}</h6>
                                <button class="btn btn-sm btn-primary">
                                    <i class="bi bi-plus"></i>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            `).join('');
    }

    // Show Menu Detail
    function showMenuDetail(menuId) {
      selectedMenu = menuData.find(m => m.id === menuId);
      quantity = 1;

      document.getElementById('modalMenuTitle').textContent = selectedMenu.name;
      document.getElementById('modalMenuImage').src = selectedMenu.image;
      document.getElementById('modalMenuDesc').textContent = selectedMenu.description;
      document.getElementById('modalMenuPrice').textContent = Rp ${selectedMenu.price.toLocaleString()};
      document.getElementById('modalMenuKantin').textContent = selectedMenu.kantin;
      document.getElementById('quantityDisplay').textContent = quantity;

      const modal = new bootstrap.Modal(document.getElementById('menuModal'));
      modal.show();
    }

    // Change Quantity
    function changeQuantity(delta) {
      quantity = Math.max(1, quantity + delta);
      document.getElementById('quantityDisplay').textContent = quantity;
    }

    // Process Order
    function processOrder() {
      const orderId = 'ORD' + Date.now();
      const total = selectedMenu.price * quantity;

      currentOrder = {
        id: orderId,
        menu: selectedMenu.name,
        quantity: quantity,
        total: total,
        kantin: selectedMenu.kantin,
        date: new Date().toLocaleString('id-ID'),
        status: 'pending'
      };

      // Close menu modal
      bootstrap.Modal.getInstance(document.getElementById('menuModal')).hide();

      // Show payment modal
      document.getElementById('orderIdPayment').textContent = orderId;
      document.getElementById('totalPayment').textContent = Total: Rp ${total.toLocaleString()};

      const paymentModal = new bootstrap.Modal(document.getElementById('paymentModal'));
      paymentModal.show();
    }

    // Confirm Payment
    function confirmPayment() {
      // Save order to localStorage
      let orders = JSON.parse(localStorage.getItem('orders') || '[]');
      currentOrder.status = 'completed';
      orders.unshift(currentOrder);
      localStorage.setItem('orders', JSON.stringify(orders));

      // Close payment modal
      bootstrap.Modal.getInstance(document.getElementById('paymentModal')).hide();

      // Show confirmation modal
      document.getElementById('orderIdConfirmation').textContent = currentOrder.id;
      document.getElementById('orderDetails').textContent =
        ${currentOrder.menu} x${currentOrder.quantity} - ${currentOrder.kantin};

      const confirmModal = new bootstrap.Modal(document.getElementById('confirmationModal'));
      confirmModal.show();

      // Reload order history
      loadOrderHistory();
    }

    // Load Order History
    function loadOrderHistory() {
      const orders = JSON.parse(localStorage.getItem('orders') || '[]');
      const container = document.getElementById('orderHistory');

      if (orders.length === 0) {
        container.innerHTML = `
                    <div class="empty-state">
                        <i class="bi bi-cart-x"></i>
                        <h5>Belum Ada Pesanan</h5>
                        <p>Yuk pesan menu favorit kamu sekarang!</p>
                    </div>
                `;
        return;
      }

      container.innerHTML = orders.map(order => `
                <div class="order-card">
                    <div class="d-flex justify-content-between align-items-start mb-2">
                        <div>
                            <h6 class="mb-1">${order.menu}</h6>
                            <p class="text-muted small mb-0">${order.kantin} • ${order.date}</p>
                        </div>
                        <span class="status-badge ${order.status === 'completed' ? 'status-completed' : 'status-pending'}">
                            ${order.status === 'completed' ? '✅ Selesai' : '⏳ Pending'}
                        </span>
                    </div>
                    <div class="d-flex justify-content-between align-items-center">
                        <p class="mb-0">Jumlah: <strong>${order.quantity}x</strong></p>
                        <h6 class="text-primary mb-0">Rp ${order.total.toLocaleString()}</h6>
                    </div>
                    <p class="text-muted small mt-2 mb-0">Order ID: ${order.id}</p>
                </div>
            `).join('');
    }

    // Filter by Kantin
    function filterByKantin(kantin) {
      const menuItems = document.querySelectorAll('.menu-item');

      anime({
        targets: '.menu-item',
        opacity: 0,
        scale: 0.8,
        duration: 300,
        easing: 'easeInOutQuad',
        complete: function () {
          menuItems.forEach(item => {
            if (item.dataset.kantin === kantin) {
              item.style.display = 'block';
            } else {
              item.style.display = 'none';
            }
          });

          anime({
            targets: '.menu-item[style*="display: block"]',
            opacity: [0, 1],
            scale: [0.8, 1],
            duration: 500,
            delay: anime.stagger(100),
            easing: 'easeOutElastic(1, .8)'
          });
        }
      });

      // Scroll to menu section
      document.getElementById('allMenu').scrollIntoView({ behavior: 'smooth', block: 'start' });
    }

    // Setup Search
    function setupSearch() {
      const searchInput = document.getElementById('searchInput');
      searchInput.addEventListener('input', function (e) {
        const searchTerm = e.target.value.toLowerCase();
        const menuItems = document.querySelectorAll('.menu-item');

        menuItems.forEach(item => {
          const menuName = item.dataset.name;
          if (menuName.includes(searchTerm)) {
            item.style.display = 'block';
          } else {
            item.style.display = 'none';
          }
        });

        if (searchTerm !== '') {
          anime({
            targets: '.menu-item[style*="display: block"]',
            opacity: [0, 1],
            translateY: [-20, 0],
            duration: 400,
            delay: anime.stagger(50),
            easing: 'easeOutQuad'
          });
        }
      });
    }

    // Switch Page
    function switchPage(page) {
      // Update navigation
      document.querySelectorAll('.nav-item-custom').forEach(item => {
        item.classList.remove('active');
      });
      event.currentTarget.classList.add('active');

      // Hide all pages
      document.querySelectorAll('.page-content').forEach(content => {
        content.classList.remove('active');
      });

      // Show selected page
      if (page === 'beranda') {
        document.getElementById('berandaPage').classList.add('active');
        animateElements();
      } else if (page === 'transaksi') {
        document.getElementById('transaksiPage').classList.add('active');
        loadOrderHistory();
        anime({
          targets: '.order-card',
          opacity: [0, 1],
          translateX: [-30, 0],
          duration: 500,
          delay: anime.stagger(100),
          easing: 'easeOutQuad'
        });
      }

      // Scroll to top
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    // Animate Elements
    function animateElements() {
      // Animate carousel
      anime({
        targets: '.carousel',
        opacity: [0, 1],
        translateY: [-20, 0],
        duration: 800,
        easing: 'easeOutQuad'
      });

      // Animate search box
      anime({
        targets: '.search-box',
        opacity: [0, 1],
        scale: [0.9, 1],
        duration: 600,
        delay: 200,
        easing: 'easeOutQuad'
      });

      // Animate section titles
      anime({
        targets: '.section-title',
        opacity: [0, 1],
        translateX: [-30, 0],
        duration: 600,
        delay: anime.stagger(200, { start: 400 }),
        easing: 'easeOutQuad'
      });

      // Animate category cards
      anime({
        targets: '.category-card',
        opacity: [0, 1],
        scale: [0.8, 1],
        duration: 600,
        delay: anime.stagger(100, { start: 600 }),
        easing: 'easeOutElastic(1, .6)'
      });

      // Animate menu cards
      anime({
        targets: '.menu-card',
        opacity: [0, 1],
        translateY: [30, 0],
        duration: 700,
        delay: anime.stagger(80, { start: 800 }),
        easing: 'easeOutQuad'
      });
    }

    // Add hover animations to menu cards
    document.addEventListener('DOMContentLoaded', function () {
      initApp();

      // Add pulse animation to terlaris badges
      setInterval(() => {
        anime({
          targets: '.badge-terlaris',
          scale: [1, 1.1, 1],
          duration: 1000,
          easing: 'easeInOutQuad'
        });
      }, 3000);
    });

    // Animate modals when shown
    document.getElementById('menuModal').addEventListener('shown.bs.modal', function () {
      anime({
        targets: '#menuModal .modal-content',
        opacity: [0, 1],
        scale: [0.8, 1],
        duration: 400,
        easing: 'easeOutQuad'
      });
    });

    document.getElementById('paymentModal').addEventListener('shown.bs.modal', function () {
      anime({
        targets: '.qr-code i',
        rotate: [0, 360],
        duration: 1000,
        easing: 'easeInOutQuad'
      });
    });

    document.getElementById('confirmationModal').addEventListener('shown.bs.modal', function () {
      anime({
        targets: '.alert-success',
        opacity: [0, 1],
        scale: [0.8, 1],
        duration: 500,
        easing: 'easeOutElastic(1, .8)'
      });

      anime({
        targets: '.qr-code i',
        scale: [0, 1],
        rotate: [-180, 0],
        duration: 800,
        delay: 200,
        easing: 'easeOutElastic(1, .6)'
      });
    });

    // Add ripple effect to buttons
    document.addEventListener('click', function (e) {
      if (e.target.classList.contains('btn') || e.target.closest('.btn')) {
        const button = e.target.classList.contains('btn') ? e.target : e.target.closest('.btn');
        const rect = button.getBoundingClientRect();
        const ripple = document.createElement('span');
        const size = Math.max(rect.width, rect.height);
        const x = e.clientX - rect.left - size / 2;
        const y = e.clientY - rect.top - size / 2;

        ripple.style.cssText = `
                    position: absolute;
                    border-radius: 50%;
                    background: rgba(255, 255, 255, 0.6);
                    width: ${size}px;
                    height: ${size}px;
                    left: ${x}px;
                    top: ${y}px;
                    pointer-events: none;
                    transform: scale(0);
                `;

        button.style.position = 'relative';
        button.style.overflow = 'hidden';
        button.appendChild(ripple);

        anime({
          targets: ripple,
          scale: [0, 2],
          opacity: [1, 0],
          duration: 600,
          easing: 'easeOutQuad',
          complete: () => ripple.remove()
        });
      }
    });
  </script>
</body>

</html>
