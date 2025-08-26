<script>
  let name = "";
  let email = "";
  let role = "Freelancer"; // default selection
  let message = "";
  let error = "";
 
  async function submitForm() {
    message = "";
    error = "";
 
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
      } else {
        error = data.error || "Submission failed.";
      }
    } catch (err) {
      error = "Network error. Please try again.";
    }
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
    max-width: 80%;
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
    flex-wrap: wrap; /* so radios wrap on smaller screens */
  }
 
  .radio-option {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    cursor: pointer;
    font-size: 1rem;
  }
 
  input[type="radio"] {
    accent-color: #654dfb; /* modern browsers */
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
    margin-bottom: 40px;
  }
  .right h2 {
    font-size: 2rem;
  }
  .role {
    padding-left: 3%;
  }
 
  /* ✅ Responsive design */
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
    <h2>Still Have a Question?</h2>
    <p>We're here to help!</p>
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
 
      <button type="submit">Contact Us</button>
    </form>
 
    {#if message}
      <p class="success">{message}</p>
    {/if}
    {#if error}
      <p class="error">{error}</p>
    {/if}
  </div>
</div>