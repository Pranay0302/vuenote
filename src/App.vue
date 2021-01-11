<template>
 <h1>notes</h1>
 <form @submit.prevent="newnote" class="nform">
     <input v-model='userip' name="okay" class="nokay">
     <!-- <h2>{{userip}}</h2> -->
     <div class="oof">
     <button class="nbutton">new note</button>
     <button class="nd" @click="lol"> delete</button>
     <button class="ndelete" @click="done">delete ALL</button>
     </div>
 </form>
 <ul>
 <div v-for="item in notes" :key="item.id">
     <h3>{{item.content}}</h3>
 </div>
 </ul>
</template>

<script>

import { ref } from 'vue';

export default {
    
    setup(){

        // object wrapper
        const userip = ref('');
        let notes = ref([]);
        notes.value = JSON.parse(localStorage.getItem("data"));
        function newnote(){
            // console.log(userip.value)
            notes.value.push({
                id: 0,
                content: userip.value
            })
            userip.value = '';
            localStorage.setItem("data", JSON.stringify(notes.value));
        }

        function done(){
                notes.value.splice(0,notes.value.length);
                localStorage.clear();
        }
        
        function lol(){
            notes.value.shift(notes.value[0]);
        }


        return {
            userip,
            notes,
            newnote,
            done,
            lol
        }
    }
}
</script>

<style>
.nform{
    margin: 5px;
    padding: 5px;
}
.oof{
    padding: 5px;
    color: #2c3e50;
}
.nbutton, .ndelete, .nd{
    margin: 4px;
}
.nokay{
    margin: 5px;
    height: 25px;
}
html{
    background-color: #34495E;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: #41B883;
  padding: 40px;
}
</style>
