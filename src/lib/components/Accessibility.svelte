<script>
  export let data;
</script>

<section class="accessibility" id="accessibility">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{data.accessibility.title}</h2>
      <p class="section-desc">{data.accessibility.description}</p>
    </div>
    
    <div class="access-content">
    <!-- <div class="access-image">
        <img src={data.accessibility.image} alt={data.accessibility.imageAlt}>
      </div> -->

      <div class="access-text">
               
        <div class="issue-levels">
          {#each data.accessibility.issueLevels as level}
            <div class="issue-card issue-{level.type}">
              <div class="issue-title">
                <div class="issue-icon icon-{level.type}">
                  <i class={level.icon}></i>
                </div>
                <h4>{level.title}</h4>
              </div>
              <p>{level.description}</p>
            </div>
          {/each}
        </div>
        <p class="accessible-intro-text">{data.accessibility.introText}</p>
      </div>
      
    
    </div>
  </div>
</section>