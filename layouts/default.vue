<template>
  <div class="bg-gray-700 text-gray-200 flex flex-col min-h-screen">
    <LeftAds/>
    <div class="w-full md:w-4/5 mx-auto">
        <NavBar/>
        <TopAds/>
        <Nuxt />
    </div>
    <RightAds/>
    <div class="mt-auto w-full md:w-4/5 mx-auto">
        <Footer/>
    </div>
  </div>
</template>

<style>
html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}
</style>
<script>
</script>