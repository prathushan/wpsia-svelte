<script>
  import { slide } from 'svelte/transition';
  export let data;
  
  // Track which FAQ item is open
  let openIndex = null;
  
  function toggleFAQ(index) {
    openIndex = openIndex === index ? null : index;
  }
</script>

<section class="faq" id="faq">
  <div class="container">
    <div class="section-header">
      <h2 class="section-title">{data.faq.title}</h2>
      <p class="section-desc">{data.faq.description}</p>
    </div>
    
    <div class="faq-content">
      <div class="faq-list">
        {#each data.faq.categories as category, categoryIndex}
          <div class="faq-category">
            <!-- <h3 class="faq-category-title">{category.name}</h3> -->
            
            {#each category.questions as question, index}
              <div class="faq-item">
                <button class="faq-question" on:click={() => toggleFAQ(`${categoryIndex}-${index}`)}>
                  <span>{question.question}</span>
                  <i class="fas {openIndex === `${categoryIndex}-${index}` ? 'fa-times' : 'fa-plus'}"></i>
                </button>
                
                {#if openIndex === `${categoryIndex}-${index}`}
  <div class="faq-answer" transition:slide={{ duration: 700 }}>
    <p>{question.answer}</p>
  </div>
{/if}
              </div>
            {/each}
          </div>
        {/each}
      </div>
      
      <!-- <div class="faq-cta">
        <p>Still have questions? We're here to help!</p>
        <a href="{data.faq.cta.href}" class="btn btn-primary">{data.faq.cta.text}</a>
      </div> -->
    </div>
  </div>
</section>

<style>
  .faq {
    background: #f9fafb;
    padding: 5rem 0;
  }
  
  .faq-content {
    margin-top: 3rem;
  }
  
  .faq-category {
    margin-bottom: 2.5rem;
  }
  
  /* .faq-category-title {
    font-size: 1.5rem;
    font-weight: 600;
    color: #111827;
    margin-bottom: 1.5rem;
    padding-bottom: 0.5rem;
    border-bottom: 2px solid #e5e7eb;
  } */
  
  .faq-item {
    margin-bottom: 1rem;
    border-radius: 0.5rem;
    overflow: hidden;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    background: white;
  }
  
  .faq-question {
    width: 100%;
    padding:0.5rem 1.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: white;
    border: none;
    text-align: left;
    font-size: 1.125rem;
    font-weight: 500;
    color: #111827;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .faq-question:hover {
    background: #f9fafb;
  }
  
  .faq-question i {
    color: #4f46e5;
    transition: transform 0.3s;
  }
  
  .faq-answer {
    padding: 0 1.5rem 1.5rem;
    color: #6b7280;
    line-height: 1.6;
  }
  
  /* .faq-cta {
    text-align: center;
    margin-top: 3rem;
    padding: 2rem;
    background: white;
    border-radius: 1rem;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
      transition: all 0.3s ease;
  }
  .faq-cta:hover{
     box-shadow: 0 15px 30px rgba(64, 86, 227, 0.73);
  }
  
  .faq-cta p {
    margin-bottom: 1.5rem;
    font-size: 1.125rem;
    color: #374151;
  } */
  
  @media (max-width: 768px) {
    .faq-question {
      font-size: 1rem;
    }
  }
</style>