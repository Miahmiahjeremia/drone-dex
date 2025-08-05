<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Drone Drop Shipping: Drone-dex</title>
    <link href="https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Source Sans Pro', sans-serif;
            background-color: #121212;
            color: #e0e0e0;
            overflow-x: hidden;
        }
        
        .container {
            width: 100%;
            max-width: 1280px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header Styles */
        header {
            background-color: #1a1a1a;
            padding: 20px 0;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 28px;
            font-weight: 700;
            color: #64B5F6;
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 10px;
            font-size: 32px;
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 25px;
        }
        
        nav ul li a {
            color: #e0e0e0;
            text-decoration: none;
            font-weight: 600;
            font-size: 18px;
            transition: color 0.3s;
        }
        
        nav ul li a:hover {
            color: #64B5F6;
        }
        
        /* Main Content */
        main {
            padding: 40px 0;
        }
        
        .page-title {
            font-size: 36px;
            font-weight: 700;
            color: #ffffff;
            margin-bottom: 30px;
            text-align: center;
        }
        
        .page-subtitle {
            font-size: 20px;
            color: #bbbbbb;
            margin-bottom: 40px;
            text-align: center;
        }
        
        /* Tabs Styles */
        .tabs {
            display: flex;
            flex-wrap: wrap;
            margin-bottom: 30px;
            border-bottom: 2px solid #333;
        }
        
        .tab {
            padding: 15px 25px;
            background-color: #1a1a1a;
            color: #e0e0e0;
            cursor: pointer;
            border: none;
            font-size: 18px;
            font-weight: 600;
            transition: all 0.3s;
            border-radius: 8px 8px 0 0;
            margin-right: 5px;
        }
        
        .tab:hover {
            background-color: #2a2a2a;
        }
        
        .tab.active {
            background-color: #64B5F6;
            color: #121212;
        }
        
        /* Tab Content */
        .tab-content {
            display: none;
            animation: fadeIn 0.5s;
        }
        
        .tab-content.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        /* Drone Cards */
        .drone-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }
        
        .drone-card {
            background-color: #1a1a1a;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .drone-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
        }
        
        .drone-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }
        
        .drone-info {
            padding: 20px;
        }
        
        .drone-name {
            font-size: 22px;
            font-weight: 700;
            color: #ffffff;
            margin-bottom: 10px;
        }
        
        .drone-type {
            font-size: 16px;
            color: #64B5F6;
            margin-bottom: 15px;
        }
        
        .drone-price {
            font-size: 20px;
            font-weight: 600;
            color: #4caf50;
            margin-bottom: 15px;
        }
        
        .drone-specs {
            margin-bottom: 15px;
        }
        
        .spec-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 16px;
        }
        
        .spec-label {
            color: #bbbbbb;
        }
        
        .spec-value {
            color: #e0e0e0;
            font-weight: 600;
        }
        
        .view-details-btn {
            background-color: #64B5F6;
            color: #121212;
            border: none;
            padding: 10px 15px;
            border-radius: 6px;
            font-weight: 600;
            cursor: pointer;
            width: 100%;
            transition: background-color 0.3s;
            font-size: 16px;
        }
        
        .view-details-btn:hover {
            background-color: #42a5f5;
        }
        
        /* Drone Detail Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            z-index: 2000;
            overflow-y: auto;
        }
        
        .modal-content {
            background-color: #1a1a1a;
            margin: 50px auto;
            padding: 30px;
            width: 90%;
            max-width: 900px;
            border-radius: 12px;
            position: relative;
            animation: slideIn 0.5s;
        }
        
        @keyframes slideIn {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        .close-modal {
            position: absolute;
            top: 20px;
            right: 20px;
            font-size: 28px;
            color: #e0e0e0;
            cursor: pointer;
            transition: color 0.3s;
        }
        
        .close-modal:hover {
            color: #64B5F6;
        }
        
        .modal-header {
            display: flex;
            margin-bottom: 30px;
        }
        
        .modal-image {
            width: 40%;
            border-radius: 8px;
            object-fit: cover;
        }
        
        .modal-title-section {
            margin-left: 30px;
            flex: 1;
        }
        
        .modal-drone-name {
            font-size: 32px;
            font-weight: 700;
            color: #ffffff;
            margin-bottom: 10px;
        }
        
        .modal-drone-type {
            font-size: 18px;
            color: #64B5F6;
            margin-bottom: 15px;
        }
        
        .modal-drone-price {
            font-size: 28px;
            font-weight: 600;
            color: #4caf50;
            margin-bottom: 20px;
        }
        
        .manufacturer-info {
            background-color: #2a2a2a;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        
        .manufacturer-name {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 5px;
        }
        
        .manufacturer-website {
            color: #64B5F6;
            text-decoration: none;
            font-size: 16px;
        }
        
        .manufacturer-website:hover {
            text-decoration: underline;
        }
        
        .modal-specs {
            margin-bottom: 30px;
        }
        
        .modal-specs h3 {
            font-size: 22px;
            margin-bottom: 15px;
            color: #ffffff;
        }
        
        .spec-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
        }
        
        .spec-item-modal {
            background-color: #2a2a2a;
            padding: 12px;
            border-radius: 8px;
        }
        
        .spec-label-modal {
            font-size: 14px;
            color: #bbbbbb;
            margin-bottom: 5px;
        }
        
        .spec-value-modal {
            font-size: 16px;
            font-weight: 600;
            color: #e0e0e0;
        }
        
        .drone-description {
            margin-bottom: 30px;
        }
        
        .drone-description h3 {
            font-size: 22px;
            margin-bottom: 15px;
            color: #ffffff;
        }
        
        .drone-description p {
            font-size: 16px;
            line-height: 1.6;
            color: #e0e0e0;
        }
        
        .video-section {
            margin-bottom: 30px;
        }
        
        .video-section h3 {
            font-size: 22px;
            margin-bottom: 15px;
            color: #ffffff;
        }
        
        .video-placeholder {
            background-color: #2a2a2a;
            height: 200px;
            border-radius: 8px;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #bbbbbb;
            font-size: 18px;
        }
        
        .buy-now-btn {
            background-color: #4caf50;
            color: #ffffff;
            border: none;
            padding: 15px 30px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            font-size: 18px;
            display: block;
            margin: 0 auto;
            transition: background-color 0.3s;
        }
        
        .buy-now-btn:hover {
            background-color: #45a049;
        }
        
        /* Footer */
        footer {
            background-color: #1a1a1a;
            padding: 30px 0;
            text-align: center;
            margin-top: 60px;
        }
        
        .footer-text {
            color: #bbbbbb;
            font-size: 16px;
        }
        
        /* Price Badge */
        .price-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: #4caf50;
            color: white;
            padding: 5px 10px;
            border-radius: 4px;
            font-weight: 600;
            font-size: 14px;
        }
        
        .drone-card {
            position: relative;
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <i class="fas fa-helicopter"></i>
                    Drone Drop Shipping: Drone-dex
                </div>
                <nav>
                    <ul>
                        <li><a href="#home">Home</a></li>
                        <li><a href="#about">About</a></li>
                        <li><a href="#contact">Contact</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>
    
    <main>
        <div class="container">
            <h1 class="page-title">Drone Drop Shipping Catalog</h1>
            <p class="page-subtitle">Explore our comprehensive collection of professional drones for all your needs</p>
            
            <div class="tabs">
                <button class="tab" data-tab="underwater">Underwater Drones</button>
                <button class="tab active" data-tab="racing">Racing Drones</button>
                <button class="tab" data-tab="fixed-wing">Fixed Wing Drones</button>
                <button class="tab" data-tab="dual-camera">Dual Camera Drones</button>
                <button class="tab" data-tab="thermal">Thermal Drones</button>
                <button class="tab" data-tab="mini-quad">Mini Quadcopters</button>
            </div>
            
            <!-- Underwater Drones Tab -->
            <div class="tab-content" id="underwater">
                <div class="drone-grid">
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/c96c53b406f8.png" alt="PowerVision PowerRay Underwater Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">PowerVision PowerRay</h3>
                            <p class="drone-type">Underwater Exploration Drone</p>
                            <p class="drone-price">$1,988</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Max Depth:</span>
                                    <span class="spec-value">98 ft</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Battery Life:</span>
                                    <span class="spec-value">4 hours</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">4K UHD</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="powerray">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/9cae6ec5a068.jpg" alt="Chasing Innovation Gladius Mini" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">Chasing Gladius Mini</h3>
                            <p class="drone-type">Compact Underwater Drone</p>
                            <p class="drone-price">$999</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Max Depth:</span>
                                    <span class="spec-value">330 ft</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Battery Life:</span>
                                    <span class="spec-value">2 hours</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">4K UHD</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="gladius">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/7058e24568c4.jpg" alt="Boxfish Research ROV" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">Boxfish Research ROV</h3>
                            <p class="drone-type">Professional Underwater Drone</p>
                            <p class="drone-price">$25,000</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Max Depth:</span>
                                    <span class="spec-value">1,640 ft</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Battery Life:</span>
                                    <span class="spec-value">4-6 hours</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">Sony 4K</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="boxfish">View Details</button>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Racing Drones Tab -->
            <div class="tab-content active" id="racing">
                <div class="drone-grid">
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/01a74371f62e.jpg" alt="Nighthawk Pro Racing Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">Nighthawk Pro</h3>
                            <p class="drone-type">Professional Racing Drone</p>
                            <p class="drone-price">$599</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Max Speed:</span>
                                    <span class="spec-value">85 mph</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">10-12 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">1080p FPV</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="nighthawk">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/9d79338fea5b.jpg" alt="EMAX Hawk Pro Racing Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">EMAX Hawk Pro</h3>
                            <p class="drone-type">5-Inch Racing Drone</p>
                            <p class="drone-price">$429</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Max Speed:</span>
                                    <span class="spec-value">80 mph</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">8-10 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">Caddx Turtle V2</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="emax">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/d044a97709da.jpg" alt="TBS Source One Racing Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">TBS Source One</h3>
                            <p class="drone-type">FPV Racing Drone</p>
                            <p class="drone-price">$299</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Max Speed:</span>
                                    <span class="spec-value">75 mph</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">7-9 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">Runcam Swift 3</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="tbs">View Details</button>
                        </div>
                    </div>
                    
                    <!-- New Racing Drones -->
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/35b124d6770d.jpg" alt="HGLRC Sector E5 Racing Drone" class="drone-image">
                        <div class="price-badge">$800-1000</div>
                        <div class="drone-info">
                            <h3 class="drone-name">HGLRC Sector E5</h3>
                            <p class="drone-type">Professional Racing Drone</p>
                            <p class="drone-price">$899</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Max Speed:</span>
                                    <span class="spec-value">90+ mph</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">6-8 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">Runcam Phoenix 2</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="hglrc">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/85fe861b779e.jpg" alt="Lumenier QAV-R 5X Racing Drone" class="drone-image">
                        <div class="price-badge">$1200-1800</div>
                        <div class="drone-info">
                            <h3 class="drone-name">Lumenier QAV-R 5X</h3>
                            <p class="drone-type">Professional Racing Drone</p>
                            <p class="drone-price">$1,499</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Max Speed:</span>
                                    <span class="spec-value">100+ mph</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">8-10 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">Runcam Swift 3</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="lumenier">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/80739a7e4d68.jpg" alt="Rotor Riot Ripper V2 Racing Drone" class="drone-image">
                        <div class="price-badge">$4000</div>
                        <div class="drone-info">
                            <h3 class="drone-name">Rotor Riot Ripper V2</h3>
                            <p class="drone-type">Professional Racing Drone</p>
                            <p class="drone-price">$3,999</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Max Speed:</span>
                                    <span class="spec-value">120+ mph</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">12-15 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">DJI FPV</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="rotorriot">View Details</button>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Fixed Wing Drones Tab -->
            <div class="tab-content" id="fixed-wing">
                <div class="drone-grid">
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/d4a8d2770093.jpg" alt="JOUAV CW-15 Fixed Wing Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">JOUAV CW-15</h3>
                            <p class="drone-type">VTOL Fixed Wing Drone</p>
                            <p class="drone-price">$25,000</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">90 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Range:</span>
                                    <span class="spec-value">30 km</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Payload:</span>
                                    <span class="spec-value">2.5 kg</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="jouav">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/3e089199026e.jpg" alt="Yangda YD6-1600 Fixed Wing Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">Yangda YD6-1600</h3>
                            <p class="drone-type">Long Endurance Drone</p>
                            <p class="drone-price">$18,000</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">160 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Range:</span>
                                    <span class="spec-value">200 km</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Payload:</span>
                                    <span class="spec-value">3 kg</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="yangda">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/c56d9ac8cf84.png" alt="Measur Drones Mapper Fixed Wing" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">Measur Mapper</h3>
                            <p class="drone-type">Mapping Fixed Wing Drone</p>
                            <p class="drone-price">$12,500</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">59 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Range:</span>
                                    <span class="spec-value">40 km</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">Sony RX1R II</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="measur">View Details</button>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Dual Camera Drones Tab -->
            <div class="tab-content" id="dual-camera">
                <div class="drone-grid">
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/672ae958ed70.jpeg" alt="E99 Pro Dual Camera Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">E99 Pro</h3>
                            <p class="drone-type">Dual Camera Drone</p>
                            <p class="drone-price">$199</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">15-18 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">Dual 4K</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Range:</span>
                                    <span class="spec-value">1.2 km</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="e99">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/d90c96fbad20.jpg" alt="Holy Stone HS720E Dual Camera Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">Holy Stone HS720E</h3>
                            <p class="drone-type">GPS Dual Camera Drone</p>
                            <p class="drone-price">$299</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">23 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">4K EIS + 1080p</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Range:</span>
                                    <span class="spec-value">1 km</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="holystone">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/ff6b6d5ec31d.jpeg" alt="SNAPTAIN SP510 Dual Camera Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">SNAPTAIN SP510</h3>
                            <p class="drone-type">Dual Camera Drone</p>
                            <p class="drone-price">$249</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">16 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">4K + 720p</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Range:</span>
                                    <span class="spec-value">120 m</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="snaptain">View Details</button>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Thermal Drones Tab -->
            <div class="tab-content" id="thermal">
                <div class="drone-grid">
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/9f56cd212c37.webp" alt="DJI Matrice 300 RTK Thermal Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">DJI Matrice 300 RTK</h3>
                            <p class="drone-type">Professional Thermal Drone</p>
                            <p class="drone-price">$15,999</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">55 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">Zenmuse H20T</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Range:</span>
                                    <span class="spec-value">15 km</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="matrice">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/11c1b00c60a7.jpg" alt="FLIR Vue Pro R Thermal Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">FLIR Vue Pro R</h3>
                            <p class="drone-type">Thermal Imaging Drone</p>
                            <p class="drone-price">$1,999</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Resolution:</span>
                                    <span class="spec-value">640x512</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Thermal Sensitivity:</span>
                                    <span class="spec-value"><30mK</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Frame Rate:</span>
                                    <span class="spec-value">30Hz</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="flir">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/712cfe209f7e.jpg" alt="Teledyne FLIR SIRAS Professional Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">Teledyne FLIR SIRAS</h3>
                            <p class="drone-type">Professional Thermal Drone</p>
                            <p class="drone-price">$7,995</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">31 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">Thermal + RGB</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Weight:</span>
                                    <span class="spec-value">2.4 kg</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="siras">View Details</button>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Mini Quadcopters Tab -->
            <div class="tab-content" id="mini-quad">
                <div class="drone-grid">
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/98e10ad9ba40.jpg" alt="DJI Mini 2 Quadcopter" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">DJI Mini 2</h3>
                            <p class="drone-type">Mini Quadcopter Drone</p>
                            <p class="drone-price">$449</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Weight:</span>
                                    <span class="spec-value">249g</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">31 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">4K HDR</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="mini2">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/fe6224049d21.jpg" alt="Holy Stone HS110D Mini Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">Holy Stone HS110D</h3>
                            <p class="drone-type">Mini FPV Drone</p>
                            <p class="drone-price">$129</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Weight:</span>
                                    <span class="spec-value">115g</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">10 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">720p HD</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="hs110d">View Details</button>
                        </div>
                    </div>
                    
                    <div class="drone-card">
                        <img src="https://sfile.chatglm.cn/images-ppt/8359a27559fa.jpg" alt="Ryze Tello Mini Drone" class="drone-image">
                        <div class="drone-info">
                            <h3 class="drone-name">Ryze Tello</h3>
                            <p class="drone-type">Mini Programmable Drone</p>
                            <p class="drone-price">$99</p>
                            <div class="drone-specs">
                                <div class="spec-item">
                                    <span class="spec-label">Weight:</span>
                                    <span class="spec-value">80g</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Flight Time:</span>
                                    <span class="spec-value">13 min</span>
                                </div>
                                <div class="spec-item">
                                    <span class="spec-label">Camera:</span>
                                    <span class="spec-value">5MP HD</span>
                                </div>
                            </div>
                            <button class="view-details-btn" data-drone="tello">View Details</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
    
    <!-- Drone Detail Modal -->
    <div class="modal" id="droneModal">
        <div class="modal-content">
            <span class="close-modal">×</span>
            <div class="modal-header">
                <img src="" alt="Drone Image" class="modal-image" id="modalImage">
                <div class="modal-title-section">
                    <h2 class="modal-drone-name" id="modalDroneName"></h2>
                    <p class="modal-drone-type" id="modalDroneType"></p>
                    <p class="modal-drone-price" id="modalDronePrice"></p>
                    <div class="manufacturer-info">
                        <p class="manufacturer-name" id="manufacturerName"></p>
                        <a href="#" class="manufacturer-website" id="manufacturerWebsite" target="_blank">Visit Manufacturer Website</a>
                    </div>
                </div>
            </div>
            
            <div class="modal-specs">
                <h3>Specifications</h3>
                <div class="spec-grid" id="specGrid">
                    <!-- Specs will be populated dynamically -->
                </div>
            </div>
            
            <div class="drone-description">
                <h3>Description</h3>
                <p id="droneDescription"></p>
            </div>
            
            <div class="video-section">
                <h3>Product Video</h3>
                <div class="video-placeholder">
                    <i class="fas fa-play-circle fa-3x"></i>
                    <p>5-second product video would be displayed here</p>
                </div>
            </div>
            
            <button class="buy-now-btn">Buy Now</button>
        </div>
    </div>
    
    <footer>
        <div class="container">
            <p class="footer-text">© 2023 Drone Drop Shipping: Drone-dex. All rights reserved.</p>
        </div>
    </footer>
    
    <script>
        // Drone data
        const droneData = {
            powerray: {
                name: "PowerVision PowerRay",
                type: "Underwater Exploration Drone",
                price: "$1,988",
                manufacturer: "PowerVision",
                website: "https://www.powervision.me",
                date: "2017",
                image: "https://sfile.chatglm.cn/images-ppt/c96c53b406f8.png",
                specs: {
                    "Max Depth": "98 ft (30 m)",
                    "Battery Life": "4 hours",
                    "Camera": "4K UHD",
                    "Connectivity": "Wi-Fi, Ethernet",
                    "Dimensions": "17.7 × 11.8 × 6.7 in",
                    "Weight": "8.4 lbs (3.8 kg)",
                    "Max Speed": "4.5 mph (2 m/s)",
                    "Lighting": "4500 lumens LED"
                },
                description: "The PowerVision PowerRay is a professional underwater drone designed for exploration, fishing, and photography. It features a 4K UHD camera with anti-shake technology, allowing you to capture stunning underwater footage. The PowerRay can dive to depths of up to 98 feet and has a battery life of 4 hours, making it perfect for extended underwater adventures."
            },
            gladius: {
                name: "Chasing Gladius Mini",
                type: "Compact Underwater Drone",
                price: "$999",
                manufacturer: "Chasing Innovation",
                website: "https://www.chasing.com",
                date: "2019",
                image: "https://sfile.chatglm.cn/images-ppt/9cae6ec5a068.jpg",
                specs: {
                    "Max Depth": "330 ft (100 m)",
                    "Battery Life": "2 hours",
                    "Camera": "4K UHD",
                    "Connectivity": "Wi-Fi, Tether",
                    "Dimensions": "15.4 × 9.8 × 5.5 in",
                    "Weight": "5.5 lbs (2.5 kg)",
                    "Max Speed": "4 knots",
                    "Lighting": "2x 1200 lumens LED"
                },
                description: "The Chasing Gladius Mini is a compact and portable underwater drone that offers professional features at an affordable price. It can dive to depths of up to 330 feet and features a 4K UHD camera for capturing high-quality underwater footage. The Gladius Mini is perfect for underwater photography, exploration, and marine research."
            },
            boxfish: {
                name: "Boxfish Research ROV",
                type: "Professional Underwater Drone",
                price: "$25,000",
                manufacturer: "Boxfish Robotics",
                website: "https://boxfishresearch.com",
                date: "2020",
                image: "https://sfile.chatglm.cn/images-ppt/7058e24568c4.jpg",
                specs: {
                    "Max Depth": "1,640 ft (500 m)",
                    "Battery Life": "4-6 hours",
                    "Camera": "Sony 4K",
                    "Connectivity": "Fiber Optic Tether",
                    "Dimensions": "23.6 × 18.9 × 14.2 in",
                    "Weight": "33 lbs (15 kg)",
                    "Max Speed": "3 knots",
                    "Lighting": "4x 5000 lumens LED"
                },
                description: "The Boxfish Research ROV is a professional-grade underwater drone designed for scientific research, underwater inspections, and marine surveys. It features a Sony 4K camera and can dive to depths of up to 1,640 feet. With its advanced stabilization system and powerful LED lighting, the Boxfish ROV delivers exceptional performance in challenging underwater environments."
            },
            nighthawk: {
                name: "Nighthawk Pro",
                type: "Professional Racing Drone",
                price: "$599",
                manufacturer: "Nighthawk",
                website: "https://nighthawkfpv.com",
                date: "2021",
                image: "https://sfile.chatglm.cn/images-ppt/01a74371f62e.jpg",
                specs: {
                    "Max Speed": "85 mph (137 km/h)",
                    "Flight Time": "10-12 min",
                    "Camera": "1080p FPV",
                    "Weight": "650g",
                    "Frame Size": "5 inches",
                    "Motors": "2207 2500kV",
                    "Battery": "6S 1300mAh LiPo",
                    "Controller": "FrSky Taranis X9D"
                },
                description: "The Nighthawk Pro is a high-performance racing drone designed for professional FPV pilots. With a top speed of 85 mph and a flight time of 10-12 minutes, it offers exceptional performance for competitive racing and freestyle flying. The drone features a durable carbon fiber frame and high-quality components for maximum reliability and performance."
            },
            emax: {
                name: "EMAX Hawk Pro",
                type: "5-Inch Racing Drone",
                price: "$429",
                manufacturer: "EMAX",
                website: "https://www.emax-usa.com",
                date: "2020",
                image: "https://sfile.chatglm.cn/images-ppt/9d79338fea5b.jpg",
                specs: {
                    "Max Speed": "80 mph (129 km/h)",
                    "Flight Time": "8-10 min",
                    "Camera": "Caddx Turtle V2",
                    "Weight": "580g",
                    "Frame Size": "5 inches",
                    "Motors": "Eco II 2207 2750kV",
                    "Battery": "6S 1300mAh LiPo",
                    "Controller": "EMAX Commander"
                },
                description: "The EMAX Hawk Pro is a versatile 5-inch racing drone that excels in both racing and freestyle applications. It features a lightweight yet durable carbon fiber frame and high-quality components for optimal performance. The Caddx Turtle V2 camera provides clear FPV footage, while the powerful ECO II motors deliver impressive speed and agility."
            },
            tbs: {
                name: "TBS Source One",
                type: "FPV Racing Drone",
                price: "$299",
                manufacturer: "Team BlackSheep",
                website: "https://www.team-blacksheep.com",
                date: "2019",
                image: "https://sfile.chatglm.cn/images-ppt/d044a97709da.jpg",
                specs: {
                    "Max Speed": "75 mph (121 km/h)",
                    "Flight Time": "7-9 min",
                    "Camera": "Runcam Swift 3",
                    "Weight": "550g",
                    "Frame Size": "5 inches",
                    "Motors": "TBS Motors 2207 2500kV",
                    "Battery": "6S 1300mAh LiPo",
                    "Controller": "TBS Tango 2"
                },
                description: "The TBS Source One is a popular FPV racing drone known for its durability and performance. It features a lightweight yet robust frame that can withstand crashes and rough landings. The drone is equipped with high-quality components, including TBS motors and a Runcam Swift 3 camera, making it an excellent choice for both beginners and experienced pilots."
            },
            hglrc: {
                name: "HGLRC Sector E5",
                type: "Professional Racing Drone",
                price: "$899",
                manufacturer: "HGLRC",
                website: "https://hglrc.com",
                date: "2022",
                image: "https://sfile.chatglm.cn/images-ppt/35b124d6770d.jpg",
                specs: {
                    "Max Speed": "90+ mph (145+ km/h)",
                    "Flight Time": "6-8 min",
                    "Camera": "Runcam Phoenix 2",
                    "Weight": "620g",
                    "Frame Size": "5 inches",
                    "Motors": "2207 2450KV",
                    "Battery": "1300mAh 6S LiPo",
                    "Controller": "HGLRC F7 Flight Controller"
                },
                description: "The HGLRC Sector E5 is a high-performance racing drone designed for competitive FPV racing. It features a durable carbon fiber frame and high-quality components for maximum speed and agility. The drone comes fully assembled and tuned, making it ready to race right out of the box."
            },
            lumenier: {
                name: "Lumenier QAV-R 5X",
                type: "Professional Racing Drone",
                price: "$1,499",
                manufacturer: "Lumenier",
                website: "https://lumenier.com",
                date: "2021",
                image: "https://sfile.chatglm.cn/images-ppt/85fe861b779e.jpg",
                specs: {
                    "Max Speed": "100+ mph (160+ km/h)",
                    "Flight Time": "8-10 min",
                    "Camera": "Runcam Swift 3",
                    "Weight": "600g",
                    "Frame Size": "5 inches",
                    "Motors": "2207 2550KV",
                    "Battery": "1550mAh 6S LiPo",
                    "Controller": "TBS Tango 2"
                },
                description: "The Lumenier QAV-R 5X is a premium racing drone built for professional pilots. It features a lightweight yet durable carbon fiber frame and top-of-the-line components for exceptional performance. The drone is designed for competitive racing and freestyle flying, offering unmatched speed and handling."
            },
            rotorriot: {
                name: "Rotor Riot Ripper V2",
                type: "Professional Racing Drone",
                price: "$3,999",
                manufacturer: "Rotor Riot",
                website: "https://rotorriot.com",
                date: "2023",
                image: "https://sfile.chatglm.cn/images-ppt/80739a7e4d68.jpg",
                specs: {
                    "Max Speed": "120+ mph (193+ km/h)",
                    "Flight Time": "12-15 min",
                    "Camera": "DJI FPV Camera",
                    "Weight": "950g",
                    "Frame Size": "7 inches",
                    "Motors": "2812 900KV",
                    "Battery": "2500mAh 6S LiPo",
                    "Controller": "TBS Tango 2",
                    "Special Features": "GPS Module, Long-Range FPV System"
                },
                description: "The Rotor Riot Ripper V2 is the ultimate high-end racing drone designed for professional FPV pilots and content creators. It features a large 7-inch frame for stability and long-range capabilities, along with top-tier components for maximum performance. The drone includes advanced features like GPS positioning and a long-range FPV system for extended flight sessions."
            },
            jouav: {
                name: "JOUAV CW-15",
                type: "VTOL Fixed Wing Drone",
                price: "$25,000",
                manufacturer: "JOUAV",
                website: "https://www.jouav.com",
                date: "2020",
                image: "https://sfile.chatglm.cn/images-ppt/d4a8d2770093.jpg",
                specs: {
                    "Flight Time": "90 min",
                    "Range": "30 km",
                    "Payload": "2.5 kg",
                    "Max Speed": "72 km/h",
                    "Wingspan": "2.4 m",
                    "Weight": "15 kg",
                    "Camera": "Sony A6000",
                    "GPS": "RTK/PPK"
                },
                description: "The JOUAV CW-15 is a versatile VTOL (Vertical Take-Off and Landing) fixed-wing drone that combines the benefits of multirotor and fixed-wing aircraft. It features a flight time of up to 90 minutes and a range of 30 km, making it ideal for mapping, surveying, and inspection applications. The CW-15 can carry a payload of up to 2.5 kg and is equipped with a high-quality Sony A6000 camera for capturing detailed aerial imagery."
            },
            yangda: {
                name: "Yangda YD6-1600",
                type: "Long Endurance Drone",
                price: "$18,000",
                manufacturer: "Yangda",
                website: "https://www.yangda.cc",
                date: "2021",
                image: "https://sfile.chatglm.cn/images-ppt/3e089199026e.jpg",
                specs: {
                    "Flight Time": "160 min",
                    "Range": "200 km",
                    "Payload": "3 kg",
                    "Max Speed": "90 km/h",
                    "Wingspan": "2.6 m",
                    "Weight": "18 kg",
                    "Camera": "Sony RX1R II",
                    "GPS": "Dual RTK"
                },
                description: "The Yangda YD6-1600 is a long-endurance fixed-wing drone designed for extended mapping and surveying missions. With a flight time of up to 160 minutes and a range of 200 km, it can cover large areas efficiently. The drone features a robust carbon fiber construction and is equipped with a high-resolution Sony RX1R II camera for capturing detailed aerial imagery."
            },
            measur: {
                name: "Measur Mapper",
                type: "Mapping Fixed Wing Drone",
                price: "$12,500",
                manufacturer: "Measur Drones",
                website: "https://www.measurdrones.com",
                date: "2020",
                image: "https://sfile.chatglm.cn/images-ppt/c56d9ac8cf84.png",
                specs: {
                    "Flight Time": "59 min",
                    "Range": "40 km",
                    "Payload": "1.2 kg",
                    "Max Speed": "58 km/h",
                    "Wingspan": "2.2 m",
                    "Weight": "9.5 kg",
                    "Camera": "Sony RX1R II",
                    "GPS": "PPK"
                },
                description: "The Measur Mapper is a professional fixed-wing drone designed for high-precision mapping and surveying applications. It features a flight time of 59 minutes and a range of 40 km, making it ideal for large-area mapping projects. The drone is equipped with a Sony RX1R II camera and PPK GPS for capturing highly accurate aerial imagery."
            },
            e99: {
                name: "E99 Pro",
                type: "Dual Camera Drone",
                price: "$199",
                manufacturer: "E99",
                website: "https://www.e99drone.com",
                date: "2022",
                image: "https://sfile.chatglm.cn/images-ppt/672ae958ed70.jpeg",
                specs: {
                    "Flight Time": "15-18 min",
                    "Camera": "Dual 4K",
                    "Range": "1.2 km",
                    "Max Speed": "40 km/h",
                    "Weight": "450g",
                    "Dimensions": "25 × 25 × 7 cm",
                    "Battery": "7.4V 1800mAh LiPo",
                    "Features": "Altitude Hold, Headless Mode"
                },
                description: "The E99 Pro is an affordable dual-camera drone that offers impressive features at a budget-friendly price. It features two 4K cameras for capturing stunning aerial footage from different angles. The drone has a flight time of 15-18 minutes and a range of 1.2 km, making it suitable for both beginners and intermediate pilots."
            },
            holystone: {
                name: "Holy Stone HS720E",
                type: "GPS Dual Camera Drone",
                price: "$299",
                manufacturer: "Holy Stone",
                website: "https://www.holystone.com",
                date: "2021",
                image: "https://sfile.chatglm.cn/images-ppt/d90c96fbad20.jpg",
                specs: {
                    "Flight Time": "23 min",
                    "Camera": "4K EIS + 1080p",
                    "Range": "1 km",
                    "Max Speed": "40 km/h",
                    "Weight": "485g",
                    "Dimensions": "25 × 20 × 8 cm",
                    "Battery": "7.4V 2800mAh LiPo",
                    "GPS": "Yes"
                },
                description: "The Holy Stone HS720E is a GPS-equipped dual-camera drone that offers excellent value for money. It features a 4K EIS camera for stable footage and a 1080p secondary camera for different perspectives. With a flight time of 23 minutes and GPS-assisted flight features, it's perfect for aerial photography and videography."
            },
            snaptain: {
                name: "SNAPTAIN SP510",
                type: "Dual Camera Drone",
                price: "$249",
                manufacturer: "SNAPTAIN",
                website: "https://www.snaptain.com",
                date: "2022",
                image: "https://sfile.chatglm.cn/images-ppt/ff6b6d5ec31d.jpeg",
                specs: {
                    "Flight Time": "16 min",
                    "Camera": "4K + 720p",
                    "Range": "120 m",
                    "Max Speed": "35 km/h",
                    "Weight": "410g",
                    "Dimensions": "23 × 23 × 6 cm",
                    "Battery": "7.4V 1600mAh LiPo",
                    "Features": "Altitude Hold, Gesture Control"
                },
                description: "The SNAPTAIN SP510 is a user-friendly dual-camera drone that's perfect for beginners and recreational pilots. It features a 4K main camera and a 720p secondary camera for capturing footage from different angles. The drone offers intuitive controls and features like altitude hold and gesture control for easy operation."
            },
            matrice: {
                name: "DJI Matrice 300 RTK",
                type: "Professional Thermal Drone",
                price: "$15,999",
                manufacturer: "DJI",
                website: "https://www.dji.com",
                date: "2020",
                image: "https://sfile.chatglm.cn/images-ppt/9f56cd212c37.webp",
                specs: {
                    "Flight Time": "55 min",
                    "Camera": "Zenmuse H20T",
                    "Range": "15 km",
                    "Max Speed": "82 km/h",
                    "Weight": "6.3 kg",
                    "Dimensions": "810 × 670 × 430 mm",
                    "Battery": "TB60 Intelligent Flight Battery",
                    "GPS": "RTK"
                },
                description: "The DJI Matrice 300 RTK is a professional-grade drone designed for industrial applications. It features the Zenmuse H20T camera, which combines a zoom camera, wide camera, thermal camera, and laser rangefinder in one payload. With a flight time of 55 minutes and advanced safety features, it's ideal for inspection, search and rescue, and mapping applications."
            },
            flir: {
                name: "FLIR Vue Pro R",
                type: "Thermal Imaging Drone",
                price: "$1,999",
                manufacturer: "FLIR Systems",
                website: "https://www.flir.com",
                date: "2019",
                image: "https://sfile.chatglm.cn/images-ppt/11c1b00c60a7.jpg",
                specs: {
                    "Resolution": "640x512",
                    "Thermal Sensitivity": "<30mK",
                    "Frame Rate": "30Hz",
                    "Lens": "19mm, 9mm, 13mm options",
                    "Weight": "125g",
                    "Dimensions": "58 × 44 × 46 mm",
                    "Power": "4.8-5.2 VDC",
                    "Interface": "Micro HDMI"
                },
                description: "The FLIR Vue Pro R is a high-performance thermal imaging camera designed for drone applications. It features a 640x512 resolution thermal sensor with exceptional thermal sensitivity of less than 30mK. The camera is compatible with a wide range of drones and is ideal for applications such as search and rescue, building inspection, and precision agriculture."
            },
            siras: {
                name: "Teledyne FLIR SIRAS",
                type: "Professional Thermal Drone",
                price: "$7,995",
                manufacturer: "Teledyne FLIR",
                website: "https://www.flir.com",
                date: "2021",
                image: "https://sfile.chatglm.cn/images-ppt/712cfe209f7e.jpg",
                specs: {
                    "Flight Time": "31 min",
                    "Camera": "Thermal + RGB",
                    "Range": "6 km",
                    "Max Speed": "51 km/h",
                    "Weight": "2.4 kg",
                    "Dimensions": "280 × 380 × 180 mm",
                    "Battery": "Smart Battery",
                    "GPS": "Dual GPS/GLONASS"
                },
                description: "The Teledyne FLIR SIRAS is a professional thermal drone designed for industrial inspections and public safety applications. It features a dual thermal and RGB camera payload for capturing detailed imagery in various conditions. The drone offers a flight time of 31 minutes and is equipped with advanced safety features for reliable operation in challenging environments."
            },
            mini2: {
                name: "DJI Mini 2",
                type: "Mini Quadcopter Drone",
                price: "$449",
                manufacturer: "DJI",
                website: "https://www.dji.com",
                date: "2020",
                image: "https://sfile.chatglm.cn/images-ppt/98e10ad9ba40.jpg",
                specs: {
                    "Weight": "249g",
                    "Flight Time": "31 min",
                    "Camera": "4K HDR",
                    "Range": "10 km",
                    "Max Speed": "57 km/h",
                    "Dimensions": "159 × 203 × 56 mm",
                    "Battery": "2S 2250mAh LiPo",
                    "GPS": "GPS + GLONASS + Galileo"
                },
                description: "The DJI Mini 2 is a compact and lightweight drone that weighs less than 250g, making it exempt from many drone regulations. It features a 4K HDR camera and a flight time of up to 31 minutes. With a range of 10 km and advanced features like OcuSync 2.0 transmission, it's perfect for aerial photography and videography enthusiasts."
            },
            hs110d: {
                name: "Holy Stone HS110D",
                type: "Mini FPV Drone",
                price: "$129",
                manufacturer: "Holy Stone",
                website: "https://www.holystone.com",
                date: "2021",
                image: "https://sfile.chatglm.cn/images-ppt/fe6224049d21.jpg",
                specs: {
                    "Weight": "115g",
                    "Flight Time": "10 min",
                    "Camera": "720p HD",
                    "Range": "120 m",
                    "Max Speed": "30 km/h",
                    "Dimensions": "31 × 31 × 7 cm",
                    "Battery": "3.7V 500mAh LiPo",
                    "Features": "Altitude Hold, One Key Takeoff/Landing"
                },
                description: "The Holy Stone HS110D is an affordable mini drone perfect for beginners and recreational pilots. It features a 720p HD camera for capturing aerial footage and FPV transmission for real-time viewing. The drone offers easy-to-use features like altitude hold and one-key takeoff/landing, making it ideal for those new to drone flying."
            },
            tello: {
                name: "Ryze Tello",
                type: "Mini Programmable Drone",
                price: "$99",
                manufacturer: "Ryze Tech",
                website: "https://www.ryzerobotics.com",
                date: "2018",
                image: "https://sfile.chatglm.cn/images-ppt/8359a27559fa.jpg",
                specs: {
                    "Weight": "80g",
                    "Flight Time": "13 min",
                    "Camera": "5MP HD",
                    "Range": "100 m",
                    "Max Speed": "28.8 km/h",
                    "Dimensions": "98 × 92.5 × 41 mm",
                    "Battery": "1S 1100mAh LiPo",
                    "Programming": "Scratch, Python, Swift"
                },
                description: "The Ryze Tello is a mini programmable drone designed for education and entertainment. It features a 5MP HD camera and can be programmed using Scratch, Python, or Swift, making it perfect for learning coding and robotics. With its lightweight design and intuitive controls, it's suitable for users of all ages and skill levels."
            }
        };
        
        // Tab functionality
        document.addEventListener('DOMContentLoaded', function() {
            const tabs = document.querySelectorAll('.tab');
            const tabContents = document.querySelectorAll('.tab-content');
            
            tabs.forEach(tab => {
                tab.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    
                    // Remove active class from all tabs and tab contents
                    tabs.forEach(t => t.classList.remove('active'));
                    tabContents.forEach(tc => tc.classList.remove('active'));
                    
                    // Add active class to clicked tab and corresponding tab content
                    this.classList.add('active');
                    document.getElementById(tabId).classList.add('active');
                });
            });
            
            // Modal functionality
            const modal = document.getElementById('droneModal');
            const closeModal = document.querySelector('.close-modal');
            const viewDetailsBtns = document.querySelectorAll('.view-details-btn');
            
            viewDetailsBtns.forEach(btn => {
                btn.addEventListener('click', function() {
                    const droneId = this.getAttribute('data-drone');
                    const drone = droneData[droneId];
                    
                    if (drone) {
                        // Populate modal with drone data
                        document.getElementById('modalImage').src = drone.image;
                        document.getElementById('modalDroneName').textContent = drone.name;
                        document.getElementById('modalDroneType').textContent = drone.type;
                        document.getElementById('modalDronePrice').textContent = drone.price;
                        document.getElementById('manufacturerName').textContent = `Manufacturer: ${drone.manufacturer}`;
                        document.getElementById('manufacturerWebsite').href = drone.website;
                        document.getElementById('droneDescription').textContent = drone.description;
                        
                        // Populate specs
                        const specGrid = document.getElementById('specGrid');
                        specGrid.innerHTML = '';
                        
                        for (const [key, value] of Object.entries(drone.specs)) {
                            const specItem = document.createElement('div');
                            specItem.className = 'spec-item-modal';
                            specItem.innerHTML = `
                                <div class="spec-label-modal">${key}</div>
                                <div class="spec-value-modal">${value}</div>
                            `;
                            specGrid.appendChild(specItem);
                        }
                        
                        // Show modal
                        modal.style.display = 'block';
                    }
                });
            });
            
            closeModal.addEventListener('click', function() {
                modal.style.display = 'none';
            });
            
            window.addEventListener('click', function(event) {
                if (event.target === modal) {
                    modal.style.display = 'none';
                }
            });
        });
    </script>
</body>
</html>
