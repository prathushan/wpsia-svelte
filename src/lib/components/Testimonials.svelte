<script>
  export let data;
</script>
 
<section class="testimonials" id="testimonials">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{data.testimonials.title} <span class="title-highlight"> {data.testimonials.titleHighlight}</span></h2> 
      <p class="section-desc">{data.testimonials.description}</p>
    </div>
  
    <div class="testimonial-grid">
      {#each data.testimonials.items as testimonial}
        <div class="testimonial-card">
          <p class="testimonial-text">{testimonial.text}</p>
          <div class="testimonial-author">
            <div class="author-avatar">{testimonial.author.initials}</div>
            <div class="author-info">
              <h4>{testimonial.author.name}</h4>
              <div class="author-role">{testimonial.author.role}</div>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  @media (max-width: 768px) {
    .testimonial-grid {
        padding-bottom:30px;
    }
}
</style>