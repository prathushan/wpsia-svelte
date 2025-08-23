<script>
  export let data;
</script>

<footer>
  <div class="container">
    <div class="footer-grid">
      <div>
        <div class="footer-logo">
          <div class="footer-logo-text">{data.footer.logo.text}<span>{data.footer.logo.highlight}</span></div>
        </div>
        <p class="footer-desc">{data.footer.description}</p>
        <div class="social-links">
          {#each data.footer.social as link}
            <a href={link.href} aria-label="social-link" class="social-link"><i class={link.icon}></i></a>
          {/each}
        </div>
      </div>
      
      {#each data.footer.sections as section}
        <div>
          <h3 class="footer-title">{section.title}</h3>
          <ul class="footer-links">
            {#each section.links as link}
              <li><a href={link.href}>{link.text}</a></li>
            {/each}
          </ul>
        </div>
      {/each}
    </div>
    
    <div class="footer-bottom">
      <p>{data.footer.copyright}</p>
    </div>
  </div>
</footer>