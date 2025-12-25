<script>
  
  import { slide, fade } from "svelte/transition";
  let menuOpen = false;
</script>


<header class="fixed top-0 left-0 w-full z-50 bg-white/80 backdrop-blur-md shadow-sm">
  <div class="max-w-7xl mx-auto flex items-center justify-between p-4">
    <!-- Logo -->
    <div class="flex items-center gap-2">
      <img src="/" alt="Logo" class="h-10 w-auto" />
      <span class="font-bold text-xl text-blue-900">TechReady Solutions</span>
    </div>

    <!-- Desktop Nav -->
    <nav class="hidden md:flex space-x-6">
      <a href="/" class="hover:text-blue-700 font-medium">Home</a>
      <a href="#services" class="hover:text-blue-700 font-medium">Services</a>
      <a href="#about" class="hover:text-blue-700 font-medium">About</a>
      <a href="/contact" class="hover:text-blue-700 font-medium">Contact</a>
    </nav>

    <!-- Mobile Menu Button -->
    <!-- <button class="md:hidden text-gray-700 focus:outline-none" on:click={() => menuOpen = !menuOpen}>
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none"
        viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
        <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
      </svg>
    </button> -->
    <button 
  class="md:hidden text-gray-700 focus:outline-none transition-transform duration-300"
  on:click={() => menuOpen = !menuOpen}
>
  <svg 
    xmlns="http://www.w3.org/2000/svg"
    class="h-6 w-6 transform transition-transform duration-300"
    viewBox="0 0 24 24" 
    fill="none" 
    stroke="currentColor" 
    stroke-width="2"
  >
    <path 
      stroke-linecap="round" 
      stroke-linejoin="round"
      d={menuOpen 
        ? "M6 18L18 6M6 6l12 12"  // X icon
        : "M4 6h16M4 12h16M4 18h16" // Hamburger
      } 
      class="transition-all duration-300"
    />
  </svg>
</button>

  </div>

  <!-- Mobile Nav -->
  {#if menuOpen}
  <div
    class="md:hidden bg-white border-t border-gray-200"
    transition:slide={{ duration: 250 }}
    
  >
      <a href="/" class="block px-4 py-2 hover:bg-gray-100">Home</a>
      <a href="#services" class="block px-4 py-2 hover:bg-gray-100">Services</a>
      <a href="#about" class="block px-4 py-2 hover:bg-gray-100">About</a>
      <a href="#contact" class="block px-4 py-2 hover:bg-gray-100">Contact</a>
  </div>
{/if}

</header>
