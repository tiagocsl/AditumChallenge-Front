<template>
  <div class="hello">
    <h1>{{ msg }}</h1> 
    <div>
      <div>    
        <label class="SendArchive TransAct" for="arquivo">Enviar arquivo</label> 
        <input type="file" id="arquivo" ref="file" class="inputFile" v-on:change="handleFileUpload()"/>
        <input type="time" id="clock" class="clockInput TransAct" v-on:change="handleTime()"/>
        <Button/>   
      </div>
      <div class="grid-div">
        <v-grid
        class = "gridV"
        theme="compact"
        row-headers="true"
        :source="rows"
        :columns="columns"
        /> 
      </div>    
    </div>       
  </div>
</template>

<script>
import axios from 'axios';
import VGrid from "@revolist/vue-datagrid";
import Button from '../components/Button'

export default {
  name: 'Home',
  components: {
    VGrid,
    Button
  },
  data(){
        return {
          file:'',
          columns: [
            {
              name: "Restaurante",
              prop:"name",
              size: 150,
            },
            { 
              name: "Horário de Abertura",
              prop: "openHour",
              size: 200,
            },
            {
              name: "Horário de Fechamento",
              prop: "closeHour",
              size: 200,             
            },
          ],
          rows: [],
        };
    },
    methods: {
        handleFileUpload(){
          var arquivo = document.querySelector("#arquivo");
          var filezin = arquivo.files[0];
          this.file = filezin;
          var formdata = new FormData();         
          formdata.append('file', this.file);
          axios.post('http://localhost:5000/api/restaurant/csv', formdata);
          /* eslint-disable no-console */
          console.log("Arquivos Enviados");
          /* eslint-disable no-console */
        },
        handleTime(){
          var clock = document.querySelector("#clock");
          var valorLido = clock.value;
          this.rows = [];
          /* eslint-disable no-console */
          console.log(valorLido);
          /* eslint-disable no-console */ 
          axios.get("http://localhost:5000/api/restaurant/filter?hour=" + valorLido)
               .then(response => { this.rows = response.data });
          /* eslint-disable no-console */
          console.log(this.rows.length);
          /* eslint-disable no-console */ 
        }
    },
    props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #48297C;
}
.SendArchive{
  padding: 10px 5px 10px 5px;
  width: 100px;
  background-color: #48297c;
  color: #FFF;
  text-transform: uppercase;
  font-size: 10px;
  text-align: center;
  display: inline-block;
  margin: 0px 0px 0px 0px;
  cursor: pointer;
}
.inputFile{
  display: none;
}
.clockInput{
  background-color: #48297c;
  width: 100px;
  border: none;
  color: white;
  padding: 08px 0px 08px 0px;
  text-align: center;
  text-transform: uppercase;
  display: inline-block;
  font-size: 10px;
  margin: 0px 10px 0px 10px;
  -webkit-transition-duration: 0.4s;
  transition-duration: 0.4s;
  cursor: pointer;
}

.TransAct{
  background-color: white; 
  color: black; 
  border: 2px solid #48297c;
}

.TransAct:hover {
  background-color: #48297c;
  color: white;
}
.grid-div {
  height: 300vh;
  text-align-last: center;
  margin: 0vh 60vh 0vh 60vh;
}

.gridV{
  padding-right: 15px;
}

</style>
