<script setup lang="ts">
import { ref } from 'vue'
import { computed } from 'vue'


const variable1 = ref<number>(2);
const count = ref<number>(0)
const countTimesVariable = computed<number>(() => {
    return count.value * variable1.value
})
const countPowerOfVariable = computed<number>(() => {
    return count.value ** variable1.value
})
const countDividedByVariable = computed<number | string>(() => {
  if (variable1.value == 0) return 'Not defined (/0)'
    return count.value / variable1.value
})
const countPlusVariable = computed<number>(() => {
    return count.value + variable1.value
})
</script>

<template>
  <h1>Counter / Calculator</h1>
  <div class="grid-2">
    <div class="card">
      <p> Count: <strong>{{ count }} </strong> </p>
      <div>
        <button class="btn-danger" title="-" @click="count--" >-</button>
        <button class="btn-success" title="+" @click="count++" >+</button>
      </div>
    </div>
    <div class="card">
      <p> Variable: <strong>{{ variable1 }} </strong> </p>
      <div>
        <button class="btn-danger" title="-" @click="variable1--" >-</button>
        <button class="btn-success" title="+" @click="variable1++" >+</button>
      </div>
    </div>
  </div>
  <div class="grid-1">
    <span class="card">{{ count }} + {{ variable1 }} = {{ countPlusVariable }}</span>
    <span class="card">{{ count }} * {{ variable1 }} = {{ countTimesVariable }}</span>
    <span class="card">{{ count }} ^ {{ variable1 }} = {{ countPowerOfVariable }}</span>
    <span class="card">{{ count }} / {{ variable1 }} = {{ countDividedByVariable }}</span>
  </div>
</template>

<style scoped>

.grid-1 {
  display: grid;
  margin: 1.5rem;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.5rem;
}
.grid-2 {
  display: grid;
  margin: 1.5rem;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
}
.card {
  background-color: #f3f3f3;
  color: #000;
  padding: 1rem;
  border-radius: 0.5rem;
}

/* From Uiverse.io by absoluteSTrange */
button {
  --btn-bg: rgb(255, 56, 86);
  --btn-shadow: rgb(201, 46, 70);
  --btn-text: hsl(0, 0%, 100%);

  padding: .75em 1.5em;
  margin: .5em;
  border-radius: 0.67em;
  border: 0;
  background-color: var(--btn-bg);
  letter-spacing: 0.1em;
  font-size: .8rem;
  transition: all 0.3s ease;
  box-shadow: 0 0.67em 0 0 var(--btn-shadow);
  color: var(--btn-text);
  cursor: pointer;
}

button:hover {
  box-shadow: 0 0.47em 0 0 var(--btn-shadow);
}

button:active {
  background-color: var(--btn-bg);
  box-shadow: 0 0 0 0 var(--btn-shadow);
  transform: translateY(0.33em);
  transition: 200ms;
}

.btn-danger {
  --btn-bg: rgb(255, 56, 86);
  --btn-shadow: rgb(201, 46, 70);
}

.btn-success {
  --btn-bg: rgb(50, 168, 80);
  --btn-shadow: rgb(38, 128, 61);
}

.btn-primary {
  --btn-bg: rgb(37, 99, 235);
  --btn-shadow: rgb(29, 78, 216);
}

</style>