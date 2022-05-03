<script>
export default {
  data() {
    return {
      names: ['Emil, Hans', 'Mustermann, Max', 'Tisch, Roman'],
      selected: '',
      prefix: '',
      first: '',
      last: ''
    }
  },
  computed: {
    filteredNames() {
      return this.names.filter((n) =>
        n.toLowerCase().startsWith(this.prefix.toLowerCase())
      )
    }
  },
  watch: {
    selected(name) {
      ;[this.last, this.first] = name.split(', ')
    }
  },
  methods: {
    create() {
      if (this.hasValidInput()) {
        const fullName = `${this.last}, ${this.first}`
        if (!this.names.includes(fullName)) {
          this.names.push(fullName)
          this.first = this.last = ''
        }
      }
    },
    update() {
      if (this.hasValidInput() && this.selected) {
        const i = this.names.indexOf(this.selected)
        this.names[i] = this.selected = `${this.last}, ${this.first}`
      }
    },
    del() {
      if (this.selected) {
        const i = this.names.indexOf(this.selected)
        this.names.splice(i, 1)
        this.selected = this.first = this.last = ''
      }
    },
    hasValidInput() {
      return this.first.trim() && this.last.trim()
    }
  }
}
</script>

<template>
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
</template>
<style>
* {
  font-size: inherit;
}

input {
  display: block;
  margin-bottom: 10px;
}

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
