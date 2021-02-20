<template>
    <button class="button buttonSub" v-on:click="submit()">Delete DB</button>
</template>

<script>
import axios from 'axios';

export default {
    name:"Button",
    methods: {
        submit(){
            axios.delete('http://localhost:5000/api/restaurant/delete-all');
        }
    },
}  

</script>

<style scoped>
.button {
  background-color: #48297c;
  width: 100px;
  border: none;
  color: white;
  padding: 10px 5px 10px 5px;
  text-align: center;
  text-transform: uppercase;
  display: inline-block;
  font-size: 10px;
  margin: 0px 0px 0px 0px;
  -webkit-transition-duration: 0.4s;
  transition-duration: 0.4s;
  cursor: pointer;
}

.buttonSub {
  background-color: white; 
  color: black; 
  border: 2px solid #48297c;
}

.buttonSub:hover {
  background-color: #48297c;
  color: white;
}
</style>