<script setup>
import { ref, computed, watch, onMounted, onBeforeMount } from 'vue'

const count = ref(0);
const inputText = ref('');
const isAwesome = ref(true);
const isClicked = ref(false);
const items = ref(['apple', 'banana', 'orange', 'mango','semangka']);
const inputLength = computed(() => inputText.value.length);
const inputElement = ref(null);
function increment() {
  count.value++;
}
function changeCalor(){
  isClicked.value = !isClicked.value;


}
function toggleAwesome() {
  isAwesome.value = !isAwesome.value;

}

watch(inputText, (newValue, oldValue) => {
  console.log('Input text berubah dari "${oldValue}"menjadi"${newValue}"');
});

onMounted(() => {
  console.log('Komponen telah dipasang ke dom');
  inputElement.value.focus();

});

onBeforeMount (() => {
  console.log('komponen akan dihancurkan');

});
</script>


<template>
<h1>count: {{ count }}</h1>
<button @click="increment">Tambah Count</button>

<input v-model="inputText" placeholder ="type something" />
<p> You typed: {{ inputText }}</p>
<p> Panjang input: {{ inputLength }}</p>

<h2> Fruits List</h2>
<ul>
  <li v-for="(item, index) in items" :key="index">{{ item }}</li>
</ul>


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