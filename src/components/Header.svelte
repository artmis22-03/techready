<script>
  let isOpen = false;
</script>
<header class="sticky top-0 z-5 bg-white shadow-md">
<div class="min-h-16 bg-gray-100">
  <!-- Navbar -->
  <nav class="bg-white shadow">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-16">
        <div class="flex">
          <div class="flex-shrink-0 flex items-center text-2xl font-bold text-blue-600">
            TechReady
          </div>
          <!-- Desktop Menu -->
          <div class="hidden md:flex md:items-center md:space-x-8 ml-10">
            <a href="#" class="text-gray-700 hover:text-blue-600 px-3 py-2 rounded-md">Home</a>
            <a href="#" class="text-gray-700 hover:text-blue-600 px-3 py-2 rounded-md">About</a>
            <div class="relative group">
              <button class="inline-flex items-center px-2 py-3 text-gray-700 hover:text-blue-600">
                Services
                <svg class="ml-1 w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M19 9l-7 7-7-7"></path>
                </svg>
              </button>
              <div
                class="absolute z-40 w-48 bg-white border border-gray-200 rounded shadow-lg opacity-0 group-hover:opacity-100 group-hover:visible invisible transition-opacity duration-200"
              >
                <a href="#" class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Implementations</a>
                <a href="#" class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Migrations</a>
                <a href="#" class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Tenant-to-Tenant Migrations</a>
                <a href="#" class="block px-4 py-2 text-gray-800 hover:bg-gray-100">VMware to Microsoft</a>
                <a href="#" class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Legacy Applications</a>
                <a href="#" class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Corporate Training</a>
              </div>
            </div>
            <a href="#" class="text-gray-700 hover:text-blue-600 px-3 py-2 rounded-md">Products</a>
            <a href="#" class="text-gray-700 hover:text-blue-600 px-3 py-2 rounded-md">FAQ's</a>
          </div>
        </div>

        <!-- Mobile menu button -->
        <div class="md:hidden flex items-center">
          <button on:click={() => isOpen = !isOpen} class="text-gray-700 hover:text-blue-600 focus:outline-none">

            <svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              {#if isOpen}
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M6 18L18 6M6 6l12 12" />
              {:else}
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16" />
              {/if}
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Menu -->
    {#if isOpen}
    <div class="md:hidden bg-white border-t border-gray-200">
      <a href="#" class="block px-4 py-2 text-gray-700 hover:bg-gray-100">Home</a>
      <a href="#" class="block px-4 py-2 text-gray-700 hover:bg-gray-100">About</a>
      <div class="block">
        <span class="block px-4 py-2 text-gray-700 font-semibold">Services</span>
        <a href="#" class="block px-6 py-2 text-gray-700 hover:bg-gray-100">Web Development</a>
        <a href="#" class="block px-6 py-2 text-gray-700 hover:bg-gray-100">App Development</a>
        <a href="#" class="block px-6 py-2 text-gray-700 hover:bg-gray-100">Consulting</a>
      </div>
      <a href="#" class="block px-4 py-2 text-gray-700 hover:bg-gray-100">Products</a>
      <a href="#" class="block px-4 py-2 text-gray-700 hover:bg-gray-100">FAQ's</a>
    </div>
    {/if}
  </nav>

  
</div>
</header>