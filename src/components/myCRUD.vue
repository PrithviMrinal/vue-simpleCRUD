<script>
//import TicTacToe from "./components/TicTacToe.vue";
//import TicTacToe_newLogic from "./components/TicTacToe_newLogic.vue"

</script>

<template>
    <div>
        <input v-model="prefix" placeholder="Filter prefix">
    <select size="5" v-model="selected">
        <option v-for-key="name in filteredNames">{{ name }}</option>
    </select>
        <label>Name: <input v-model="first"></label>
        <label>Surname: <input v-model="last"></label>
    </div>
</template>

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

<style scoped>
 app1{ 
     color: #42b983;
 }
</style>

