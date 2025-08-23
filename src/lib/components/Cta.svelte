<script>
  export let data;
</script>

<section class="cta" id="pricing">
  <div class="container">
    <h2 class="cta-title">{data.cta.title}</h2>
    <p class="cta-desc">{data.cta.description}</p>
    
    <div class="cta-buttons">
      {#each data.cta.buttons as button}
        <a href={button.href} class="btn btn-{button.style}">{button.text}</a>
      {/each}
    </div>
  </div>
</section>