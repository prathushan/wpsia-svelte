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
  import Workflow from '$lib/components/Workflow.svelte';
  import Models from '$lib/components/Models.svelte';
  import ContactUs from '$lib/components/Contact_us.svelte';
  import Language from '$lib/components/Language.svelte';
</script>

<Header {data} />
<Hero {data} />
<Features {data} />
<HowItWorks {data} />
<Accessibility {data} />
<Models />
<!-- <AiModels {data} /> -->
<Language />
<Pricing {data} />
<Testimonials {data} />
<Cta {data} />

<Faq {data} />
<ContactUs />
<Footer {data} />