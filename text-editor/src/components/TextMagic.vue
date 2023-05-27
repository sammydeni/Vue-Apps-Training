<script setup>
import { reactive, computed } from "vue";

const fontParam = reactive({
  text1: "Testo1",
  size: '',
  color: "",
  isActive: false
});

const finalStyle = computed(() => {
  return `font-size: ${fontParam.size}px;color: ${fontParam.color};`
});



function magic() {
  fontParam.size = 50
  fontParam.color = "white"
  fontParam.isActive = true
  console.log(finalStyle)
}

function reset() {
  fontParam.text1 = "Testo1"
  fontParam.size = ""
  fontParam.color = ""
  fontParam.isActive = false
}
</script>

<template>
  <div class="inputBox">
    <input type="text" name="text" v-model="fontParam.text1">
  </div>
  <div id="box">

    <p :style="finalStyle">{{ fontParam.text1 }}</p>
    <p :class="{ styling: fontParam.isActive}">Test2</p>

    <button @click="magic">Magic</button>
    <button @click="reset">Cleann</button>
  </div>
</template>

<style scoped>
button {
  margin: 0 5px;
}

#box {
  color: red;
}

.styling {
  color: teal;
  font-size: 50px;
}
</style>
