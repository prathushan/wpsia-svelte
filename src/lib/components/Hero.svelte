<script>
  export let data;
</script>

<section class="hero">
  <div class="container hero-content">
    <div class="hero-text">
      <div class="hero-badge">{data.hero.badge}</div>
      <h1 class="hero-title">{data.hero.title}</h1>
      <p class="hero-desc">{data.hero.description}</p>
      
      <div class="hero-cta">
        {#each data.hero.cta as button}
          <a href={button.href} class="btn btn-{button.style}">{button.text}</a>
        {/each}
      </div>
      
      <div class="hero-stats">
        {#each data.hero.stats as stat}
          <div class="stat-item">
            <div class="stat-icon">
              <i class={stat.icon}></i>
            </div>
            <div class="stat-text">
              <div class="stat-number">{stat.number}</div>
              <div>{stat.text}</div>
            </div>
          </div>
        {/each}
      </div>
    </div>
    
    <div class="hero-image">
      <img src={data.hero.image} alt="WP-Site-Inspector Dashboard">
    </div>
  </div>
</section>