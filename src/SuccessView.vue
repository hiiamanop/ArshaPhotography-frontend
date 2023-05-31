<template>
    <div id="SuksesView">
      <HeaderComp />
      <SuksesKonten />
      <FooterComp />
    </div>
  </template>
  
  <script>
  import HeaderComp from "@/sections/HeaderComp.vue";
  import SuksesKonten from "@/sections/SuccessSection.vue";
  import FooterComp from "@/sections/FooterComp.vue";
  export default {
    name: "SuksesView",
    components: { HeaderComp, SuksesKonten, FooterComp },
  };
  </script>
  
  <style>
  </style>