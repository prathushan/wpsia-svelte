<script>
  export let data;

  let scrolled = false;
  let menuOpen = false; // for mobile hamburger

  function handleScroll() {
    scrolled = window.scrollY > 50;
  }

  if (typeof window !== 'undefined') {
    window.addEventListener('scroll', handleScroll);
  }

  function smoothScroll(e, targetId) {
    e.preventDefault();
    if (targetId === '#') return;

    const targetElement = document.querySelector(targetId);
    if (targetElement) {
      window.scrollTo({
        top: targetElement.offsetTop - 80,
        behavior: 'smooth'
      });
    }

    // Close mobile menu after clicking
    menuOpen = false;
  }

  function toggleMenu() {
    menuOpen = !menuOpen;
  }
</script>

<header class:scrolled>
  <div class="container header-container">
    <div class="logo">
      <div class="logo-text">{data.header.logo.text}<span>{data.header.logo.highlight}</span></div>
    </div>

    <!-- Hamburger for Mobile -->
    <div class="hamburger" on:click={toggleMenu}>
      <span class:open={menuOpen}></span>
      <span class:open={menuOpen}></span>
      <span class:open={menuOpen}></span>
    </div>

    <nav class:open={menuOpen} class="nav-menu">
      {#each data.header.nav as item}
        <a href={item.href} class="nav-link" on:click={(e) => smoothScroll(e, item.href)}>
          {item.text}
        </a>
      {/each}

      <!-- CTA buttons inside mobile menu -->
      <div class="header-cta-mobile">
        {#each data.header.cta as button}
          <a href={button.href} class="btn btn-{button.style}">{button.text}</a>
        {/each}
      </div>
    </nav>

    <!-- Desktop CTA -->
    <div class="header-cta">
      {#each data.header.cta as button}
        <a href={button.href} class="btn btn-{button.style}">{button.text}</a>
      {/each}
    </div>
  </div>
</header>


