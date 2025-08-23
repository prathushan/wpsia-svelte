<!-- src/routes/+page.svelte -->
<script>
    
  import Header from '$lib/components/Header.svelte';
  import Hero from '$lib/components/Hero.svelte';
  import Features from '$lib/components/Features.svelte';
  import HowItWorks from '$lib/components/HowItWorks.svelte';
  import Testimonials from '$lib/components/Testimonials.svelte';
  import Cta from '$lib/components/Cta.svelte';
  import Footer from '$lib/components/Footer.svelte';
  
  // Import data from JSON
  import data from '$lib/data.json';
  import Accessibility from '$lib/components/Accessibility.svelte';
  import AiModels from '$lib/components/AiModels.svelte';
  import Pricing from '$lib/components/Pricing.svelte';
  import Faq from '$lib/components/FAQ.svelte';
</script>

<Header {data} />
<Hero {data} />
<Features {data} />
<HowItWorks {data} />
<Accessibility {data} />
<AiModels {data} />
<Pricing {data} />
<Testimonials {data} />
<Faq {data} />
<Cta {data} />
<Footer {data} />