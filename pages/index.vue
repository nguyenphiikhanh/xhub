<template>
  <div class="w-full mt-5 px-3 bg-transparent">
    <h3 class="text-2xl lg:text-3xl text-white font-extrabold mb-2">
      Best Sellers
    </h3>
    <div class="grid grid-cols-1 md:grid-cols-3 lg:grid-cols-5 gap-4 mb-5">
      <template v-for="i in 15">
        <div class="">
          <div class="bg-gray-900 rounded-lg m-h-64 p-2 transform hover:scale-100 hover:shadow-xl transition duration-300 cursor-pointer">
            <div class="mb-2 hover:scale-50">
              <img class="h-64 mx-auto object-fill" src="https://srv-cdn.onedio.com/store/988bccbdb9ca395f581f98faa9ce3a55123f12bfcef608c838532b813646e557.png" alt="" />
            </div>
            <div class="rounded-lg p-4 bg-gray-700 flex flex-col">
              <div class="">
                <p class="text-white text-md text-left md:text-center font-bold leading-none hover:text-orange-600 md:hidden">
                  iPhone XR AI-Generated Tailwind Cards overflow-ellipsis
                </p>
                <p class="text-white text-md text-left md:text-center font-bold leading-none hover:text-orange-600 hidden md:block">
                  iPhone XR AI-Generated Tailwind Cards overflow-ellipsis
                </p>
              </div>
            </div>
          </div>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>

</style>
