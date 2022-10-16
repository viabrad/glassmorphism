<script setup>
import Slider from './components/ui/Slider.vue';
</script>

<template>
  <section>
    <Slider></Slider>
    <div>
      <a href="https://twitter.com/viabrad" target="_blank" rel="noreferrer noopener">@viabrad</a>
    </div>

  </section>
</template>

<style scoped>
section {
  width: 100%;
}

div {
  display: flex;
  flex-direction: column;
  margin: auto;
  justify-content: center;
  align-items: center;
  width: 100%;
}

a {
  position: fixed;
  bottom: 10px;
  text-decoration: none;
  color: inherit
}

a:visited {
  color: inherit;
}

a:hover {
  color: rgba(255, 255, 255, 0.24);
  transition: 0.4s ease all;
  text-shadow: 0 4px 30px rgba(255, 255, 255, 0.5);
}
</style>

