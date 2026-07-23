<script>
  import { onMount, onDestroy } from "svelte";
  import { fade, fly } from "svelte/transition";
  import { cubicInOut } from "svelte/easing";
  const whatWeDo = [
    {
      title: "Training & Readiness",
      icon: "🎯",
      items: [
        "Workshops and deep-dive bootcamps",
        "Online delivered presentations and demos",
        "Half day technology updates",
        "1-day overview and scenario-based sessions",
        "Multi-day deep-dive with real-world experience",
        "Focus group discussions"
      ]
    },
    {
      title: "Professional Technology Consulting",
      icon: "🧭",
      items: [
        "Hybrid Cloud & On-Prem IT Strategy Consulting",
        "Pre-Sales Support for IT Distributors & Partners",
        "IT Solution Architecture & Implementation"
      ]
    },
    {
      title: "Go-To-Market & Business Growth",
      icon: "📈",
      items: [
        "Partner Enablement & Technical Pre-Sales Support",
        "Microsoft Solution GTM Planning & Execution",
        "Distributor & Channel Partner Training"
      ]
    },
    {
      title: "RFP & Proposal Support",
      icon: "📝",
      items: [
        "Technical Documentation & Proposal Writing",
        "IT Solution Design for Large-Scale Projects",
        "Partner Collaboration for Microsoft Solution Bidding"
      ]
    },
    {
      title: "From Concept to Reality",
      icon: "🚀",
      items: [
        "Solution positioning to deal closure",
        "Productization of services from start to market"
      ]
    }
  ];
  // --- Carousel Data (Services) ---
  let currentSlide = 0;
  const carouselItems = [
    {
      title: "Technology Consulting",
      description: "Hybrid cloud and on-prem IT strategy, solution architecture, and pre-sales support to help you chart a clear path for digital transformation.",
      icon: "🧠"
    },
    {
      title: "Migrations",
      description: "Seamless migration of data, workloads, and identities — on-prem to cloud, cross-platform, tenant-to-tenant, and VMware to Microsoft.",
      icon: "☁️"
    },
    {
      title: "Corporate Training",
      description: "Hands-on training for Microsoft 365, Azure, Windows Server, and Copilot — led by a Microsoft Certified Trainer.",
      icon: "🎓"
    },
    {
      title: "Implementations",
      description: "Deploy modern IT solutions like Microsoft 365, Windows Server, Azure Stack HCI, and Azure Virtual Desktop tailored to your environment.",
      icon: "⚙️"
    }
  ];

  const nextSlide = () => {
    currentSlide = (currentSlide + 1) % carouselItems.length;
  };

  const prevSlide = () => {
    currentSlide = (currentSlide - 1 + carouselItems.length) % carouselItems.length;
  };

  // --- Auto-play Carousel ---
  /** @type {number | undefined} */
  let interval;
  onMount(() => {
    interval = setInterval(nextSlide, 5000);
  });
  onDestroy(() => clearInterval(interval));

  // --- Pillar Cards ---
  const pillarCards = [
    {
      title: "Making Potential a Reality",
      text: "We believe in turning potential into reality by providing the right tools, training, and support to help businesses thrive in the digital age.",
      color: "from-[#0a1a4a] to-blue-800"
    },
    {
      title: "Making It Happen",
      text: "Our commitment to excellence ensures that we deliver on our promises, helping you achieve your IT goals efficiently and effectively.",
      color: "from-[#6a1b1b] to-red-800"
    },
    {
      title: "People to People",
      text: "We focus on mentoring and grooming your team so they're ready to tackle any IT challenge with confidence.",
      color: "from-[#0a1a4a] to-blue-800"
    }
  ];

  // --- Where We Deliver Value ---
  const valueItems = [
    "Microsoft 365 Implementation & Licensing",
    "Hybrid Cloud with Azure Stack HCI",
    "Infrastructure Modernization (Windows Server, VMware to Microsoft)",
    "Tenant-to-Tenant Migrations",
    "Corporate IT Training & User Readiness",
    "Cloud Evaluation & Migration (Azure, AWS, GCP)",
    "Rescue & Recovery for failed or incomplete IT projects"
  ];
  const goToSlide = (i) => {
    currentSlide = i;
  };
  let showIntro = true;

  const taglineWords = ["Making", "Potential", "a", "Reality."];

  onMount(() => {
    document.body.style.overflow = "hidden";
    const t = setTimeout(() => {
      showIntro = false;
      document.body.style.overflow = "";
    }, 1500);
    return () => clearTimeout(t);
  });

  const skipIntro = () => {
    showIntro = false;
    document.body.style.overflow = "";
  };
