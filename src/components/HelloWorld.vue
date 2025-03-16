<script setup>
import { ref } from 'vue'

const count = ref(0);
const inputText = ref('');
const isAwesome = ref(true);
const isClicked = ref(false);
function increment() {
  count.value++;
}
function changeCalor(){
  isClicked.value = !isClicked.value;


}
function toggleAwesome() {
  isAwesome.value = !isAwesome.value;

}
</script>


<template>
<h1>count: {{ count }}</h1>
<button @click="increment">Tambah Count</button>

<input v-model="inputText" placeholder ="type something" />
<p> You typed: {{ inputText }}</p>

<h1 :class="isClicked ? 'tittle-clicked' : 'tittle'">make me red or blue</h1>
<button @click="changeCalor">change calor</button>

<button @click="toggleAwesome">Toggle</button>
<h1 v-if="isAwesome"> vue is awesome!</h1>
<h1 v-else>oh no</h1>

</template>

<style>
.tittle {
  color :red
}
.tittle.clicked {
  color :blue
}
</style>
