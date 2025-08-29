<script>
  export let data;
</script>

<section class="features bg-no-change" id="features">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{data.features.title}</h2>
      <p class="section-desc">{data.features.description}</p>
    </div>
    
    <div class="features-grid">
      {#each data.features.items as feature}
        <div class="feature-card">
          <div class="feature-icon">
            <i class={feature.icon}></i>
          </div>
          <h3 class="feature-title">{feature.title}</h3>
          <p class="feature-desc">{feature.description}</p>
          <a href={feature.link.href} class="btn btn-outline">{feature.link.text}</a>
        </div>
      {/each}
    </div>
  </div>
</section>