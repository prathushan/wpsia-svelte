<!-- src/lib/components/Languages.svelte -->
<script>
  let languages = [
    { name: "English", flag: "🇺🇸" },
    { name: "Spanish", flag: "🇪🇸" },
    { name: "French", flag: "🇫🇷" },
    { name: "German", flag: "🇩🇪" }
   
  ];
</script>

<section class="languages bg-change" id="languages">
  <div class="container">
  <div class="section-header">
    <h2>Unlock Global Access</h2>
    <p>WP-Site-Inspector Now in Multiple Languages!</p>
  </div>

  <div class="scroll-wrapper">
    <div class="scroll-track">
      <!-- Repeat languages multiple times -->
      {#each Array(6).fill(languages).flat() as lang, i}
        <div class="lang-card" key={i}>
          <span class="flag">{lang.flag}</span>
          <span class="name">{lang.name}</span>
        </div>
      {/each}
    </div>
  </div>
  </div>
</section>

<style>
.languages {
  text-align: center;
  padding: 60px 20px;
}

.section-header h2 {
  font-size: 2.5rem;
  font-weight: bold;
  margin-bottom: 10px;
}

.section-header p {
  font-size: 1.125rem;
  color: #555;
  margin-bottom: 30px;
}

.scroll-wrapper {
  width: 100%;
  overflow: hidden;
  position: relative;
  padding: 20px 0;
}

.scroll-track {
  display: flex;
  gap: 40px;
  width: max-content;
  animation: scroll-left 75s linear infinite; /* slower because more items */
}

.lang-card {
  display: flex;
  flex-direction: column;   /* ✅ stack vertically */
  align-items: center;      /* ✅ center horizontally */
  justify-content: center;
  font-size: 1.2rem;
  background: #fff;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
  border-radius: 12px;
  padding: 15px 25px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
  flex-shrink: 0;
  transition: all 0.3s ease;
}

.lang-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 30px rgba(64, 86, 227, 0.73);
}


.flag {
  font-size: 4rem;   /* make flag big */
  line-height: 1;
  margin-bottom: 8px;
}

.name {
  font-size: 1rem;
  font-weight: 500;
  color: #333;
}

/* Infinite scroll */
@keyframes scroll-left {
  0%   { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
</style>
