<script>
  let name = "";
  let email = "";
  let role = "Freelancer"; // default selection
  let message = "";
  let error = "";
  let showPopup = false; // popup state

  async function submitForm() {
    message = "";
    error = "";
    showPopup = false;

    try {
      const res = await fetch("https://dev-wpsia.pantheonsite.io/wp-json/contact/v1/submit", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ name, email, role })
      });

      const data = await res.json();

      if (res.ok && data.success) {
        message = data.message;
        name = "";
        email = "";
        role = "Freelancer"; // reset to default
        showPopup = true; // show popup
      } else {
        error = data.error || "Submission failed.";
      }
    } catch (err) {
      error = "Network error. Please try again.";
    }
  }

  function closePopup() {
    showPopup = false;
  }
</script>

<style>
  .form-container {
    display: flex;
    gap: 2rem;
    max-width: 1000px;
    margin: 2rem auto;
    align-items: flex-start;
  }

  .left {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .left img {
    max-width: 90%;
    border-radius: 10px;
  }

  .right {
    flex: 1.2;
    padding: 2.5rem;
    border-radius: 10px;
    background-color: #ffffff !important;
  }

  form {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }

  input[type="text"], input[type="email"] {
    width: 100%;
    padding: 0.8rem;
    font-size: 1rem;
    border: none;
    border-bottom: 2px solid #ccc;
    outline: none;
    background: transparent;
    transition: border-color 0.3s ease;
  }

  input[type="text"]:focus, input[type="email"]:focus {
    border-bottom-color: #654dfb;
  }

  /* Radio button group */
  .radio-group {
    display: flex;
    gap: 2rem;
    margin-top: 0.5rem;
    padding-left: 3%;
    flex-wrap: wrap;
  }

  .radio-option {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    cursor: pointer;
    font-size: 1rem;
  }

  input[type="radio"] {
    accent-color: #654dfb;
    width: 18px;
    height: 18px;
    cursor: pointer;
  }

  button {
    padding: 0.9rem;
    background: var(--gradient);
    color: #fff;
    font-weight: bold;
    cursor: pointer;
    border: none;
    border-radius: 6px;
    font-size: 1rem;
  }

  button:hover {
    background: var(--gradient);
  }

  .success {
    color: green;
    margin-top: 1rem;
  }

  .error {
    color: red;
    margin-top: 1rem;
  }

  .right p {
    margin-bottom: 24px; 
  }
  .right h2 {
    font-size: 2rem;
    margin-bottom:2%;
  }
  .role {
    padding-left: 3%;
  }

  /* Popup Overlay */
  .popup-overlay {
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: rgba(0,0,0,0.7);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  .popup {
    background: #fff;
    padding: 2rem;
    border-radius: 12px;
    max-width: 500px;
    width: 90%;
    text-align: center;
    position: relative;
    animation: fadeIn 0.3s ease;
  }

  .popup h2 {
    font-size: 1.4rem;
    margin-bottom: 1rem;
    color: #654dfb;
  }

  .popup p {
    margin-bottom: 1rem;
    font-size: 0.9rem;
  }

  /* Close Icon */
  .close-icon {
    position: absolute;
    top: -5px;
    right: 12px;
    font-size: 1.5rem;
    font-weight: bold;
    color: #333;
    cursor: pointer;
    transition: color 0.2s ease;
  }

  .close-icon:hover {
    color: #654dfb;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: scale(0.95); }
    to { opacity: 1; transform: scale(1); }
  }

  /* Responsive design */
  @media (max-width: 768px) {
    .form-container {
      flex-direction: column;
      gap: 1.5rem;
      padding: 1rem;
    }

    .left img {
      max-width: 100%;
    }

    .right {
      padding: 1.5rem;
    }

    .right h2 {
      font-size: 1.5rem;
    }

    .radio-group {
      gap: 1rem;
      padding-left: 0;
    }

    .radio-option {
      font-size: 0.95rem;
    }

    button {
      font-size: 0.95rem;
      padding: 0.8rem;
    }
  }

  @media (max-width: 480px) {
    .form-container {
      margin: 1rem;
    }

    .right h2 {
      font-size: 1.3rem;
    }

    input[type="text"], input[type="email"] {
      font-size: 0.9rem;
      padding: 0.7rem;
    }

    .radio-option {
      font-size: 0.9rem;
    }

    button {
      font-size: 0.9rem;
      padding: 0.7rem;
    }
  }
</style>

<div class="form-container">
  <!-- Left: Image -->
  <div class="left">
    <img src="assets/Contact.png" alt="Contact us" />
  </div>

  <!-- Right: Form -->
  <div class="right">
    <h2>Claim Your Free Pro & Agency License – Early Access</h2>
   <p>Download and start using the Free plugin today. If you’re among the first 100 to request early access, we’ll email your Pro/Agency license key and ZIP on launch day. 
   <br>Giving you all features at no cost, lifetime updates and support, and early access to new tools while helping shape the product.</p>
    <form on:submit|preventDefault={submitForm}>
      <input type="text" placeholder="Name" bind:value={name} required />
      <input type="email" placeholder="Email" bind:value={email} required />

      <div>
        <label class="role">Role:</label>
        <div class="radio-group">
          <label class="radio-option">
            <input type="radio" value="Freelancer" bind:group={role} /> Freelancer
          </label>
          <label class="radio-option">
            <input type="radio" value="Agency" bind:group={role} /> Agency
          </label>
          <label class="radio-option">
            <input type="radio" value="Hosting Provider" bind:group={role} /> Hosting Provider
          </label>
        </div>
      </div>

      <button type="submit">Join Early Access – Claim Free License</button>
    </form>

    {#if message}
      <p class="success">{message}</p>
    {/if}
    {#if error}
      <p class="error">{error}</p>
    {/if}
  </div>
</div>

{#if showPopup}
  <div class="popup-overlay">
    <div class="popup">
      <span class="close-icon" on:click={closePopup}>&times;</span>
      <h2>Thank You for Joining Early Access!</h2>
      <p>We’ve received your request for a free Pro/Agency license.<br>
      Your <strong>license key + Pro/Agency ZIP will be mailed to you on launch day</strong>.<br>
      Meanwhile, you can start using the Free plugin today.</p>
      <button><a href="https://github.com/prathushan/WP-Site-Inspector-Agent/archive/refs/heads/main.zip">Download Free Zip</a></button>
    </div>
  </div>
{/if}
