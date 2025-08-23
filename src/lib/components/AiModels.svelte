<script>
  export let data;
</script>

<section class="ai-models" id="ai-models">
  <div class="container">
    <div class="models-header">
      <h2 class="section-title">{data.aiModels.title}</h2>
      <p class="section-desc">{data.aiModels.description}</p>
    </div>
    
    <div class="providers-grid">
      {#each data.aiModels.providers as provider}
        <div class="provider-card">
          <div class="provider-header">
            <div class="provider-icon">
              <i class={provider.icon}></i>
            </div>
            <div class="provider-name">{provider.name}</div>
          </div>
          <ul class="models-list">
            {#each provider.models as model}
              <li><span class="model-badge">{model.badge}</span> {model.name}</li>
            {/each}
          </ul>
        </div>
      {/each}
    </div>
    
    <div style="text-align: center;">
      <a href={data.aiModels.cta.href} class="btn btn-primary">{data.aiModels.cta.text}</a>
    </div>
  </div>
</section>