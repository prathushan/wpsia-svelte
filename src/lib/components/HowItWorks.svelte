<script>
  import Workflow from "./Workflow.svelte";

  export let data;
</script>

<section class="how-it-works bg-change" id="how-it-works">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{data.howItWorks.title}</h2>
      <p class="section-desc">{data.howItWorks.description}</p>
    </div>
    
    <div class="process-steps">
      {#each data.howItWorks.steps as step}
        <div class="step">
          <div class="step-number">{step.number}</div>
          <h3 class="step-title">{step.title}</h3>
          <p class="step-desc">{step.description}</p>
        </div>
      {/each}
    </div>

    <Workflow/>
    
    <div style="text-align: center; margin-top: 3rem;">
      <a href={data.howItWorks.cta.href} class="btn btn-primary">{data.howItWorks.cta.text}</a>
    </div>
  </div>
</section>