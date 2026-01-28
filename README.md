
html_content = '''<!DOCTYPE html>
<html lang="ht">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Boutik Manager</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #6366f1;
            --primary-dark: #4f46e5;
            --secondary: #ec4899;
            --success: #10b981;
            --warning: #f59e0b;
            --danger: #ef4444;
            --dark: #1e293b;
            --light: #f8fafc;
            --gray: #64748b;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }
        
        /* Mobile Container */
        .mobile-container {
            max-width: 480px;
            margin: 0 auto;
            background: var(--light);
            min-height: 100vh;
            position: relative;
            box-shadow: 0 0 50px rgba(0,0,0,0.3);
        }
        
        /* Login Screen */
        .login-screen {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 40px 30px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }
        
        .logo {
            font-size: 80px;
            margin-bottom: 20px;
            animation: float 3s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
        
        .login-screen h1 {
            font-size: 28px;
            margin-bottom: 10px;
            text-align: center;
        }
        
        .login-screen p {
            opacity: 0.9;
            margin-bottom: 40px;
            text-align: center;
        }
        
        .role-selector {
            display: flex;
            gap: 15px;
            margin-bottom: 30px;
            width: 100%;
        }
        
        .role-btn {
            flex: 1;
            padding: 20px;
            border: 2px solid rgba(255,255,255,0.3);
            background: rgba(255,255,255,0.1);
            border-radius: 15px;
            color: white;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
        }
        
        .role-btn.active {
            background: white;
            color: var(--primary);
            border-color: white;
            transform: scale(1.05);
        }
        
        .role-btn i {
            font-size: 30px;
            margin-bottom: 10px;
            display: block;
        }
        
        .input-group {
            width: 100%;
            margin-bottom: 20px;
        }
        
        .input-group input {
            width: 100%;
            padding: 18px 20px;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            background: rgba(255,255,255,0.95);
            outline: none;
        }
        
        .btn-primary {
            width: 100%;
            padding: 18px;
            border: none;
            border-radius: 12px;
            background: white;
            color: var(--primary);
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
            transition: transform 0.2s;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }
        
        .btn-primary:active {
            transform: scale(0.98);
        }
        
        /* Main App */
        .app-container {
            display: none;
            min-height: 100vh;
            background: #f1f5f9;
        }
        
        /* Header */
        .header {
            background: white;
            padding: 20px;
            box-shadow: 0 2px 20px rgba(0,0,0,0.08);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .header-top {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .user-info h2 {
            font-size: 20px;
            color: var(--dark);
        }
        
        .user-info p {
            color: var(--gray);
            font-size: 14px;
        }
        
        .notification-btn {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: var(--light);
            border: none;
            font-size: 20px;
            color: var(--dark);
            cursor: pointer;
            position: relative;
        }
        
        .badge {
            position: absolute;
            top: -5px;
            right: -5px;
            background: var(--danger);
            color: white;
            width: 22px;
            height: 22px;
            border-radius: 50%;
            font-size: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
        }
        
        /* Stats Cards */
        .stats-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .stat-card {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            padding: 20px;
            border-radius: 16px;
            color: white;
            box-shadow: 0 10px 30px rgba(99, 102, 241, 0.3);
        }
        
        .stat-card:nth-child(2) {
            background: linear-gradient(135deg, var(--secondary) 0%, #be185d 100%);
            box-shadow: 0 10px 30px rgba(236, 72, 153, 0.3);
        }
        
        .stat-card:nth-child(3) {
            background: linear-gradient(135deg, var(--success) 0%, #059669 100%);
            box-shadow: 0 10px 30px rgba(16, 185, 129, 0.3);
        }
        
        .stat-card:nth-child(4) {
            background: linear-gradient(135deg, var(--warning) 0%, #d97706 100%);
            box-shadow: 0 10px 30px rgba(245, 158, 11, 0.3);
        }
        
        .stat-card h3 {
            font-size: 12px;
            opacity: 0.9;
            margin-bottom: 8px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .stat-card .value {
            font-size: 28px;
            font-weight: 700;
        }
        
        /* Quick Actions */
        .quick-actions {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin-bottom: 25px;
        }
        
        .action-btn {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            padding: 15px 10px;
            background: white;
            border: none;
            border-radius: 16px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }
        
        .action-btn:active {
            transform: scale(0.95);
        }
        
        .action-btn i {
            width: 50px;
            height: 50px;
            border-radius: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
            color: white;
        }
        
        .action-btn span {
            font-size: 12px;
            color: var(--dark);
            font-weight: 500;
        }
        
        .bg-primary { background: var(--primary); }
        .bg-success { background: var(--success); }
        .bg-warning { background: var(--warning); }
        .bg-secondary { background: var(--secondary); }
        
        /* Section Title */
        .section-title {
            font-size: 18px;
            font-weight: 600;
            color: var(--dark);
            margin-bottom: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .see-all {
            font-size: 14px;
            color: var(--primary);
            text-decoration: none;
            font-weight: 500;
        }
        
        /* Product List */
        .products-section {
            background: white;
            padding: 20px;
            border-radius: 20px 20px 0 0;
            min-height: 400px;
        }
        
        .product-item {
            display: flex;
            align-items: center;
            padding: 15px;
            background: var(--light);
            border-radius: 12px;
            margin-bottom: 12px;
            transition: all 0.3s;
        }
        
        .product-item:active {
            transform: scale(0.98);
            background: #e2e8f0;
        }
        
        .product-img {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 24px;
            margin-right: 15px;
        }
        
        .product-info {
            flex: 1;
        }
        
        .product-info h4 {
            font-size: 16px;
            color: var(--dark);
            margin-bottom: 4px;
        }
        
        .product-info p {
            font-size: 14px;
            color: var(--gray);
        }
        
        .product-stock {
            text-align: right;
        }
        
        .stock-number {
            font-size: 20px;
            font-weight: 700;
            color: var(--success);
        }
        
        .stock-label {
            font-size: 12px;
            color: var(--gray);
        }
        
        .low-stock .stock-number {
            color: var(--danger);
        }
        
        /* Bottom Navigation */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100%;
            max-width: 480px;
            background: white;
            display: flex;
            justify-content: space-around;
            padding: 15px 0 25px;
            box-shadow: 0 -5px 30px rgba(0,0,0,0.1);
            border-radius: 20px 20px 0 0;
        }
        
        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 5px;
            background: none;
            border: none;
            color: var(--gray);
            font-size: 12px;
            cursor: pointer;
            transition: all 0.3s;
            padding: 5px 15px;
        }
        
        .nav-item.active {
            color: var(--primary);
        }
        
        .nav-item i {
            font-size: 24px;
        }
        
        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 1000;
            justify-content: center;
            align-items: flex-end;
        }
        
        .modal-content {
            background: white;
            width: 100%;
            max-width: 480px;
            border-radius: 25px 25px 0 0;
            padding: 30px;
            animation: slideUp 0.3s ease;
        }
        
        @keyframes slideUp {
            from { transform: translateY(100%); }
            to { transform: translateY(0); }
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
        }
        
        .modal-header h3 {
            font-size: 22px;
            color: var(--dark);
        }
        
        .close-btn {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            border: none;
            background: var(--light);
            font-size: 20px;
            cursor: pointer;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: var(--dark);
            font-weight: 500;
            font-size: 14px;
        }
        
        .form-group input, .form-group select {
            width: 100%;
            padding: 15px;
            border: 2px solid #e2e8f0;
            border-radius: 12px;
            font-size: 16px;
            outline: none;
            transition: border-color 0.3s;
        }
        
        .form-group input:focus, .form-group select:focus {
            border-color: var(--primary);
        }
        
        .quantity-selector {
            display: flex;
            align-items: center;
            gap: 20px;
        }
        
        .qty-btn {
            width: 50px;
            height: 50px;
            border-radius: 12px;
            border: 2px solid var(--primary);
            background: white;
            color: var(--primary);
            font-size: 24px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .qty-display {
            font-size: 28px;
            font-weight: 700;
            color: var(--dark);
            min-width: 60px;
            text-align: center;
        }
        
        /* Employee View Specific */
        .employee-only {
            display: none;
        }
        
        .owner-only {
            display: none;
        }
        
        .view-owner .owner-only {
            display: block;
        }
        
        .view-owner .employee-only {
            display: none;
        }
        
        .view-employee .employee-only {
            display: block;
        }
        
        .view-employee .owner-only {
            display: none;
        }
        
        /* Recent Sales */
        .sales-list {
            margin-top: 20px;
        }
        
        .sale-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            border-bottom: 1px solid #e2e8f0;
        }
        
        .sale-info h4 {
            font-size: 16px;
            color: var(--dark);
            margin-bottom: 4px;
        }
        
        .sale-info p {
            font-size: 13px;
            color: var(--gray);
        }
        
        .sale-amount {
            font-size: 18px;
            font-weight: 700;
            color: var(--success);
        }
        
        /* Animations */
        .fade-in {
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Toast Notification */
        .toast {
            position: fixed;
            top: 100px;
            left: 50%;
            transform: translateX(-50%) translateY(-100px);
            background: var(--dark);
            color: white;
            padding: 15px 30px;
            border-radius: 50px;
            font-weight: 500;
            opacity: 0;
            transition: all 0.3s;
            z-index: 2000;
        }
        
        .toast.show {
            opacity: 1;
            transform: translateX(-50%) translateY(0);
        }
        
        .toast.success {
            background: var(--success);
        }
        
        .toast.error {
            background: var(--danger);
        }
    </style>
</head>
<body>
    <div class="mobile-container">
        <!-- Login Screen -->
        <div class="login-screen" id="loginScreen">
            <div class="logo">
                <i class="fas fa-store"></i>
            </div>
            <h1>Boutik Manager</h1>
            <p>Jere boutik ou nenpòt kote, nenpòt lè</p>
            
            <div class="role-selector">
                <button class="role-btn active" onclick="selectRole('owner')">
                    <i class="fas fa-crown"></i>
                    Pwopriyetè
                </button>
                <button class="role-btn" onclick="selectRole('employee')">
                    <i class="fas fa-user-tie"></i>
                    Anplwaye
                </button>
            </div>
            
            <div class="input-group">
                <input type="email" placeholder="Imèl ou" id="emailInput" value="boss@boutik.com">
            </div>
            <div class="input-group">
                <input type="password" placeholder="Modpas" id="passwordInput" value="123456">
            </div>
            
            <button class="btn-primary" onclick="login()">
                <i class="fas fa-sign-in-alt"></i> Konekte
            </button>
        </div>
        
        <!-- Main App -->
        <div class="app-container" id="appContainer">
            <!-- Header -->
            <div class="header">
                <div class="header-top">
                    <div class="user-info">
                        <h2 id="userName">John Doe</h2>
                        <p id="userRole">Pwopriyetè</p>
                    </div>
                    <button class="notification-btn">
                        <i class="fas fa-bell"></i>
                        <span class="badge">3</span>
                    </button>
                </div>
                
                <!-- Stats -->
                <div class="stats-container owner-only">
                    <div class="stat-card">
                        <h3>Vant Jodi a</h3>
                        <div class="value" id="todaySales">12,500 G</div>
                    </div>
                    <div class="stat-card">
                        <h3>Benefis</h3>
                        <div class="value" id="todayProfit">4,200 G</div>
                    </div>
                    <div class="stat-card">
                        <h3>Tranzaksyon</h3>
                        <div class="value">28</div>
                    </div>
                    <div class="stat-card">
                        <h3>En Stok</h3>
                        <div class="value">145</div>
                    </div>
                </div>
                
                <!-- Employee Stats -->
                <div class="stats-container employee-only">
                    <div class="stat-card">
                        <h3>Vant Ou Jodi a</h3>
                        <div class="value">3,200 G</div>
                    </div>
                    <div class="stat-card">
                        <h3>Komisyon</h3>
                        <div class="value">320 G</div>
                    </div>
                </div>
            </div>
            
            <!-- Quick Actions -->
            <div style="padding: 20px;">
                <div class="quick-actions">
                    <button class="action-btn" onclick="openModal('saleModal')">
                        <i class="fas fa-cash-register bg-success"></i>
                        <span>Nouvo Vant</span>
                    </button>
                    <button class="action-btn owner-only" onclick="openModal('productModal')">
                        <i class="fas fa-plus bg-primary"></i>
                        <span>Ajoute Pwodwi</span>
                    </button>
                    <button class="action-btn" onclick="showToast('Fonksyonalite nan devlopman', 'info')">
                        <i class="fas fa-box bg-warning"></i>
                        <span>Envantè</span>
                    </button>
                    <button class="action-btn owner-only" onclick="showToast('Rapò detaye disponib nan vèsyon peye a', 'info')">
                        <i class="fas fa-chart-line bg-secondary"></i>
                        <span>Rapò</span>
                    </button>
                </div>
                
                <!-- Products Section -->
                <div class="section-title">
                    <span>Pwodwi Popilè</span>
                    <a href="#" class="see-all">Wè tout</a>
                </div>
            </div>
            
            <div class="products-section">
                <div id="productList">
                    <div class="product-item">
                        <div class="product-img">
                            <i class="fas fa-tshirt"></i>
                        </div>
                        <div class="product-info">
                            <h4>T-shirt Nike</h4>
                            <p>1,500 G • Kategori: Rad</p>
                        </div>
                        <div class="product-stock">
                            <div class="stock-number">24</div>
                            <div class="stock-label">An stok</div>
                        </div>
                    </div>
                    
                    <div class="product-item">
                        <div class="product-img" style="background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);">
                            <i class="fas fa-shoe-prints"></i>
                        </div>
                        <div class="product-info">
                            <h4>Soulye Sport</h4>
                            <p>3,500 G • Kategori: Soulye</p>
                        </div>
                        <div class="product-stock">
                            <div class="stock-number">12</div>
                            <div class="stock-label">An stok</div>
                        </div>
                    </div>
                    
                    <div class="product-item low-stock">
                        <div class="product-img" style="background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);">
                            <i class="fas fa-mobile-alt"></i>
                        </div>
                        <div class="product-info">
                            <h4>Earbuds Bluetooth</h4>
                            <p>2,800 G • Kategori: Elektwonik</p>
                        </div>
                        <div class="product-stock">
                            <div class="stock-number">3</div>
                            <div class="stock-label">Piti ki rete!</div>
                        </div>
                    </div>
                    
                    <div class="product-item">
                        <div class="product-img" style="background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);">
                            <i class="fas fa-shopping-bag"></i>
                        </div>
                        <div class="product-info">
                            <h4>Sak Main</h4>
                            <p>4,200 G • Kategori: Akseswa</p>
                        </div>
                        <div class="product-stock">
                            <div class="stock-number">8</div>
                            <div class="stock-label">An stok</div>
                        </div>
                    </div>
                </div>
                
                <!-- Recent Sales -->
                <div class="section-title" style="margin-top: 30px;">
                    <span>Dènye Vant yo</span>
                    <a href="#" class="see-all">Wè tout</a>
                </div>
                
                <div class="sales-list">
                    <div class="sale-item">
                        <div class="sale-info">
                            <h4>T-shirt Nike x2</h4>
                            <p>14:30 • Anplwaye: Marie</p>
                        </div>
                        <div class="sale-amount">3,000 G</div>
                    </div>
                    <div class="sale-item">
                        <div class="sale-info">
                            <h4>Soulye Sport x1</h4>
                            <p>14:15 • Anplwaye: Jean</p>
                        </div>
                        <div class="sale-amount">3,500 G</div>
                    </div>
                    <div class="sale-item">
                        <div class="sale-info">
                            <h4>Sak Main x1</h4>
                            <p>13:45 • Anplwaye: Marie</p>
                        </div>
                        <div class="sale-amount">4,200 G</div>
                    </div>
                </div>
            </div>
            
            <!-- Bottom Navigation -->
            <div class="bottom-nav">
                <button class="nav-item active" onclick="switchTab('home')">
                    <i class="fas fa-home"></i>
                    <span>Akèy</span>
                </button>
                <button class="nav-item" onclick="switchTab('products')">
                    <i class="fas fa-box"></i>
                    <span>Pwodwi</span>
                </button>
                <button class="nav-item owner-only" onclick="switchTab('reports')">
                    <i class="fas fa-chart-pie"></i>
                    <span>Rapò</span>
                </button>
                <button class="nav-item" onclick="switchTab('profile')">
                    <i class="fas fa-user"></i>
                    <span>Pwofil</span>
                </button>
            </div>
        </div>
        
        <!-- Sale Modal -->
        <div class="modal" id="saleModal">
            <div class="modal-content">
                <div class="modal-header">
                    <h3>Nouvo Vant</h3>
                    <button class="close-btn" onclick="closeModal('saleModal')">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
                
                <div class="form-group">
                    <label>Chwazi Pwodwi</label>
                    <select id="saleProduct">
                        <option value="">-- Chwazi yon pwodwi --</option>
                        <option value="tshirt" data-price="1500">T-shirt Nike - 1,500 G</option>
                        <option value="shoes" data-price="3500">Soulye Sport - 3,500 G</option>
                        <option value="earbuds" data-price="2800">Earbuds Bluetooth - 2,800 G</option>
                        <option value="bag" data-price="4200">Sak Main - 4,200 G</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label>Kantite</label>
                    <div class="quantity-selector">
                        <button class="qty-btn" onclick="changeQty(-1)">-</button>
                        <div class="qty-display" id="qtyDisplay">1</div>
                        <button class="qty-btn" onclick="changeQty(1)">+</button>
                    </div>
                </div>
                
                <div class="form-group">
                    <label>Total: <span id="totalAmount" style="font-size: 24px; color: var(--primary); font-weight: 700;">0 G</span></label>
                </div>
                
                <button class="btn-primary" onclick="processSale()" style="margin-top: 10px;">
                    <i class="fas fa-check"></i> Konfime Vant
                </button>
            </div>
        </div>
        
        <!-- Add Product Modal -->
        <div class="modal" id="productModal">
            <div class="modal-content">
                <div class="modal-header">
                    <h3>Ajoute Nouvo Pwodwi</h3>
                    <button class="close-btn" onclick="closeModal('productModal')">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
                
                <div class="form-group">
                    <label>Non Pwodwi a</label>
                    <input type="text" placeholder="Ekri non pwodwi a" id="newProductName">
                </div>
                
                <div class="form-group">
                    <label>Pri (Gourdes)</label>
                    <input type="number" placeholder="0.00" id="newProductPrice">
                </div>
                
                <div class="form-group">
                    <label>Kantite An Stok</label>
                    <input type="number" placeholder="0" id="newProductStock">
                </div>
                
                <div class="form-group">
                    <label>Kategori</label>
                    <select id="newProductCategory">
                        <option>Rad</option>
                        <option>Soulye</option>
                        <option>Elektwonik</option>
                        <option>Akseswa</option>
                        <option>Lòt</option>
                    </select>
                </div>
                
                <button class="btn-primary" onclick="addProduct()" style="margin-top: 10px;">
                    <i class="fas fa-plus"></i> Ajoute Pwodwi
                </button>
            </div>
        </div>
        
        <!-- Toast -->
        <div class="toast" id="toast"></div>
    </div>
    
    <script>
        let currentRole = 'owner';
        let currentQty = 1;
        let currentPrice = 0;
        
        // Sample data
        let products = [
            { id: 1, name: 'T-shirt Nike', price: 1500, stock: 24, category: 'Rad', icon: 'tshirt', color: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)' },
            { id: 2, name: 'Soulye Sport', price: 3500, stock: 12, category: 'Soulye', icon: 'shoe-prints', color: 'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)' },
            { id: 3, name: 'Earbuds Bluetooth', price: 2800, stock: 3, category: 'Elektwonik', icon: 'mobile-alt', color: 'linear-gradient(135deg, #4facfe 0%, #00f2fe 100%)' },
            { id: 4, name: 'Sak Main', price: 4200, stock: 8, category: 'Akseswa', icon: 'shopping-bag', color: 'linear-gradient(135deg, #43e97b 0%, #38f9d7 100%)' }
        ];
        
        let sales = [];
        let todayTotal = 12500;
        
        function selectRole(role) {
            currentRole = role;
            document.querySelectorAll('.role-btn').forEach(btn => btn.classList.remove('active'));
            event.target.closest('.role-btn').classList.add('active');
            
            if (role === 'owner') {
                document.getElementById('emailInput').value = 'boss@boutik.com';
            } else {
                document.getElementById('emailInput').value = 'employee@boutik.com';
            }
        }
        
        function login() {
            const appContainer = document.getElementById('appContainer');
            const loginScreen = document.getElementById('loginScreen');
            const userName = document.getElementById('userName');
            const userRole = document.getElementById('userRole');
            
            if (currentRole === 'owner') {
                userName.textContent = 'Boss';
                userRole.textContent = 'Pwopriyetè';
                appContainer.classList.add('view-owner');
                appContainer.classList.remove('view-employee');
            } else {
                userName.textContent = 'Marie';
                userRole.textContent = 'Anplwaye';
                appContainer.classList.add('view-employee');
                appContainer.classList.remove('view-owner');
            }
            
            loginScreen.style.display = 'none';
            appContainer.style.display = 'block';
            appContainer.classList.add('fade-in');
            
            showToast('Byenveni nan Boutik Manager!', 'success');
        }
        
        function openModal(modalId) {
            document.getElementById(modalId).style.display = 'flex';
            if (modalId === 'saleModal') {
                currentQty = 1;
                document.getElementById('qtyDisplay').textContent = currentQty;
                calculateTotal();
            }
        }
        
        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }
        
        function changeQty(delta) {
            currentQty += delta;
            if (currentQty < 1) currentQty = 1;
            document.getElementById('qtyDisplay').textContent = currentQty;
            calculateTotal();
        }
        
        document.getElementById('saleProduct').addEventListener('change', function() {
            const selected = this.options[this.selectedIndex];
            currentPrice = parseInt(selected.getAttribute('data-price')) || 0;
            calculateTotal();
        });
        
        function calculateTotal() {
            const total = currentPrice * currentQty;
            document.getElementById('totalAmount').textContent = total.toLocaleString() + ' G';
        }
        
        function processSale() {
            const productSelect = document.getElementById('saleProduct');
            if (!productSelect.value) {
                showToast('Tanpri chwazi yon pwodwi', 'error');
                return;
            }
            
            const productName = productSelect.options[productSelect.selectedIndex].text.split(' - ')[0];
            const total = currentPrice * currentQty;
            
            // Update today's sales
            todayTotal += total;
            document.getElementById('todaySales').textContent = todayTotal.toLocaleString() + ' G';
            
            // Add to sales list
            const salesList = document.querySelector('.sales-list');
            const newSale = document.createElement('div');
            newSale.className = 'sale-item';
            newSale.innerHTML = `
                <div class="sale-info">
                    <h4>${productName} x${currentQty}</h4>
                    <p>${new Date().toLocaleTimeString('ht-HT', {hour: '2-digit', minute:'2-digit'})} • Anplwaye: ${currentRole === 'owner' ? 'Boss' : 'Marie'}</p>
                </div>
                <div class="sale-amount">${total.toLocaleString()} G</div>
            `;
            salesList.insertBefore(newSale, salesList.firstChild);
            
            closeModal('saleModal');
            showToast('Vant anrejistre avèk siksè!', 'success');
            
            // Reset form
            productSelect.value = '';
            currentQty = 1;
            document.getElementById('qtyDisplay').textContent = currentQty;
            calculateTotal();
        }
        
        function addProduct() {
            const name = document.getElementById('newProductName').value;
            const price = parseInt(document.getElementById('newProductPrice').value);
            const stock = parseInt(document.getElementById('newProductStock').value);
            const category = document.getElementById('newProductCategory').value;
            
            if (!name || !price || !stock) {
                showToast('Tanpli ranpli tout chan yo', 'error');
                return;
            }
            
            const newProduct = {
                id: products.length + 1,
                name: name,
                price: price,
                stock: stock,
                category: category,
                icon: 'box',
                color: 'linear-gradient(135deg, #fa709a 0%, #fee140 100%)'
            };
            
            products.push(newProduct);
            
            // Add to product list
            const productList = document.getElementById('productList');
            const productItem = document.createElement('div');
            productItem.className = 'product-item';
            productItem.innerHTML = `
                <div class="product-img" style="background: ${newProduct.color};">
                    <i class="fas fa-${newProduct.icon}"></i>
                </div>
                <div class="product-info">
                    <h4>${name}</h4>
                    <p>${price.toLocaleString()} G • Kategori: ${category}</p>
                </div>
                <div class="product-stock">
                    <div class="stock-number">${stock}</div>
                    <div class="stock-label">An stok</div>
                </div>
            `;
            productList.insertBefore(productItem, productList.firstChild);
            
            closeModal('productModal');
            showToast('Pwodwi ajoute avèk siksè!', 'success');
            
            // Reset form
            document.getElementById('newProductName').value = '';
            document.getElementById('newProductPrice').value = '';
            document.getElementById('newProductStock').value = '';
        }
        
        function switchTab(tab) {
            document.querySelectorAll('.nav-item').forEach(item => item.classList.remove('active'));
            event.target.closest('.nav-item').classList.add('active');
            
            if (tab !== 'home') {
                showToast('Tab sa a nan devlopman', 'info');
            }
        }
        
        function showToast(message, type = 'info') {
            const toast = document.getElementById('toast');
            toast.textContent = message;
            toast.className = 'toast show ' + type;
            
            setTimeout(() => {
                toast.classList.remove('show');
            }, 3000);
        }
        
        // Close modal when clicking outside
        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.style.display = 'none';
            }
        }
    </script>
</body>
</html>'''

# Save the file
with open('/mnt/kimi/output/boutik_manager_prototype.html', 'w', encoding='utf-8') as f:
    f.write(html_content)

print("✅ Pwototip la kreye avèk siksè!")
print("\n📁 Fichye a anrejistre nan: /mnt/kimi/output/boutik_manager_prototype.html")
print("\n🎯 Kijan pou w itilize l:")
print("1. Telechaje fichye a")
print("2. Ouvri l nan yon navigatè (Chrome, Safari, elatriye)")
print("3. Sou telefòn ou: itilize mòd 'Desktop Site' si bezwen")
print("4. Teste koneksyon kòm Pwopriyetè oswa Anplwaye")
