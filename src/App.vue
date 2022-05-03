<!--<script>
//import TicTacToe from "./components/TicTacToe.vue";
//import TicTacToe_newLogic from "./components/TicTacToe_newLogic.vue"
import myCRUD from "./components/myCRUD.vue"

export default {
  name: "App",
  components: {
    //TicTacToe,
    //TicTacToe_newLogic,
    myCRUD,
  },
};
</script>

<template>
  <myCRUD msg="Hello We are going to see Vue 3 + Vite application for the basic CRUD applications" />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
-->

<!--<script>
//import TicTacToe from "./components/TicTacToe.vue";
//import TicTacToe_newLogic from "./components/TicTacToe_newLogic.vue"
//</script>-->

<script setup>
import { ref, reactive, computed, watch } from 'vue'

const names = reactive(['Rachana, Oza', 'Chandni, Trivedi', 'Deven, Dave'])
const selected = ref('')
const prefix = ref('')
const first = ref('')
const last = ref('')

const filteredNames = computed(() =>
  names.filter((n) =>
    n.toLowerCase().startsWith(prefix.value.toLowerCase())
  ) 
)

watch(selected, (name) => {
  ;[first.value, last.value] = name.split(', ')
})

function create() {
  if (hasValidInput()) {
    const fullName = `${first.value}, ${last.value}`
    if (!names.includes(fullName)) {
      names.push(fullName)
      first.value = last.value = ''
    }
  }
}

function update() {
  if (hasValidInput() && selected.value) {
    const i = names.indexOf(selected.value)
    names[i] = selected.value = `${first.value}, ${last.value}`
  }
}

function del() {
  if (selected.value) {
    const i = names.indexOf(selected.value)
    names.splice(i, 1)
    selected.value = first.value = last.value = ''
  }
}

function hasValidInput() {
  return first.value.trim() && last.value.trim()
}
</script>

<template>
    <body>
        <div>
            <input v-model="prefix" placeholder="Filter prefix">
        </div>
        <select size="5" v-model="selected">
            <option v-for-key="name in filteredNames">{{ name }}</option>
        </select>
        <label>Name: <input v-model="first"></label>
        <label>Surname: <input v-model="last"></label>
        <div class="buttons">
            <button @click="create">Create</button>
            <button @click="update">Update</button>
            <button @click="del">Delete</button>
        </div>
    </body>
</template>

<style>
* {
  font-size: inherit;
}

input {
  display: block;
  margin-bottom: 10px;
}
v
select {
  float: left;
  margin: 0 1em 1em 0;
  width: 14em;
}

.buttons {
  clear: both;
}

button + button {
  margin-left: 5px;
}
</style>


