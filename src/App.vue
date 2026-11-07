<template>
  <div id="app">
    <Nav />
    <router-view />

    <ChatBot/>
  </div>
</template>

<script>
import Nav from "./components/nav.vue";
import ChatBot from "./components/features/chatbot.vue";
import { onMounted } from "vue";
import AOS from "aos";

export default {
  components: {
    Nav,
    ChatBot,
  },
  data() {
    return {
      isScrollDown: false,
    };
  },
  mounted() {
    Zoomtastic.mount({
      size: '95%',
      easing: 'ease',
      duration: 300,
      background: 'rgba(0, 0, 0, 0.9)',
      filter: 'drop-shadow(0 2px 16px rgba(0, 0, 0, 0.3))',
      animation: 'slide'
    });

    Zoomtastic.listen('[zoomtastic]', 'src');

    AOS.init({
      duration: 700,
      easing: 'ease-out-cubic',
      offset: 80,
      once: true,
      disable: window.matchMedia('(prefers-reduced-motion: reduce)').matches,
    });
  },
};
</script>

<style lang="scss">
/* Only the viewport scrolls. "clip" trims sideways overflow without making
   the element a second vertical scroll container, as "hidden" would. */
html {
  overflow-x: hidden;
}

body, #app {
  overflow-x: clip;
  width: 100%;
}

:root {
  --color-primary: #17967F;
  --color-primary-rgb: 23, 150, 127;
  --color-secondary: #D76436;
  --color-secondary-rgb: 215, 100, 54;
}

[id] {
  scroll-margin-top: 76px;
}

* { 
  margin: 0;
  padding: 0;
  font-family: "Segoe UI", Tahoma;
  transition: width 1s ease, height 1s ease, background-color 1s ease;
  box-sizing: border-box;
}
::-webkit-scrollbar {
  width: 15px;
  background: transparent;
}
::-webkit-scrollbar-track {
  background: transparent;
}
::-webkit-scrollbar-thumb {
  background: #888; 
  border-radius: 10px;
}




</style>
