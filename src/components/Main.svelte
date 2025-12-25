<script>
  import { onMount, onDestroy } from "svelte";

  // --- Carousel Data ---
  let currentSlide = 0;
  const carouselItems = [
    { 
      title: "Technology Consulting", 
      description: "From strategy to execution, we provide expert guidance to align your IT with business goals. Let us help you chart a clear path for digital transformation.",
      icon: "🧠"
    },
    { 
      title: "Cloud Migration Services", 
      description: "Seamlessly transition your infrastructure to Azure. We handle planning, execution, and optimization to minimize downtime.",
      icon: "☁️"
    },
    { 
      title: "Managed IT Services", 
      description: "24/7 proactive monitoring, security management, and support, ensuring your systems are always available, secure, and performing optimally.",
      icon: "🛡️"
    },
    { 
      title: "IT Staff Augmentation", 
      description: "Scale your team quickly with highly skilled IT professionals tailored to your specific project needs and company culture.",
      icon: "🤝"
    },
  ];

  const nextSlide = () => {
    currentSlide = (currentSlide + 1) % carouselItems.length;
  };

  const prevSlide = () => {
    currentSlide = (currentSlide - 1 + carouselItems.length) % carouselItems.length;
  };

  // --- Auto-play Carousel ---
  /**
     * @type {number | undefined}
     */
  let interval;
  onMount(() => {
    interval = setInterval(nextSlide, 5000); // Change every 5s
  });
  onDestroy(() => clearInterval(interval));

  // --- Cards Data ---
  const pillarCards = [
    { 
      title: "Making Potential a Reality", 
      text: "We help organizations turn potential into performance with the right IT tools, strategy, and support.",
      color: "from-[#0a1a4a] to-blue-800"
    },
    { 
      title: "Making It Happen", 
      text: "With expert guidance and proven solutions, we ensure smooth execution of your technology vision.",
      color: "from-[#6a1b1b] to-red-800"
    },
    { 
      title: "People to People", 
      text: "Empowering your team through mentorship and training to tackle IT challenges confidently.",
      color: "from-[#0a1a4a] to-blue-800"
    },
  ];
</script>

<!-- --- Main Layout --- -->
<div class="pt-24 text-gray-900 overflow-hidden">

  <!-- --- Hero Carousel --- -->
  <section class="relative flex flex-col items-center justify-center text-center px-6 min-h-[70vh]">
    <div class="absolute inset-0 bg-gradient-to-r from-[#0a1a4a] to-[#6a1b1b] opacity-90"></div>

    <!-- Carousel Slide -->
    <div class="relative z-10 max-w-3xl text-white transition-all duration-700 ease-in-out">
      <div class="flex flex-col items-center">
        <div class="text-6xl mb-6 animate-bounce">{carouselItems[currentSlide].icon}</div>
        <h2 class="text-4xl md:text-5xl font-bold mb-4">{carouselItems[currentSlide].title}</h2>
        <p class="text-lg md:text-xl text-gray-200 leading-relaxed px-4">{carouselItems[currentSlide].description}</p>
      </div>
    </div>

    <!-- Carousel Controls -->
    <div class="absolute bottom-6 flex items-center gap-4 z-20">
      <button
        on:click={prevSlide}
        class="p-2 bg-white/20 rounded-full hover:bg-white/40 transition"
        aria-label="Previous Slide">
        ◀
      </button>
      <button
        on:click={nextSlide}
        class="p-2 bg-white/20 rounded-full hover:bg-white/40 transition"
        aria-label="Next Slide">
        ▶
      </button>
    </div>

    <!-- Slide Indicators -->
    <div class="absolute bottom-2 flex justify-center gap-2">
      {#each carouselItems as _, i}
        <span
          class="h-2 w-2 rounded-full transition-all duration-300"
          class:bg-white={i === currentSlide}
          ></span>
      {/each}
    </div>
  </section>

  <!-- --- What We Do Section --- -->
  <section id="services" class="max-w-6xl mx-auto py-20 px-6">
    <div class="relative rounded-3xl bg-gradient-to-r from-[#0a1a4a] to-[#6a1b1b] text-white px-8 py-16 shadow-lg overflow-hidden">
      <div class="relative z-10 flex flex-col md:flex-row items-center justify-between gap-10">
        <div class="max-w-2xl">
          <h3 class="text-4xl font-semibold mb-4">What We Do</h3>
          <p class="text-lg text-gray-200 leading-relaxed">
            At TechReady Solutions, we specialize in technology consulting, migrations, and managed IT services.
            From Microsoft ecosystem deployments to hybrid cloud strategies, we help you transform and future-proof your IT operations.
          </p>
        </div>

        <a href="/contact" class="rounded-xl bg-white text-[#0a1a4a] font-semibold px-8 py-4 shadow-lg hover:bg-gray-100 transition-all">
          Contact Us
        </a>
      </div>
      <div class="absolute inset-0 bg-gradient-to-tr from-white/5 to-transparent"></div>
    </div>
  </section>

  <!-- --- Pillar Cards --- -->
  <section class="max-w-7xl mx-auto py-16 px-6 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-10">
    {#each pillarCards as card}
      <div
        class="p-8 rounded-3xl shadow-lg border border-gray-100 bg-gradient-to-br {card.color} text-white hover:shadow-xl hover:-translate-y-1 transition-all duration-300">
        <h2 class="text-2xl font-semibold mb-3 text-center">{card.title}</h2>
        <p class="text-gray-100 text-center leading-relaxed">{card.text}</p>
      </div>
    {/each}
  </section>
</div>
