<script>
  export let data;
</script>

<section class="hero">
  <div class="container hero-content">
    <div class="hero-text">
      <!-- <div class="hero-badge">{data.hero.badge}</div> -->
       <div class="hero-badge-container">
        <div class="hero-badge-download">
          <i class="fas fa-download"></i> Free Version Available Now
        </div>
        <div class="hero-badge-other">
          <i class="fas fa-bolt"></i> Limited Time Offer
        </div>
      </div>
      <h2 class="hero-title">{data.hero.title}</h2>
      <p class="hero-desc">{data.hero.description}</p>
      <p class="hero-desc">{data.hero.secDescription}</p>

      <div class="hero-cta">
        {#each data.hero.cta as button}
          <a href={button.href} class="btn btn-{button.style}">
            {#if button.icon}
              <i class="fab {button.icon}"></i>
            {/if}
            {button.text}
          </a>
        {/each}
      </div>

      <div class="hero-stats">
        {#each data.hero.stats as stat}
          <div class="stat-item">
            <div class="stat-icon">
              <i class={stat.icon}></i>
            </div>
            <div class="stat-text">
              <span class="stat-number">{stat.number}</span>
              <span>{stat.text}</span>
            </div>
          </div>
        {/each}
      </div>

      <!-- <h4 class="hero-subtext">{data.hero.subDescription}</h4> -->
      
    </div>



    <div class="hero-image">       

      <img src={data.hero.image} alt="WP-Site-Inspector Dashboard" />
    </div>
  </div>
</section>

<style>
  .stat-text {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .stat-text span {
    line-height: 20px;
  }
  .hero-subtext {
    margin-top: 20px;
    font-size: 25px;
  }
  .hero-badge-container {
    margin-top: 20px;
    display: flex;
    flex-direction: row;
    gap: 15px;
    justify-content: center;
  }
  .hero-badge-other {
    display: inline-block;
    padding: 10px 25px;
    background: rgba(245, 158, 11, 0.1);
    color: #f59e0b;
    border-radius: 30px;
    font-size: 1rem;
    font-weight: 600;
    margin-bottom: 15px;
    animation: pulse 2s infinite;
  }
    @keyframes pulse {
    0% {
      transform: scale(1);
    }
    50% {
      transform: scale(1.05);
    }
    100% {
      transform: scale(1);
    }
  }
  .hero-badge-download {
    display: inline-block;
    padding: 10px 25px;
    background: rgba(16, 185, 129, 0.1);
    color: var(--success);
    border-radius: 30px;
    font-size: 1rem;
    font-weight: 600;
    margin-bottom: 15px; 
  }
  

/* @media(min-width:1024px){
  .hero-image img {
  height:600px;
}
} */
  @media (max-width: 480px) {
    .hero-badge-container {
      flex-direction: column;
    }
    .hero-badge-download{
      margin-bottom:0;
    }


  }
    @media (max-width: 992px) {

    .hero-desc{
      margin-bottom:25px;
    }
    .hero-cta{
      justify-content: center;
    }
    .hero-title{
      text-align: center;
    }

  }
</style>
