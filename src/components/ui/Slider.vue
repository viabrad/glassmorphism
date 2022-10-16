<script setup>
import { ref, watch } from 'vue';
import BaseButton from './BaseButton.vue'
import Modal from './Modal.vue'

const blur = ref(10);
const opacity = ref(0.5);
const borderOpacity = ref(0.5);
const copiedtoClipboard = ref(false);
const btnLabel = ref('Copy to Clipboard!');
const boxShadow = ref('0 4px 30px rgba(255, 255, 255, 0.5)')
const hexColor = ref('#ffffff');
const rgbColor = ref([255, 255, 255]);

watch(hexColor, function () {
  const hexCode = document.getElementById('color').value;
  const r = parseInt(hexCode.substr(1, 2), 16)
  const g = parseInt(hexCode.substr(3, 2), 16)
  const b = parseInt(hexCode.substr(5, 2), 16)
  const array = [r, g, b]
  // console.log(`red: ${r}, green: ${g}, blue: ${b}`)
  console.log(array.join(' , '));
  rgbColor.value = array
});

function copyToClipboard() {
  const cssValues = document.getElementById('clipboard');
  navigator.clipboard.writeText(cssValues.value.replace(/ +/g, "  "));
  copiedtoClipboard.value = true;
  setTimeout(function () {
    copiedtoClipboard.value = false;
  }, 2000);
}
</script>

<template>
  <div class="container">
    <div class="card-display">
      <h1>Glass Card</h1>
      <div :style="{
        backgroundColor: 'rgba(' + rgbColor + ',' + opacity + ')',
        borderRadius: 16 + 'px',
        width: 500 + 'px',
        maxWidth: 90 + '%',
        height: 200 + 'px',
        backdropFilter: 'blur(' + blur + 'px)',
        border: 1 + 'px solid rgba(' + rgbColor + ',' + borderOpacity + ')',
        boxShadow: boxShadow,
      }">
      </div>
    </div>
    <div class="card-editor">
      <transition>
        <modal v-show="copiedtoClipboard"></modal>
      </transition>
      <div class="settings">
        <h2>Blur</h2>
        <input v-model="blur" type="range" min="0" max="20" step="0.1" class="slider" id="blur" />
        <h2>Transparency</h2>
        <input v-model="opacity" type="range" min="0" max="1" step="0.01" class="slider" id="opacity" />
        <h2> Border Transparency</h2>
        <input v-model="borderOpacity" type="range" min="0" max="1" step="0.01" class="slider" id="border" />
        <h2>Color</h2>
        <input v-model="hexColor" type="color" id="color" />
      </div>
      <div class="css">
        <h2>CSS</h2>
        <div class="text-container">
          <textarea name="text" id="clipboard" disabled spellcheck="false">/*hex color code: {{ hexColor }}*/
            background-color: rgba({{rgbColor[0]}}, {{rgbColor[1]}}, {{rgbColor[2]}}, {{opacity}});
            border-radius: 16px;
            border: 1px solid rgba({{rgbColor[0]}}, {{rgbColor[1]}}, {{rgbColor[2]}}, {{borderOpacity}});
            backdrop-filter: blur({{ blur }}px);
            -webkit-backdrop-filter: blur({{ blur }}px);
          </textarea>
        </div>
        <BaseButton @click="copyToClipboard">{{ btnLabel }}</BaseButton>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1 {
  color: white;
  font-size: clamp(2rem, 10vw, 8rem);
  position: absolute;
}

h2 {
  font-size: clamp(1rem, 1vw, 2rem);
}

textarea {
  font-family: inherit;
  font-size: clamp(1rem, 2vw, 1rem);
  color: white;
  background: transparent;
  resize: none;
  white-space: pre-line;
  width: 100%;
  height: 11rem;
  border: 0;
  border-radius: 16px;
  padding-bottom: 0px;
}


.css {
  display: flex;
  flex-direction: column;
  width: 90%;
  margin: auto;
}

.card-editor {
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 500px;
  max-width: 90%;
  padding: 2rem 0;
  height: fit-content;
  background-color: rgba(255, 255, 255, 0.24);
  border-radius: 16px;
  backdrop-filter: blur(5.4px);
  -webkit-backdrop-filter: blur(5.4px);
  border: 1px solid rgba(255, 255, 255, 0.48);
  box-shadow: 0 4px 30px rgba(255, 255, 255, 0.5);
}


.container {
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
}

.card-display {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.settings {
  display: flex;
  flex-direction: column;
  margin: auto;
  width: 90%;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>




/*hex  color  code:  #ffffff*/
background-color:  rgba(255,  255,  255,  0.02);
border-radius:  16px;
border:  1px  solid  rgba(255,  255,  255,  0);
backdrop-filter:  blur(18px);
-webkit-backdrop-filter:  blur(18px);

