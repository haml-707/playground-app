<script setup>
import { ref } from "vue";
import mitt from "@/shared/mitt";

import { PLAYGROUND_PAGES } from "@/pages/playground/shared";

import AppHeader from "@/components/AppHeader.vue";
import AppFooter from "@/components/AppFooter.vue";

import bg from "@/assets/bg/home-bg-nav.png";

const showFooter = ref(true);

mitt.on(PLAYGROUND_PAGES.SET_FOOTER, (val) => {
  showFooter.value = val;
});
</script>

<template>
  <header class="app-header" :style="{ backgroundImage: `url(${bg})` }">
    <app-header></app-header>
  </header>

  <main class="app-body">
    <router-view></router-view>
  </main>
  <div class="app-dialogs"></div>

  <footer v-if="showFooter" class="app-footer">
    <app-footer></app-footer>
  </footer>
</template>

<style lang="scss" scoped>
.app-header {
  position: relative;
  z-index: 2;
  height: 80px;
  background-color: #002fa7;
  background-size: 100% 100%;
  background-position: center;
  background-repeat: no-repeat;
  @media screen and (max-width: 1023px) {
    // height: 60px;
  }
}
.app-body {
  position: relative;
  z-index: 1;
  // min-height: calc(100vh - 80px);
}
.app-dialogs {
  position: relative;
  z-index: 100;
}

.app-footer {
  background: #191a20;
}
</style>
