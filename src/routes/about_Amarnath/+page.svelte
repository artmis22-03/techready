<script>
  import { onMount } from "svelte";
  import { fade, fly } from "svelte/transition";
  import { cubicInOut } from "svelte/easing";

  let visible = false;
  onMount(() => {
    visible = true;
  });

  const stats = [
    { value: "20+", label: "Years in IT Industry" },
    { value: "3", label: "Regions — India, EMEA, SEA" },
    { value: "MCT", label: "Microsoft Certified Trainer" },
    { value: "GTM", label: "Strategy for Global LDPs" }
  ];

  const expertise = [
    {
      icon: "☁️",
      title: "Cloud Transformation",
      text: "Driving cloud adoption and hybrid infrastructure strategy across enterprise and channel ecosystems."
    },
    {
      icon: "🤖",
      title: "AI-Powered Innovation",
      text: "Championing Microsoft Copilot and AI-driven solutions to unlock measurable business value."
    },
    {
      icon: "🎓",
      title: "Training & Enablement",
      text: "As a Microsoft Certified Trainer, delivering hands-on sessions on Windows Server, Azure Stack HCI, and Modern Workplace."
    },
    {
      icon: "🤝",
      title: "Partner & Channel Strategy",
      text: "Building GTM strategy for Large Device Partners like Dell, HPE, and Lenovo, plus distributors and channel partners."
    },
    {
      icon: "📈",
      title: "Revenue & Growth",
      text: "A proven track record of increasing partner success rates, operational efficiency, and revenue growth."
    },
    {
      icon: "🧭",
      title: "Techno-Commercial Leadership",
      text: "Bridging technology and business value to help organizations navigate the evolving digital landscape."
    }
  ];

  const journey = [
    {
      title: "Regional Sales Leadership",
      text: "Drove sales goals across India and EMEA, building the foundation in Microsoft technologies and enterprise IT."
    },
    {
      title: "Microsoft Certified Trainer",
      text: "Began delivering hands-on training on Windows Server, Azure Stack HCI, Modern Workplace, and Copilot — focused on practical, real-world implementation."
    },
    {
      title: "Techno Commercial Specialist",
      text: "Now leading Go-to-Market strategy for Large Device Partners (Dell, HPE, Lenovo) and Microsoft distributors and channel partners across India, SEA, and EMEA."
    },
    {
      title: "Driving What's Next",
      text: "Focused on bridging technology and business value — helping organizations build sustainable IT ecosystems for long-term success."
    }
  ];
</script>

