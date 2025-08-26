<script>
  import { onMount } from 'svelte';
  
  let isMobile = false;
  
  // Check screen size on mount and when window is resized
  onMount(() => {
    const checkScreenSize = () => {
      isMobile = window.innerWidth <= 1024;
    };
    
    checkScreenSize();
    window.addEventListener('resize', checkScreenSize);
    
    return () => {
      window.removeEventListener('resize', checkScreenSize);
    };
  });
</script>

<style>
  .workflow-container {
    position: relative;
    height: 700px;
    margin: -150px auto; /* Reduced top margin */
  }
  
  .workflow-heading {
    text-align: center;
    margin: 0 auto;
  }
 
  /* Center Circle with Pulse */
  .center, .center-ai {
    position: absolute;
    transform: translate(-50%, -50%);
    width: 120px;
    height: 120px;
    background: radial-gradient(circle, #7b61ff, #4f39f5);
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    font-size: 1rem;
    font-weight: bold;
    box-shadow: 0 0 25px rgba(123, 97, 255, 0.6);
    z-index: 10;
  }
 
  .center { left: 25%; top: 50%; }
  .center-ai { left: 66%; top: 50%; }
 
  .center::before, .center-ai::before {
    content: '';
    position: absolute;
    width: 120px;
    height: 120px;
    border-radius: 50%;
    background: rgba(123, 97, 255, 0.5);
    animation: pulse 2s infinite;
    z-index: -1;
  }
 
  @keyframes pulse {
    0% { transform: scale(1); opacity: 0.7; }
    100% { transform: scale(1.8); opacity: 0; }
  }
 
  /* Cards */
  .card {
    position: absolute;
    background: #fff;
    border-radius: 12px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    padding: 10px;
    width: 210px;
    text-align: center;
    z-index: 5;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
 
  .card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.15);
  }
 
  /* Right side cards */
  .card.right-1 { top: 28%; right: 46%; }
  .card.right-2 { top: 40%; right: 46%; }
  .card.right-3 { top: 52%; right: 46%; }
  .card.right-4 { top: 64%; right: 46%; }
  .card.right-5 { top: 56%; right: 4%; }
  .card.right-6 { top: 36%; right: 4%; }
 
  /* Left side final output card */
  .card.left {
    top: 50%;
    left: 1%;
    transform: translateY(-50%);
    box-shadow: none;
    background-color: transparent;
  }
 
  /* SVG Lines */
  svg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    pointer-events: none;
  }
 
  .list-items, .list-items-ai {
    list-style: none;
    margin: 0;
    padding: 0;
  }
 
  .list-items {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 5px;
  }
 
  .list-items li {
    background: #edf0ff;
    padding: 3px;
    text-align: center;
    border-radius: 4px;
    font-size: 0.6rem;
    color: #4b6df8;
    font-weight: bold;
  }
 
  .list-items-ai li {
    background: #edf0ff;
    padding: 3px 10px;
    text-align: center;
    border-radius: 4px;
    font-size: 0.8rem;
    color: #4b6df8;
    font-weight: bold;
  }
 
  .wordpress-logo {
    width: 60%;
  }
 
  path {
    stroke: #a3a0f8;
    stroke-width: 3;
    fill: none;
    stroke-dasharray: 6,6;
    animation: dash 3s linear infinite;
  }
 
  @keyframes dash {
    to { stroke-dashoffset: -2000; }
  }
  
  /* Mobile Layout Styles */
  .mobile-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
    gap: 10px;
    position: relative;
    margin:0 auto;
  }
  
  .mobile-logo {
    width: 80px;
    margin-bottom: 10px;
  }
  
  .mobile-card {
    background: #fff;
    border-radius: 12px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    padding: 15px;
    width: 100%;
    max-width: 300px;
    text-align: center;
    position: relative;
    z-index: 2;
  }
  
  .mobile-center {
    width: 100px;
    height: 100px;
    background: radial-gradient(circle, #7b61ff, #4f39f5);
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    font-size: 0.9rem;
    font-weight: bold;
    box-shadow: 0 0 25px rgba(123, 97, 255, 0.6);
    margin: 15px 0;
    position: relative;
    z-index: 2;
  }
  
  .mobile-center::before {
    content: '';
    position: absolute;
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background: rgba(123, 97, 255, 0.5);
    animation: pulse 2s infinite;
    z-index: -1;
  }
  
  /* Mobile connecting lines */
  .mobile-connector {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    z-index: 1;
    background: #a3a0f8;
  }
  
  .mobile-dashed-line {
    width: 3px;
    height: 40px;
    background: repeating-linear-gradient(
      to bottom,
      transparent,
      transparent 5px,
      #a3a0f8 5px,
      #a3a0f8 10px
    );
  }
  
  /* Hide appropriate containers based on screen size */
  .desktop-only {
    display: block;
  }
  
  .mobile-only {
    display: none;
  }
  
  @media (max-width: 1024px) {
    .desktop-only {
      display: none;
    }
    
    .mobile-only {
      display: flex;
    }
  }
</style>

<!-- Desktop Layout -->
<div class="desktop-only">
  <div class="container">
    <div class="workflow-container">
      <svg viewBox="0 0 1200 700" preserveAspectRatio="xMidYMid meet">
        <!-- Left-side curves -->
        <path d="M450 240 C 425 240, 395 310, 350 350" />
        <path d="M450 320 C 425 320, 395 335, 350 350" />
        <path d="M450 400 C 425 400, 395 365, 350 350" />
        <path d="M450 480 C 425 480, 395 395, 350 350" />
     
        <!-- Center to left card -->
        <path d="M350 350 C 325 350, 200 350, 150 350" stroke="black" fill="transparent"/>
     
        <!-- Right-side reversed curves -->
        <path d="M750 350 C 705 310, 675 240, 650 240" />
        <path d="M750 350 C 705 335, 675 320, 650 320" />
        <path d="M750 350 C 705 365, 675 400, 650 400" />
        <path d="M750 350 C 705 395, 675 480, 650 480" />
     
        <!-- AI curves -->
        <path d="M950 280 C 925 280, 870 320, 800 350" />
        <path d="M950 420 C 925 420, 870 380, 800 350" />
      </svg>
     
      <!-- Center -->
      <div class="center">WPSI Plugin</div>
      <div class="center-ai">WPSI Agent</div>
     
      <!-- Right-side cards -->
      <div class="card right-1">
        <ul class="list-items">
          <li>Pages</li>
          <li>Posts</li>
          <li>Post types</li>
          <li>Templates</li>
          <li>Shortcodes</li>
          <li>Hooks</li>
        </ul>
      </div>
     
      <div class="card right-2">
        <ul class="list-items">
          <li>Theme</li>
          <li>Builders</li>
          <li>Plugins</li>
          <li>APIs</li>
          <li>CDN</li>
        </ul>
      </div>
     
      <div class="card right-3">
        <ul class="list-items">
          <li>Logs</li>
          <li>Backup</li>
          <li>Export</li>
          <li>Restore</li>
        </ul>
      </div>
     
      <div class="card right-4">
        <ul class="list-items">
          <li>Ask AI</li>
          <li>Fix AI</li>
          <li>Accessibility</li>
          <li>Code AI</li>
        </ul>
      </div>
     
      <!-- Left-side card -->
      <div class="card left card-left">
        <img src="/assets/wordpress-icon.png" alt="Final Output" class="wordpress-logo">
      </div>
     
      <!-- AI cards -->
      <div class="card right-5">
        <ul class="list-items-ai">
          <li>AI-Fixes</li>
        </ul>
      </div>
      <div class="card right-6">
        <ul class="list-items-ai">
          <li>AI-Suggestions</li>
        </ul>
      </div>
    </div>
  </div>
</div>

<!-- Mobile Layout -->
<div class="mobile-only">
  <div class="mobile-container">
    <!-- Logo at the top -->
    <img src="/assets/wordpress-icon.png" alt="WordPress Logo" class="mobile-logo">
    
    <!-- Connection line after logo -->
    <div class="mobile-connector mobile-dashed-line" style="top: 90px;"></div>
    
    <!-- WPSI Plugin -->
    <div class="mobile-center">WPSI Plugin</div>
    
    <!-- Connection line after WPSI Plugin -->
    <div class="mobile-connector mobile-dashed-line" style="top: 215px;"></div>
    
    <!-- Four cards -->
    <div class="mobile-card">
      <ul class="list-items">
        <li>Pages</li>
        <li>Posts</li>
        <li>Post types</li>
        <li>Templates</li>
        <li>Shortcodes</li>
        <li>Hooks</li>
      </ul>
    </div>
    
    <!-- Connection line after first card -->
    <div class="mobile-connector mobile-dashed-line" style="top: 250px;"></div>
    
    <div class="mobile-card">
      <ul class="list-items">
        <li>Theme</li>
        <li>Builders</li>
        <li>Plugins</li>
        <li>APIs</li>
        <li>CDN</li>
      </ul>
    </div>
    
    <!-- Connection line after second card -->
    <div class="mobile-connector mobile-dashed-line" style="top:305px;"></div>
    
    <div class="mobile-card">
      <ul class="list-items">
        <li>Logs</li>
        <li>Backup</li>
        <li>Export</li>
        <li>Restore</li>
      </ul>
    </div>
    
    <!-- Connection line after third card -->
    <div class="mobile-connector mobile-dashed-line" style="top: 400px;"></div>
    
    <div class="mobile-card">
      <ul class="list-items">
        <li>Ask AI</li>
        <li>Fix AI</li>
        <li>Accessibility</li>
        <li>Code AI</li>
      </ul>
    </div>
    
    <!-- Connection line after fourth card -->
    <div class="mobile-connector mobile-dashed-line" style="top: 600px;"></div>
    
    <!-- WPSI Agent -->
    <div class="mobile-center">WPSI Agent</div>
    
    <!-- Connection line after WPSI Agent -->
    <div class="mobile-connector mobile-dashed-line" style="top: 730px;"></div>
    
    <!-- Two AI cards -->
    <div class="mobile-card">
      <ul class="list-items-ai">
        <li>AI-Suggestions</li>
      </ul>
    </div>
    
    <!-- Connection line after first AI card -->
    <div class="mobile-connector mobile-dashed-line" style="top: 800px;"></div>
    
    <div class="mobile-card">
      <ul class="list-items-ai">
        <li>AI-Fixes</li>
      </ul>
    </div>
  </div>
</div>
