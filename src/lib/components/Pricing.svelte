<script>
  export let data;
</script>

<section class="pricing bg-no-change" id="pricing">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{data.pricing.title}</h2>
      <p class="section-desc">{data.pricing.description}</p>
    </div>
    
    <div class="pricing-grid">
      {#each data.pricing.plans as plan}
        <div class="pricing-card {plan.popular ? 'popular' : ''}">
          {#if plan.popular}
            <div class="popular-badge">{plan.popularText}</div>
          {/if}
          <h3 class="pricing-name">{plan.name}</h3>
          <div class="pricing-price">{plan.price}</div>
          <div class="pricing-period">{plan.period}</div>
          
          <ul class="pricing-features">
            {#each plan.features as feature}
              <li>
                {#if feature.included}
                  <i class="fas fa-check feature-icon"></i>
                {:else}
                  <i class="fas fa-times feature-icon-cross"></i>
                {/if}
                {feature.text}
              </li>
            {/each}
          </ul>
          
          <a href={plan.cta.href} class="btn btn-{plan.cta.style}">{plan.cta.text}</a>
        </div>
      {/each}
    </div>
  </div>
</section>


<style>
  @media (max-width: 992px) {
 .pricing-grid {
        display:flex;
        flex-direction: column;
        align-items: center;

    }
    .pricing-card {
    border: 2px solid #4a6cf7;
    }
}
</style>