<div class="text-gray-900 overflow-hidden">

  <!-- --- Hero --- -->
  <section class="relative flex flex-col items-center justify-center text-center px-6 min-h-[70vh] overflow-hidden">

    <!-- Layered animated background -->
    <div class="absolute inset-0 bg-gradient-to-br from-[#0a1a4a] via-[#3a1a3a] to-[#6a1b1b] bg-[length:200%_200%] animate-gradient-pan"></div>
    <div class="absolute -top-32 -left-24 w-96 h-96 bg-blue-500/20 rounded-full blur-3xl animate-blob-float"></div>
    <div class="absolute -bottom-32 -right-24 w-96 h-96 bg-red-500/20 rounded-full blur-3xl animate-blob-float-delayed"></div>
    <div class="absolute inset-0 opacity-[0.07]" style="background-image: radial-gradient(circle, white 1px, transparent 1px); background-size: 28px 28px;"></div>
    <div class="absolute inset-0 bg-black/10"></div>

    {#if visible}
      <div class="relative z-10 max-w-3xl text-white" in:fly={{ y: 24, duration: 700, easing: cubicInOut }}>
        <span class="inline-block text-sm font-semibold tracking-wide text-white/80 bg-white/10 border border-white/20 backdrop-blur-md px-4 py-1.5 rounded-full mb-6">
          About the Founder
        </span>
        <h1 class="text-4xl md:text-6xl font-bold mb-4 tracking-tight">
          Amarnath Tumbalam
        </h1>
        <div class="w-16 h-1 rounded-full bg-white/50 mx-auto mb-6"></div>
        <p class="text-lg md:text-xl text-gray-200 leading-relaxed px-4 max-w-2xl mx-auto">
          20+ years driving cloud transformation, AI-powered innovation, and strategic
          business development across India, EMEA, and SEA.
        </p>
      </div>
    {/if}
  </section>

  <!-- --- Stats Strip --- -->
  <section class="max-w-6xl mx-auto px-6 -mt-12 relative z-20">
    <div class="grid grid-cols-2 md:grid-cols-4 gap-4 md:gap-6">
      {#each stats as stat, i}
        <div
          class="bg-white rounded-2xl border border-gray-100 shadow-lg p-6 text-center hover:-translate-y-1 hover:shadow-xl transition-all duration-300"
          in:fly={{ y: 20, duration: 500, delay: 150 + i * 100 }}
        >
          <div class="text-3xl font-bold text-[#0a1a4a] mb-1">{stat.value}</div>
          <div class="text-sm text-gray-500 leading-snug">{stat.label}</div>
        </div>
      {/each}
    </div>
  </section>

  <!-- --- Bio Section --- -->
  <section class="max-w-4xl mx-auto py-20 px-6">
    <div class="space-y-6 text-gray-700 leading-relaxed text-lg">
      <p in:fade={{ duration: 600, delay: 100 }}>
        With over 20 years of extensive experience in the IT industry and deep expertise in
        Microsoft technologies, Amarnath Tumbalam has cultivated a strong foundation in driving
        cloud transformation, AI-powered innovation, and strategic business development across
        India, EMEA, and SEA. Amarnath's career spans leadership roles that have enabled
        organizations to embrace cutting-edge technologies, optimize IT operations, and achieve
        measurable business outcomes.
      </p>
      <p in:fade={{ duration: 600, delay: 200 }}>
        As a Microsoft Certified Trainer (MCT), Amarnath takes pride in empowering teams and
        organizations to unlock the potential of emerging tools, such as Windows Server, Azure
        Stack HCI, Modern Workplace, Microsoft Copilot, and AI-driven solutions. Training sessions
        focus on practical implementation, ensuring users and businesses fully realize the value
        of technology adoption.
      </p>
      <p in:fade={{ duration: 600, delay: 300 }}>
        Throughout Amarnath's career, initiatives have resulted in significant achievements,
        including a proven track record of increasing partner success rates, improving
        operational efficiency, and driving revenue growth. By collaborating with strategic
        partners and leveraging advanced tools, Amarnath has consistently delivered solutions
        that align technology with business goals.
      </p>
      <p in:fade={{ duration: 600, delay: 400 }}>
        Amarnath has successfully driven sales goals across India and EMEA earlier in their
        career. Now, as a Techno Commercial Specialist, Amarnath is driving the Go-to-Market
        (GTM) strategy for Large Device Partners (LDPs) like Dell, HPE, Lenovo, as well as
        Microsoft Distributors and Channel Partners across India, SEA, and EMEA. Efforts have
        been pivotal in launching new products and surpassing sales targets, ensuring that
        partners achieve their goals.
      </p>
      <p in:fade={{ duration: 600, delay: 500 }}>
        Passionate about fostering innovation and building sustainable IT ecosystems, Amarnath is
        committed to bridging the gap between technology and business value, helping
        organizations navigate the evolving digital landscape to achieve long-term success.
      </p>
    </div>
  </section>

  <!-- --- Areas of Expertise --- -->
  <section class="max-w-7xl mx-auto py-16 px-6">
    <div class="text-center max-w-3xl mx-auto mb-14">
      <span class="inline-block text-sm font-semibold tracking-wide text-[#6a1b1b] bg-red-50 px-4 py-1.5 rounded-full mb-4">
        Areas of Expertise
      </span>
      <h3 class="text-3xl md:text-4xl font-semibold text-[#0a1a4a]">Where Amarnath Delivers Value</h3>
    </div>

    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
      {#each expertise as block, i}
        <div
          class="group relative rounded-3xl bg-white p-8 border border-gray-100 shadow-sm
                 hover:shadow-2xl hover:-translate-y-2 transition-all duration-500 ease-out overflow-hidden"
          in:fly={{ y: 30, duration: 500, delay: 100 * i }}
        >
          <div class="absolute inset-0 rounded-3xl bg-gradient-to-br from-[#0a1a4a] to-[#6a1b1b]
                      opacity-0 group-hover:opacity-100 transition-opacity duration-500 -z-10 blur-xl scale-95 group-hover:scale-100"></div>
          <div class="absolute inset-[1px] rounded-3xl bg-white -z-10"></div>

          <div class="w-14 h-14 flex items-center justify-center rounded-2xl bg-gradient-to-br from-[#0a1a4a]/10 to-[#6a1b1b]/10
                      text-3xl mb-6 transition-all duration-500 group-hover:scale-110 group-hover:rotate-6
                      group-hover:from-[#0a1a4a] group-hover:to-[#6a1b1b]">
            {block.icon}
          </div>

          <h4 class="text-xl font-semibold text-[#0a1a4a] mb-3 transition-colors duration-300 group-hover:text-[#6a1b1b]">
            {block.title}
          </h4>
          <p class="text-sm text-gray-600 leading-relaxed">{block.text}</p>
        </div>
      {/each}
    </div>
  </section>

  <!-- --- Career Journey Timeline --- -->
  <section class="max-w-4xl mx-auto py-16 px-6">
    <div class="text-center mb-14">
      <h3 class="text-3xl md:text-4xl font-semibold text-[#0a1a4a] mb-4">The Journey</h3>
      <p class="text-gray-600">From regional sales leadership to global GTM strategy.</p>
    </div>

    <div class="relative pl-8 md:pl-10">
      <div class="absolute left-[9px] md:left-[13px] top-2 bottom-2 w-0.5 bg-gradient-to-b from-[#0a1a4a] via-gray-300 to-[#6a1b1b]"></div>

      {#each journey as step, i}
        <div
          class="relative pb-12 last:pb-0"
          in:fly={{ x: -20, duration: 500, delay: 100 * i }}
        >
          <span class="absolute -left-8 md:-left-10 top-1 w-5 h-5 rounded-full bg-white border-4 border-[#0a1a4a] shadow"></span>
          <h4 class="text-lg font-semibold text-[#0a1a4a] mb-1.5">{step.title}</h4>
          <p class="text-gray-600 leading-relaxed text-sm md:text-base">{step.text}</p>
        </div>
      {/each}
    </div>
  </section>

  <!-- --- Closing CTA --- -->
  <section class="max-w-6xl mx-auto py-16 px-6">
    <div class="relative rounded-3xl bg-gradient-to-r from-[#0a1a4a] to-[#6a1b1b] text-white px-8 py-16 shadow-lg overflow-hidden text-center">
      <div class="relative z-10 max-w-2xl mx-auto">
        <h3 class="text-3xl md:text-4xl font-semibold mb-4">Let's Build What's Next</h3>
        <p class="text-lg text-gray-200 leading-relaxed mb-8">
          Bridging technology and business value to help your organization navigate the
          evolving digital landscape.
        </p>
        <a href="/contact" class="inline-block rounded-xl bg-white text-[#0a1a4a] font-semibold px-8 py-4 shadow-lg hover:bg-gray-100 transition-all">
          Get in Touch
        </a>
      </div>
      <div class="absolute inset-0 bg-gradient-to-tr from-white/5 to-transparent"></div>
    </div>
  </section>
</div>

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
</style>