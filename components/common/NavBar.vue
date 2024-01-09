<template>
  <nav class="w-full p-6 bg-gray-900">
    <div class="flex items-center">

      <!-- Header logo -->
      <div class="md:mr-20">
        <Logo />
      </div>

      <!-- Mobile toggle -->
      <div class="md:hidden ml-auto">
        <button @click="drawer">
          <svg
            class="h-8 w-8 fill-current text-white hover:text-orange-600"
            fill="none" stroke-linecap="round"
            stroke-linejoin="round" stroke-width="2"
            viewBox="0 0 24 24" stroke="currentColor">
              <path d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
        </button>
      </div>

      <!-- Navbar -->
      <div class="hidden md:block">
        <ul class="flex space-x-5 text-xl font-sans font-semibold flex-wrap">
          <li class="hover:text-orange-600"><a href="#">Home</a></li>
          <li class="hover:text-orange-600"><a href="#">Services</a></li>
          <li class="hover:text-orange-600"><a href="#">Features</a></li>
          <li class="hover:text-orange-600"><a href="#">FAQ</a></li>
          <li class="hover:text-orange-600"><a href="#">Contact</a></li>
          <li class="hover:text-orange-600">
              <div class="relative flex items-center text-gray-900">
                  <input type="text"
                          placeholder="Tìm kiếm"
                          class="px-4 border border-gray-300 rounded-full focus:outline-none focus:ring focus:border-blue-300"/>
                  <div class="absolute inset-y-0 right-0 flex items-center pr-3">
                      <svg class="h-5 w-5 text-gray-400"
                           fill="none"
                           stroke="currentColor"
                           viewBox="0 0 24 24"
                           xmlns="http://www.w3.org/2000/svg">
                          <path stroke-linecap="round"
                                  stroke-linejoin="round"
                                  stroke-width="2"
                                  d="M21 21l-5.2-5.2"></path>
                          <circle cx="10" cy="10" r="7"></circle>
                      </svg>
                  </div>
              </div>
          </li>
        </ul>
      </div>

      <!-- Dark Background Transition -->
      <transition
        enter-class="opacity-0"
        enter-active-class="ease-out transition-medium"
        enter-to-class="opacity-100"
        leave-class="opacity-100"
        leave-active-class="ease-out transition-medium"
        leave-to-class="opacity-0"
      >
        <div @keydown.esc="isOpen = false" v-show="isOpen" class="z-10 fixed inset-0 md:hidden transition-opacity">
            <div @click="isOpen = false" class="absolute inset-0 bg-black opacity-50" tabindex="0"></div>
        </div>
      </transition>

      <!-- Drawer Menu -->
      <aside class="p-5 md:hidden transform top-0 left-0 w-64 bg-gray-900 fixed h-full overflow-auto ease-in-out transition-all duration-300 z-30" :class="isOpen ? 'translate-x-0' : '-translate-x-full'">

        <div class="close">
          <button class="absolute top-0 right-0 mt-4 mr-4 hover:text-orange-600" @click=" isOpen = false">
            <svg
              class="w-6 h-6"
              fill="none" stroke-linecap="round"
              stroke-linejoin="round" stroke-width="2"
              viewBox="0 0 24 24" stroke="currentColor">
              <path d="M6 18L18 6M6 6l12 12"></path>
            </svg>
          </button>
        </div>

        <span @click="isOpen = false" class="flex w-full items-center p-4 border-b">
          <Logo />
        </span>
        <ul class="font-sans font-semibold">
            <li>
                <div class="relative my-3 flex items-center justify-start text-gray-900">
                <input type="text"
                       placeholder="Tìm kiếm"
                       class="pl-2 border border-gray-300 rounded-full focus:outline-none focus:ring focus:border-blue-300"/>
                <button class="bg-orange-600 h-full p-1 rounded-md ml-1">
                    <svg class="h-5 w-5 text-white"
                         fill="none"
                         stroke="currentColor"
                         viewBox="0 0 24 24"
                         xmlns="http://www.w3.org/2000/svg">
                        <path stroke-linecap="round"
                              stroke-linejoin="round"
                              stroke-width="2"
                              d="M21 21l-5.2-5.2"></path>
                        <circle cx="10" cy="10" r="7"></circle>
                    </svg>
                </button>
            </div>
            </li>
          <li><a href="#" @click="isOpen = false" class="my-1 inline-block">Home</a></li>
          <li><a href="#" @click="isOpen = false" class="my-1 inline-block">Services</a></li>
          <li><a href="#" @click="isOpen = false" class="my-1 inline-block">Features</a></li>
          <li><a href="#" @click="isOpen = false" class="my-1 inline-block">FAQ</a></li>
          <li><a href="#" @click="isOpen = false" class="my-1 inline-block">Contact</a></li>
        </ul>
      </aside>

    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false
    };
  },
  methods: {
    drawer() {
      this.isOpen = !this.isOpen;
    }
  },
  watch: {
    isOpen: {
      immediate: true,
      handler(isOpen) {
        if (process.client) {
          if (isOpen) document.body.style.setProperty("overflow", "hidden");
          else document.body.style.removeProperty("overflow");
        }
      }
    }
  },
  mounted() {
    document.addEventListener("keydown", e => {
      if (e.keyCode == 27 && this.isOpen) this.isOpen = false;
    });
  }
};
</script>
