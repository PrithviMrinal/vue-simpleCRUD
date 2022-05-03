<!--<script>
//import TicTacToe from "./components/TicTacToe.vue";
//import TicTacToe_newLogic from "./components/TicTacToe_newLogic.vue"
//</script>

<script setup>
import { ref, reactive, computed, watch } from 'vue'

const names = reactive(['Rachana, Oza', 'Chandni, Trivedi', 'Deven, Dave'])
const selected = ref('')
const prefix = ref('')
const first = ref('')
const last = ref('')
console.log(selected);
console.log(prefix);
console.log(first);
console.log(last);


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
            <option v-for-KEY="name in filteredNames">{{ name }}</option>
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


<!--<template>
    <body style="text-align:center">
        <h1>My first simple CRUD operations with vue + vite applications</h1>
        <form class="main">
            <div>
                <label>Search Prefix to Update and or Delete </label>
                <input v-model="prefix " placeholder="Filter Prefix" alignment="center" v-text="center" text-align="center"/>
            </div>
            <div>
                <select size=10 v-model="selected">
                    <option v-for-key="name in prefix">{{ name }}</option>
                </select>
                <label>First Name </label>
                <input v-model="First" alignment="center" v-text="center" text-align="center"/>
            </div>
            <div>
            <label>Surname </label>
                <input v-model="surname " alignment="center" v-text="center" text-align="center"/>
            </div>
            <div>
                <button @click="Create">Create Record</button>
                <button @click="Update">Update Record</button>
                <button @click="Delete">Delete Record</button>
                <button @click="ClearAll" type="reset" value="reset">ClearAll</button>
            </div>
        </form>  
    </body>
</template>-->


