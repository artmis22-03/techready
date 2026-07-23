<script>
// @ts-nocheck

  import { fade, slide } from "svelte/transition";

  let menuOpen = false;
  let megaOpen = false;
  let active = "Implementation";

  const capabilities = [
    "Implementation",
    "Migration",
    "Project Rescue",
    "Support Services",
    "Corporate Training",
    "Partner Services"
  ];

  const details = {
    Implementation: [
      {
        title: "CRM",
        desc: "Empower relationships with strategy, not guesswork."
      },
      {
        title: "ERP",
        desc: "Attain clarity, control, and confidence in every process."
      }
    ],
    Migration: [
      {
        title: "Cloud Migration",
        desc: "Seamless and secure system transitions."
      }
    ],
    "Project Rescue": [
      {
        title: "Recovery",
        desc: "Fix failing implementations efficiently."
      }
    ],
    "Support Services": [
      {
        title: "Managed Support",
        desc: "Enterprise-grade operational support."
      }
    ],
    "Corporate Training": [
      {
        title: "Enablement",
        desc: "Upskill teams with expert-led training."
      }
    ],
    "Partner Services": [
      {
        title: "Alliances",
        desc: "Certified solution partnerships."
      }
    ]
  };
</script>

<header class="fixed top-0 left-0 w-full z-50 bg-white/90 backdrop-blur shadow-sm">
  <div class="max-w-7xl mx-auto flex items-center justify-between px-6 py-4">

    <!-- Logo -->
    <div class="font-bold text-xl text-blue-900">
      TechReady Solutions
    </div>

    <!-- Desktop Navigation -->
    <nav class="hidden md:flex items-center gap-8">

      <a href="/" class="font-medium hover:text-blue-700">Home</a>

      
      <!-- CAPABILITIES MEGA MENU -->
      <!-- svelte-ignore a11y_no_static_element_interactions -->
      <div
        class="relative"
        on:mouseenter={() => megaOpen = true}
        on:mouseleave={() => megaOpen = false}
      >

        <!-- Trigger -->
        <button
          class="font-medium flex items-center gap-1 hover:text-blue-700"
          aria-haspopup="true"
        >
          Capabilities
          <span
            class="transition-transform duration-200"
            class:rotate-180={megaOpen}
          >
            ⌄
          </span>
        </button>

        <!-- Hover bridge (critical) -->
        <div class="absolute left-0 top-full h-6 w-full"></div>

        <!-- Mega Menu -->
        <div
          class={`absolute left-0 top-full pt-6 w-[900px]
            transition-all duration-200 ease-out
            ${megaOpen
              ? "opacity-100 visible translate-y-0"
              : "opacity-0 invisible -translate-y-1"}`}
        >
          <div class="bg-white rounded-xl shadow-xl p-8">

            <div class="grid grid-cols-3 gap-8">

              <!-- LEFT COLUMN (LINKS) -->
              <div>
                <p class="text-xs uppercase tracking-wide text-gray-400 mb-4">
                  Our Capabilities
                </p>

                {#each capabilities as item}
                  <a
                    href={`/capabilities/${item.toLowerCase().replaceAll(" ", "-")}`}
                    on:mouseenter={() => active = item}
                    class={`block px-4 py-3 rounded-lg flex justify-between items-center
                      transition-colors
                      ${active === item
                        ? "bg-blue-50 text-blue-700"
                        : "hover:bg-gray-50"}`}
                  >
                    <span>{item}</span>
                    <span class="opacity-60">→</span>
                  </a>
                {/each}
              </div>

              <!-- RIGHT PANEL -->
              <div class="col-span-2">
                <div class="space-y-6">
                  {#each details[active] as block}
                    <div>
                      <h3 class="font-semibold text-gray-900">
                        {block.title}
                      </h3>
                      <p class="text-sm text-gray-500">
                        {block.desc}
                      </p>
                    </div>
                  {/each}
                </div>
              </div>

            </div>

          </div>
        </div>
      </div>



      <a href="#technologies" class="font-medium hover:text-blue-700">
        Technologies
      </a>
      <a href="#industries" class="font-medium hover:text-blue-700">
        Industries
      </a>
      <a href="#resources" class="font-medium hover:text-blue-700">
        Resources
      </a>
      <a href="/contact" class="font-medium hover:text-blue-700">
        Contact
      </a>
    </nav>

    <!-- Mobile Toggle -->
    <!-- svelte-ignore a11y_consider_explicit_label -->
    <button
      class="md:hidden text-gray-700"
      on:click={() => menuOpen = !menuOpen}
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none"
        viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d={menuOpen
            ? "M6 18L18 6M6 6l12 12"
            : "M4 6h16M4 12h16M4 18h16"}
        />
      </svg>
    </button>
  </div>

  <!-- Mobile Navigation -->
  {#if menuOpen}
  <div
    class="md:hidden bg-white border-t"
    transition:slide={{ duration: 250 }}
  >
    <a href="/" class="block px-4 py-3 hover:bg-gray-100">Home</a>

    <!-- Mobile Capabilities -->
    <details class="px-4 py-2">
      <summary class="font-medium cursor-pointer">
        Capabilities
      </summary>
      <div class="mt-2 space-y-2 pl-4 text-sm text-gray-600">
        {#each capabilities as item}
          <div>{item}</div>
        {/each}
      </div>
    </details>

    <a href="#technologies" class="block px-4 py-3 hover:bg-gray-100">
      Technologies
    </a>
    <a href="#industries" class="block px-4 py-3 hover:bg-gray-100">
      Industries
    </a>
    <a href="/contact" class="block px-4 py-3 hover:bg-gray-100">
      Contact
    </a>
  </div>
  {/if}
</header>
