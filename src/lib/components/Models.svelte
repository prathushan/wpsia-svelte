<script>
  import { onMount } from 'svelte';
  
  // State for active card and its index
  let activeCardIndex = 0;
  let autoScrollInterval;
  
  // Model card data
  const modelCards = [
    {
      title: "Bring Your Own Key",
      description: "Pre-optimized models for inference with day 1 access to newly released models.",
      tags: ["wp-site-inspector", "Openai", "Deepseek", "Antheopic", "Google", "Mistral" , "Openrouter"],
      image: "assets/BYOK.png",
      imageAlt: "Open Source Model Launcher"
    },
    
     {
      title: "Ask AI",
      description: "Pre-optimized models for inference with day 1 access to newly released models.",
      image: "assets/Ask_AI.png",
      imageAlt: "Ask AI"
    },
    {
      title: "Model Providers",
      description: "Pre-optimized models for inference with day 1 access to newly released models.",
      tags: ["wp-site-inspector", "Openai", "Deepseek", "Antheopic", "Google", "Mistral" , "Openrouter"],
      image: "assets/Providers.png",
      imageAlt: "Open Source Model Launcher"
    },
    {
      title: "Serving Models",
      description: "Deploy models of any architecture, framework, or modality with full customization.",
      tags: ["WPSI-01", "gpt-4", "gpt-3.5-turbo", "deepseek-chat", "deepseek-coder", "deepseek-chat-v3", "claude 3 Opus", "claude 3 Sonnet", "claude 3 Haiku" , "gemini-1.5 Pro", "gemini 1.0 pro", "mistral Small",
       "mistral Medium","mistral Large", "GPT-3.5 Turbo", "GPT_4", "DeepSeek Chat v3 (Free)" ],
        image: "assets/Models.png",
        imageAlt: "Serving Models"
    } , 
 {
      title: "FIx With AI",
      description: "Pre-optimized models for inference with day 1 access to newly released models.",
  
      image: "assets/Providers.png",
      imageAlt: "Open Source Model Launcher"
    }, 
  ];

  // Function to handle card click
  function handleCardClick(index) {
    activeCardIndex = index;
    resetAutoScroll();
  }

  // Function to go to next card
  function nextCard() {
    activeCardIndex = (activeCardIndex + 1) % modelCards.length;
  }

  // Function to go to previous card
  function prevCard() {
    activeCardIndex = (activeCardIndex - 1 + modelCards.length) % modelCards.length;
  }

  // Set up auto-scroll
  function setupAutoScroll() {
    autoScrollInterval = setInterval(() => {
      nextCard();
    }, 5000); // Change card every 5 seconds
  }

  // Reset auto-scroll timer
  function resetAutoScroll() {
    clearInterval(autoScrollInterval);
    setupAutoScroll();
  }

  // Initialize on component mount
  onMount(() => {
    setupAutoScroll();
    
    // Clean up on component destroy
    return () => {
      clearInterval(autoScrollInterval);
    };
  });
</script>

