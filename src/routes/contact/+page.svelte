<script>
  // Static contact details (easy to change later)
  const contactDetails = [
    {
      title: "Phone",
      icon: "📞",
      value: "+1 (555) 123-4567",
      note: "Mon – Fri, 9:00 AM – 6:00 PM"
    },
    {
      title: "Email",
      icon: "✉️",
      value: "info@techreadysolutions.com",
      note: "We usually respond within 24 hours"
    },
    {
      title: "Address",
      icon: "📍",
      value: `TechReady Solutions
123 Innovation Drive,
Suite 400,
San Jose, CA 95110, USA`
    }
  ];
</script>

<!-- Hero Section -->
<section class="contact-hero">
  <h1>Contact Us</h1>
  <p>
    We’re here to help. Reach out to TechReady Solutions through any of the channels below.
  </p>
</section>

<!-- Contact Cards -->
<section class="contact-container">
  {#each contactDetails as item}
    <div class="contact-card">
      <h3>{item.icon} {item.title}</h3>
      <p class="value">{item.value}</p>
      {#if item.note}
        <span class="note">{item.note}</span>
      {/if}
    </div>
  {/each}
</section>

<!-- Map Section -->
<section class="map-section">
  <h2>Find Us</h2>
  <div class="map-container">
    <iframe
      src="https://www.google.com/maps?q=San%20Jose%20CA%2095110&t=&z=13&ie=UTF8&iwloc=&output=embed"
      loading="lazy"
      referrerpolicy="no-referrer-when-downgrade"
      allowfullscreen>
    </iframe>
  </div>
</section>

<style>
  /* Hero */
  .contact-hero {
    background: linear-gradient(135deg, #1e3a8a, #7f1d1d);
    color: #fff;
    text-align: center;
    padding: 80px 20px;
  }

  .contact-hero h1 {
    font-size: 2.4rem;
    margin-bottom: 10px;
  }

  .contact-hero p {
    max-width: 700px;
    margin: 0 auto;
    opacity: 0.9;
    font-size: 1rem;
  }

  /* Cards */
  .contact-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 24px;
    padding: 60px 8%;
  }

  .contact-card {
    background: linear-gradient(135deg, #0f2a6d, #7f1d1d);
    color: #fff;
    padding: 30px;
    border-radius: 14px;
    box-shadow: 0 12px 30px rgba(0, 0, 0, 0.15);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .contact-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 16px 40px rgba(0, 0, 0, 0.25);
  }

  .contact-card h3 {
    margin-bottom: 12px;
    font-size: 1.2rem;
  }

  .value {
    white-space: pre-line;
    font-size: 0.95rem;
    line-height: 1.6;
  }

  .note {
    display: block;
    margin-top: 8px;
    font-size: 0.8rem;
    opacity: 0.85;
  }

  /* Map */
  .map-section {
    padding: 40px 8% 80px;
    text-align: center;
  }

  .map-section h2 {
    margin-bottom: 20px;
    font-size: 1.8rem;
  }

  .map-container {
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 14px 40px rgba(0, 0, 0, 0.2);
  }

  .map-container iframe {
    width: 100%;
    height: 380px;
    border: none;
  }

  @media (max-width: 768px) {
    .contact-hero {
      padding: 60px 16px;
    }

    .contact-container {
      padding: 40px 6%;
    }
  }
</style>
