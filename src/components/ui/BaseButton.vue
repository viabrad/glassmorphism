<template>
  <button><slot></slot></button>
</template>

<style scoped>
button {
  font-family: inherit;
  width: 100%;
  max-width: 100%;
  height: 3rem;
  background-color: rgba(255, 255, 255, 0.247);
  border-radius: 8px;
  backdrop-filter: blur(7.7px);
  -webkit-backdrop-filter: blur(7.7px);
  border: 1px solid rgba(255, 255, 255, 0.48);
  color: white;
  cursor: pointer;
  margin: auto;
}

button:hover {
  background-color: rgba(0, 0, 0, 0.247);
  transition: 0.4s ease all;
}

</style>


