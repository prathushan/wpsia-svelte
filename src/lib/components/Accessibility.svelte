<script>
  export let data;
</script>

<section class="accessibility" id="accessibility">
  <div class="accessibility-header">
    <h2 class="section-title">{data.accessibility.title}</h2>
    <p class="section-desc">{data.accessibility.description}</p>
  </div>

  <div class="container">
    <div class="accessibility-content">
      <div class="hero-text">
        <div>
          <h2 class="uat-title">{data.uat.title}</h2>
        <p class="uat-desc">{data.uat.description}</p>
        </div>
        <div class="uat-desText">
          {#each data.uat.desText as descText}
            <p>{descText.text}</p>
          {/each}
        </div>

        <div class="uat-icon-dev">
          {#each data.uat.issueLevels as level}
            <div class="issue-title">
              <div class="issue-icon icon-{level.type}">
                <i class={level.icon}></i>
              </div>
              <h4>{level.title}</h4>
            </div>
          {/each}
        </div>
      </div>

      <div class="hero-image">
        <img src={data.uat.image} alt="WP-Site-Inspector Dashboard" />
      </div>
    </div>
  </div>
</section>

<style>
  .uat-icon-dev {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-top: 30px;
  }


  .accessibility-header {
    text-align: center;
    max-width: 1200px;
    margin: 0 auto 60px;
  }

  .accessibility-content {
    display: flex;

    gap: 30px;
  }

      @media (max-width: 992px) {

    .accessibility-content{
      flex-direction: column;
    }
    .accessibility-header{
      margin-bottom:30px;
    }
   

  }

</style>
