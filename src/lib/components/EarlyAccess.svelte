
    <section class="hero">
        <div class="container">
            <div class="hero-badge-container">
                <div class="hero-badge-download">
                <i class="fas fa-download"></i> Free Version Available Now
            </div>
            <div class="hero-badge">
                
                <i class="fas fa-bolt"></i> Limited Time Offer
            </div>
            </div>
            <h1 class="hero-title">Be One of the First 100 Get Pro Access FREE!</h1>
            <p class="hero-desc">Join our early access program and receive lifetime access to all Pro and Agency features of WP-Site-Inspector. No payment required.</p>
            
            <div class="hero-cta">
                <a href="https://github.com/prathushan/WP-Site-Inspector/" class="btn btn-primary">
                    <i class="fab fa-github"></i> Download from GitHub
                </a>
                <a href="#early-access" class="btn btn-outline">Request Early Pro Access</a>
            </div>
            
        </div>
    </section>

    <style>
                /* Hero Section */
        .hero {
            padding: 160px 0 30px;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" viewBox="0 0 800 800"><rect fill="%23f8fafc" width="800" height="800"/><path fill="%23e2e8f0" fill-opacity="0.2" d="M0,0L800,800M800,0L0,800" stroke-width="2"/></svg>');
            background-size: cover;
            text-align: center;
            scroll-behavior: smooth;
        }
        .hero-badge-container{
            display:flex;
            flex-direction: row;
            gap:15px;
            justify-content: center;
        }
        .hero-badge {
            display: inline-block;
            padding: 10px 25px;
            background: rgba(245, 158, 11, 0.1);
            color: #f59e0b;
            border-radius: 30px;
            font-size: 1rem;
            font-weight: 600;
            margin-bottom: 25px;
            animation: pulse 2s infinite;
        }
        .hero-badge-download {
    display: inline-block;
    padding: 10px 25px;
    background: rgba(16, 185, 129, 0.1);
    color: var(--success);
    border-radius: 30px;
    font-size: 1rem;
    font-weight: 600;
    margin-bottom: 25px;
}
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        .hero-title {
            font-size: 3.5rem;
            margin-bottom: 20px;
            line-height: 1.2;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .hero-desc {
            font-size: 1.3rem;
            margin-bottom: 40px;
            color: var(--body-color);
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .hero-cta {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin-bottom: 50px;
            flex-wrap: wrap;
        }
        
        .hero-stats {
            display: flex;
            gap: 40px;
            justify-content: center;
            flex-wrap: wrap;
        }
        
        .stat-item {
            text-align: center;
        }
        
        .stat-number {
            font-size: 2rem;
            font-weight: 700;
            color: var(--dark);
            margin-bottom: 5px;
        }
        
        .stat-label {
            font-size: 1rem;
            color: var(--secondary);
        }

        @media(max-width:480px){
             .hero-badge-container{
            
            flex-direction: column;
            
        }
        }
    </style>