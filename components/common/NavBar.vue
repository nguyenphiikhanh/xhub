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
        <ul class="flex space-x-8 text-md font-sans font-semibold">
          <li><a href="#" class="border-b-4 border-orange-600 pb-1">Home</a></li>
          <li><a href="#" class="hover:border-b-4 hover:border-orange-600">Services</a></li>
          <li><a href="#" class="hover:border-b-4 hover:border-orange-600">Features</a></li>
          <li><a href="#" class="hover:border-b-4 hover:border-orange-600">FAQ</a></li>
          <li><a href="#" class="hover:border-b-4 hover:border-orange-600">Contact</a></li>
          <li><a href="#" class="cta bg-blue-500 hover:bg-blue-600 px-3 py-2 rounded text-white font-semibold">Sign Up</a></li>
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

        <ul class="divide-y font-sans">
          <li><a href="#" @click="isOpen = false" class="my-4 inline-block">Home</a></li>
          <li><a href="#" @click="isOpen = false" class="my-4 inline-block">Services</a></li>
          <li><a href="#" @click="isOpen = false" class="my-4 inline-block">Features</a></li>
          <li><a href="#" @click="isOpen = false" class="my-4 inline-block">FAQ</a></li>
          <li><a href="#" @click="isOpen = false" class="my-4 inline-block">Contact</a></li>
          <li><a href="#" @click="isOpen = false" class="my-8 w-full text-center font-semibold cta inline-block bg-blue-500 hover:bg-blue-600 px-3 py-2 rounded text-white">Sign Up</a></li>
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
