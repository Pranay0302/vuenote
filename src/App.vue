<template>
 <h1>notes</h1>
 <form @submit.prevent="newnote" class="nform">
     <input v-model='userip' name="okay" class="nokay">
     <!-- <h2>{{userip}}</h2> -->
     <div class="oof">
     <button class="nbutton">new note</button>
     <button class="ndelete" @click="done">delete all</button>
     </div>
 </form>
 <ul>
 <li v-for="item in notes" :key="item.id" v-bind="enabled">
     <h3>{{item.content}}</h3>
 </li>
 </ul>
</template>

<script>

import { ref } from 'vue';

export default {
    
    setup(){

        // object wrapper
        const userip = ref('');
        const notes = ref([]);

        function newnote(){
            // console.log(userip.value)
            notes.value.push({
                id: 0,
                content: userip.value
            })
            userip.value = '';
        }

        function done(){
            // yet to add
        }

        return {
            userip,
            notes,
            newnote,
            done
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
.nbutton, .ndelete{
    margin: 4px;
}
.nokay{
    margin: 5px;
    height: 25px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