<div class="section-container">
  <div class="content-wrapper">
    <div class="grid-layout">
      <!-- Left Column - Text and Cards -->
      <div class="left-column">
        <div class="text-content">
          <h2 class="section-title">Supported AI Models & Providers</h2>
          <p class="section-description">
           Choose from a wide range of AI models to power your WordPress site analysis and fixes
          </p>
        </div>
        
        <div class="cards-container">
          {#each modelCards as card, index}
            <div 
              class="model-card {activeCardIndex === index ? 'active' : ''}" 
              on:click={() => handleCardClick(index)}
              on:mouseenter={resetAutoScroll}
              data-index={index}
            >
              <div class="card-header">
                <div class="card-icon"></div>
                <h3 class="card-title">{card.title}</h3>
              </div>
              
              <div 
                class="card-content-container" 
                data-index={index}
                style={`max-height: ${activeCardIndex === index ? 'none' : '0px'}`}
              >
                <div class="content-wrapper">
                  <p class="card-description">{card.description}</p>
                  <div class="tags-container">
                    {#each card.tags as tag}
                      <div class="tag">
                        <span class="tag-dot"></span>
                        <span>{tag}</span>
                      </div>
                    {/each}
                  </div>
                </div>
              </div>
            </div>
          {/each}
        </div>

        <!-- Navigation controls -->
        <!-- <div class="navigation-controls">
          <button on:click={prevCard} on:mouseenter={resetAutoScroll} class="nav-button">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="15 18 9 12 15 6"></polyline>
            </svg>
          </button>
          <div class="pagination-dots">
            {#each modelCards as _, index}
              <button 
                on:click={() => handleCardClick(index)}
                class="dot {activeCardIndex === index ? 'active' : ''}"
              ></button>
            {/each}
          </div>
          <button on:click={nextCard} on:mouseenter={resetAutoScroll} class="nav-button">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="9 18 15 12 9 6"></polyline>
            </svg>
          </button>
        </div> -->
      </div>
      
      <!-- Right Column - Display Area -->
      <div class="right-column">
        {#each modelCards as card, index}
          <div 
            class="display-content {activeCardIndex === index ? 'active' : ''}" 
            data-index={index}
            style={`transform: translate(0px, 0px); opacity: ${activeCardIndex === index ? 1 : 0}; display: ${activeCardIndex === index ? 'flex' : 'none'}`}
          >
            {#if card.image}
              <div class="image-container">
                <img src={card.image} alt={card.imageAlt} />
              </div>
            {:else}
              <div class="code-container">
                <pre><code class="language-python">{card.codeContent}</code></pre>
              </div>
            {/if}
          </div>
        {/each}
      </div>
    </div>
  </div>
</div>

<style>
  /* Container styles */
  .section-container {
    padding-top: 3.5rem;
    padding-bottom: 3.5rem;
  }
  
  @media (min-width: 768px) {
    /* .section-container {
      padding-top: 17rem;
      padding-bottom: 5rem;
    } */
  }
  
  .content-wrapper {
    width: 100%;
    height: 100%;
    padding-left: 1.25rem;
    padding-right: 1.25rem;
    margin-left: auto;
    margin-right: auto;
    max-width: 1600px;
  }
  
  @media (min-width: 768px) {
    .content-wrapper {
      /* padding-left: 4rem;
      padding-right: 4rem; */
    }
  }
  
  .grid-layout {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr;
    gap: 4rem;
  }
  
  @media (min-width: 1024px) {
    .grid-layout {
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
    }
  }
  
  /* Left column styles */
  .left-column {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-height: 578px;
    gap: 1.25rem;
  }
  
  @media (min-width: 1024px) {
    .left-column {
      gap: 2.75rem;
    }
  }
  
  .text-content {
    width: 100%;
  }
  
  .section-title {
    margin-bottom: 1.75rem;
    max-width: 35ch;
    font-size: 2.25rem;
    line-height: 2.5rem;
    font-weight: 700;
  }
  
  .section-description {
    max-width: 80ch;
    color: #000;
    font-size: 1.125rem;
    line-height: 1.75rem;
  }
  
  .cards-container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    overflow: hidden;
  }
  
  .model-card {
    padding: 0.75rem;
    border-radius: 10px;
    cursor: pointer;
    background-color: #f8fafc; /* cinza-claro-3 equivalent */
    overflow: hidden;
    transition: all 0.3s ease;
  }
  
  .model-card.active {
    background-color: #f8fafc; /* Slightly darker when active */
  }
 
  .model-card:hover {
    background-color: #f8fafc;
  }
  
  .card-header {
    display: flex;
    align-items: flex-start;
  }
  
  .card-icon {
    width: 2rem;
    height: 2rem;
    --gradient: linear-gradient(135deg, #4a6cf7 0%, #6f42c1 100%);
    background: var(--gradient);
    border-radius: 5px;
    margin-right: 1rem;
    flex-shrink: 0;
  }
  
  .card-title {
    font-family: 'Inter', sans-serif;
    font-weight: 600;
    font-size: 1.25rem;
    line-height: 1.75rem;
  }
  
  .card-content-container {
    overflow: hidden;
    transition: max-height 0.3s ease;
  }
  
  .content-wrapper {
    padding-top: 1.5rem;
  }
  
  .card-description {
    margin-bottom: 1.5rem;
  }
  
  .tags-container {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    max-width: 100%;
    overflow-y: auto;
    max-height: 150px;
    padding-right: 5px;
  }
  
  /* Scrollbar styling */
  .tags-container::-webkit-scrollbar {
    width: 0px;
  }
  
  .tags-container::-webkit-scrollbar-track {
    background: #f1f1f1;
    border-radius: 10px;
  }
  
  .tags-container::-webkit-scrollbar-thumb {
    background: #c1c1c1;
    border-radius: 10px;
  }
  
  .tags-container::-webkit-scrollbar-thumb:hover {
    background: #a8a8a8;
  }
  
  .tag {
    padding: 0.5rem 0.75rem;
    background-color: #fff;
    color: #000;
    font-size: 0.75rem;
    line-height: 1rem;
    border-radius: 5px;
    display: flex;
    gap: 0.5rem;
    align-items: center;
    flex-shrink: 0;
  }
  
  .tag-dot {
    width: 0.5rem;
    height: 0.5rem;
    --gradient: linear-gradient(135deg, #4a6cf7 0%, #6f42c1 100%);
    background: var(--gradient);
    border-radius: 50%;
    flex-shrink: 0;
  }
  
  /* Navigation controls */
  .navigation-controls {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    margin-top: 1.5rem;
  }
  
  .nav-button {
    background: #f5f5f5;
    border: none;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.2s ease;
  }
  
  .nav-button:hover {
    --gradient: linear-gradient(135deg, #4a6cf7 0%, #6f42c1 100%);
    background: var(--gradient);
    color: white;
  }
  
  .pagination-dots {
    display: flex;
    gap: 0.5rem;
  }
  
  .dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    border: none;
    background: #d1d1d1;
    cursor: pointer;
    transition: all 0.2s ease;
  }
  
  .dot.active {
    --gradient: linear-gradient(135deg, #4a6cf7 0%, #6f42c1 100%);
    background: var(--gradient);
    transform: scale(1.2);
  }
  
  /* Right column styles */
  .right-column {
    position: relative;
    /* background-color: #f8fafc; */
     --gradient: linear-gradient(135deg, #4a6cf7 0%, #6f42c1 100%);
    background: var(--gradient);
    border-radius: 20px;
    padding: 2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    height: 612px;
  }
  
  .display-content {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    transition: opacity 0.3s ease;
  }
  
  .image-container {
    width: 100%;
    height: 100%;
    border-radius: 10px;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .image-container img {
    max-width: 100%;
    max-height: 100%;
    object-fit: contain;
    border-radius: 10px;
    transition: transform 0.3s ease;
  }
  
  .image-container img:hover {
    transform: scale(1.02);
  }
  
  .code-container {
    width: 100%;
    height: 100%;
    overflow: hidden;
    font-size: 13px;
  }
  
  .code-container pre {
    margin: 0;
  }
  
  .code-container code {
    white-space: pre;
    background: #FAFAFA;
    color: hsl(230, 8%, 24%);
    font-family: source-code-pro, Menlo, Monaco, "Courier New", Courier, monospace;
    direction: ltr;
    text-align: left;
    word-spacing: normal;
    word-break: normal;
    line-height: 1.25;
    -moz-tab-size: 2;
    -o-tab-size: 2;
    tab-size: 2;
    -webkit-hyphens: none;
    -moz-hyphens: none;
    -ms-hyphens: none;
    hyphens: none;
    padding: 1em;
    margin: 0.5em 0;
    overflow: auto;
    border-radius: 10px;
    display: block;
    max-height: 485px;
  }
  
  @media (max-width: 768px) {
    .code-container {
      overflow: hidden;
    }
    
    .navigation-controls {
      margin-top: 1rem;
    }
    
    .tags-container {
      max-height: 120px;
    }
    
    .left-column {
      min-height: auto;
    }
  }
</style>