</script>

<!-- --- Main Layout --- -->
<div class=" text-gray-900 overflow-hidden ">
  {#if showIntro}
    <div
      class="fixed inset-0 z-[100] flex flex-col items-center justify-center overflow-hidden bg-[#0b0b14]"
      out:fly={{ y: -60, duration: 700, easing: cubicInOut }}
    >
      <!-- Background texture: spotlight + drifting light beams -->
      <div class="absolute inset-0 animate-spotlight-drift" style="background: radial-gradient(circle at 50% 45%, rgba(106,27,27,0.35), transparent 55%);"></div>
      <div class="absolute inset-0 opacity-40 animate-beam-sweep" style="background: linear-gradient(115deg, transparent 30%, rgba(10,26,74,0.5) 45%, rgba(255,255,255,0.06) 50%, rgba(10,26,74,0.5) 55%, transparent 70%); background-size: 250% 250%;"></div>
      <div class="absolute inset-0 opacity-[0.05]" style="background-image: linear-gradient(white 1px, transparent 1px), linear-gradient(90deg, white 1px, transparent 1px); background-size: 48px 48px;"></div>
      <div class="absolute inset-0 bg-gradient-to-b from-transparent via-transparent to-[#0b0b14]"></div>

      <!-- Logo mark -->
      <div
        class="mb-8 w-16 h-16 rounded-2xl bg-white/10 backdrop-blur-md border border-white/20 flex items-center justify-center"
        in:fly={{ y: 20, duration: 600, delay: 100 }}
      >
        <span class="text-3xl">⚡</span>
      </div>

      <!-- Staggered tagline -->
      <h1 class="relative z-10 flex flex-wrap justify-center gap-x-4 px-6 text-4xl md:text-6xl font-bold text-white tracking-tight text-center">
        {#each taglineWords as word, i}
          <span
            class="inline-block"
            in:fly={{ y: 30, duration: 600, delay: 300 + i * 150, easing: cubicInOut }}
          >
            {word}
          </span>
        {/each}
      </h1>

      <p
        class="relative z-10 mt-6 text-gray-300 text-base md:text-lg tracking-wide"
        in:fade={{ duration: 600, delay: 300 + taglineWords.length * 150 + 200 }}
      >
        TechReady Solutions
      </p>

      <!-- Progress line -->
      <div class="absolute bottom-14 w-40 h-0.5 bg-white/20 rounded-full overflow-hidden">
        <span class="block h-full bg-white rounded-full animate-intro-progress"></span>
      </div>

      <!-- Skip -->
      <button
        on:click={skipIntro}
        class="absolute bottom-6 text-xs text-white/50 hover:text-white/90 tracking-wide transition-colors"
      >
        Skip →
      </button>
    </div>
  {/if}
  <!-- --- Hero Carousel --- -->
  <section class="relative flex flex-col items-center justify-center text-center px-6 min-h-[80vh] overflow-hidden">

  <!-- Layered animated background -->
  <div class="absolute inset-0 bg-gradient-to-br from-[#0a1a4a] via-[#3a1a3a] to-[#6a1b1b] bg-[length:200%_200%] animate-gradient-pan"></div>
  <div class="absolute -top-32 -left-24 w-96 h-96 bg-blue-500/20 rounded-full blur-3xl animate-blob-float"></div>
  <div class="absolute -bottom-32 -right-24 w-96 h-96 bg-red-500/20 rounded-full blur-3xl animate-blob-float-delayed"></div>
  <div class="absolute inset-0 opacity-[0.07]" style="background-image: radial-gradient(circle, white 1px, transparent 1px); background-size: 28px 28px;"></div>
  <div class="absolute inset-0 bg-black/10"></div>

  <!-- Slide content — fixed-height stage so slides overlap instead of pushing layout -->
  <div class="relative z-10 w-full max-w-3xl h-[280px] md:h-[260px] flex items-center justify-center">
    {#key currentSlide}
      <div
        in:fly={{ y: 16, duration: 700, easing: cubicInOut }}
        out:fly={{ y: -16, duration: 700, easing: cubicInOut }}
        class="absolute inset-0 flex flex-col items-center justify-center text-white"
      >
        <div class="mb-7 flex items-center justify-center w-24 h-24 rounded-2xl bg-white/10 backdrop-blur-md border border-white/20 shadow-xl">
          <span class="text-5xl">{carouselItems[currentSlide].icon}</span>
        </div>

        <h2 class="text-4xl md:text-5xl font-bold mb-4 tracking-tight">
          {carouselItems[currentSlide].title}
        </h2>
        <div class="w-16 h-1 rounded-full bg-white/50 mb-5"></div>

        <p class="text-lg md:text-xl text-gray-200 leading-relaxed px-4 max-w-2xl">
          {carouselItems[currentSlide].description}
        </p>
      </div>
    {/key}
  </div>

  <!-- Carousel Controls -->
  <div class="absolute bottom-14 flex items-center gap-5 z-20">
    <button
      on:click={prevSlide}
      class="group p-3 bg-white/10 rounded-full border border-white/20 backdrop-blur-md hover:bg-white/20 hover:scale-110 transition-all duration-300"
      aria-label="Previous Slide">
      <svg class="w-4 h-4 text-white transition-transform group-hover:-translate-x-0.5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
        <path d="M15 18l-6-6 6-6" />
      </svg>
    </button>
    <button
      on:click={nextSlide}
      class="group p-3 bg-white/10 rounded-full border border-white/20 backdrop-blur-md hover:bg-white/20 hover:scale-110 transition-all duration-300"
      aria-label="Next Slide">
      <svg class="w-4 h-4 text-white transition-transform group-hover:translate-x-0.5" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
        <path d="M9 18l6-6-6-6" />
      </svg>
    </button>
  </div>

  <!-- Slide Indicators with autoplay progress -->
  <div class="absolute bottom-6 flex justify-center gap-2.5 z-20">
    {#each carouselItems as _, i}
      <button
        on:click={() => goToSlide(i)}
        aria-label={`Go to slide ${i + 1}`}
        class="relative h-1.5 rounded-full bg-white/25 overflow-hidden transition-all duration-500"
        class:w-8={i === currentSlide}
        class:w-1.5={i !== currentSlide}
      >
        {#if i === currentSlide}
          {#key currentSlide}
            <span class="absolute inset-0 bg-white rounded-full origin-left animate-progress"></span>
          {/key}
        {/if}
      </button>
    {/each}
  </div>
</section>

<style>
  @keyframes gradient-pan {
    0%   { background-position: 0% 50%; }
    50%  { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }
  .animate-gradient-pan {
    animation: gradient-pan 12s ease-in-out infinite;
  }

  @keyframes blob-float {
    0%, 100% { transform: translate(0, 0) scale(1); }
    50%      { transform: translate(30px, 20px) scale(1.1); }
  }
  .animate-blob-float {
    animation: blob-float 9s ease-in-out infinite;
  }
  .animate-blob-float-delayed {
    animation: blob-float 9s ease-in-out infinite;
    animation-delay: 3s;
  }

  @keyframes progress {
    from { transform: scaleX(0); }
    to   { transform: scaleX(1); }
  }
  .animate-progress {
    animation: progress 5s linear forwards;
  }
  @keyframes intro-progress {
    from { transform: scaleX(0); transform-origin: left; }
    to   { transform: scaleX(1); transform-origin: left; }
  }
  .animate-intro-progress {
    animation: intro-progress 1.5s linear forwards;
  }
</style>

  <!-- --- What We Do Section --- -->
  <section id="services" class="max-w-6xl mx-auto py-20 px-6">
    <div class="relative rounded-3xl bg-gradient-to-r from-[#0a1a4a] to-[#6a1b1b] text-white px-8 py-16 shadow-lg overflow-hidden">
      <div class="relative z-10 flex flex-col md:flex-row items-center justify-between gap-10">
        <div class="max-w-2xl">
          <h3 class="text-4xl font-semibold mb-4">What We Do</h3>
          <p class="text-lg text-gray-200 leading-relaxed">
            At TechReady Solutions, we specialize in Technology Consulting, Implementation, Migrations,
            and IT services tailored for businesses of all sizes. From Microsoft ecosystem deployments to
            hybrid cloud strategies, we help you transform, optimize, and future-proof your IT operations.
          </p>
        </div>

        <a href="/contact" class="rounded-xl bg-white text-[#0a1a4a] font-semibold px-8 py-4 shadow-lg hover:bg-gray-100 transition-all whitespace-nowrap">
          Contact Us
        </a>
      </div>
      <div class="absolute inset-0 bg-gradient-to-tr from-white/5 to-transparent"></div>
    </div>
  </section>

  <!-- --- Vision Section --- -->
  <section class="max-w-4xl mx-auto py-4 px-6 text-center">
    <h3 class="text-3xl font-semibold mb-4 text-[#0a1a4a]">Our Vision</h3>
    <p class="text-lg text-gray-700 leading-relaxed">
      To simplify and strengthen IT transformation for businesses by aligning technology
      with purpose, scalability, and measurable outcomes.
    </p>
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
    <!-- --- What We Do (Detailed) --- -->
  <section class="max-w-7xl mx-auto py-16 px-6">
    <div class="text-center max-w-3xl mx-auto mb-14" in:fly={{ y: 20, duration: 600 }}>
      <h3 class="text-3xl md:text-4xl font-semibold text-[#0a1a4a] mb-4">What We Do</h3>
      <p class="text-gray-600 leading-relaxed">
        We focus on mentoring and grooming your team to ensure they are ready to tackle any IT challenge with confidence.
      </p>
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
      {#each whatWeDo as block, i}
        <div
          class="group relative rounded-3xl bg-white p-8 border border-gray-100 shadow-sm
                hover:shadow-2xl hover:-translate-y-2 transition-all duration-500 ease-out overflow-hidden"
          in:fly={{ y: 30, duration: 500, delay: 100 * i }}
        >
          <!-- Animated gradient border glow on hover -->
          <div class="absolute inset-0 rounded-3xl bg-gradient-to-br from-[#0a1a4a] to-[#6a1b1b]
                      opacity-0 group-hover:opacity-100 transition-opacity duration-500 -z-10 blur-xl scale-95 group-hover:scale-100"></div>
          <div class="absolute inset-[1px] rounded-3xl bg-white -z-10"></div>

          <!-- Icon -->
          <div class="w-14 h-14 flex items-center justify-center rounded-2xl bg-gradient-to-br from-[#0a1a4a]/10 to-[#6a1b1b]/10
                      text-3xl mb-6 transition-all duration-500 group-hover:scale-110 group-hover:rotate-6
                      group-hover:from-[#0a1a4a] group-hover:to-[#6a1b1b]">
            {block.icon}
          </div>

          <h4 class="text-xl font-semibold text-[#0a1a4a] mb-4 transition-colors duration-300 group-hover:text-[#6a1b1b]">
            {block.title}
          </h4>

          <ul class="space-y-2.5">
            {#each block.items as item}
              <li class="flex items-start gap-2.5 text-sm text-gray-600 leading-relaxed">
                <span class="mt-1.5 w-1.5 h-1.5 rounded-full bg-[#6a1b1b] shrink-0"></span>
                {item}
              </li>
            {/each}
          </ul>
        </div>
      {/each}
    </div>
  </section>

  <!-- --- Where We Deliver Value --- -->
  <section class="max-w-6xl mx-auto py-16 px-6">
    <h3 class="text-3xl font-semibold mb-10 text-center text-[#0a1a4a]">Where We Deliver Value</h3>
    <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
      {#each valueItems as item}
        <div class="flex items-start gap-3 p-5 rounded-2xl border border-gray-100 shadow-sm hover:shadow-md transition-all">
          <span class="text-[#6a1b1b] text-xl leading-none">●</span>
          <p class="text-gray-800">{item}</p>
        </div>
      {/each}
    </div>
  </section>

  
</div>