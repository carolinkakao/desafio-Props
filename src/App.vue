<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />   
    <h1>Planificación de tareas</h1>
    <section class="mt-3">
    <input placeholder="Escribe tu tarea" type="text" v-model="tarea" @keyup.enter="agregarTarea()">    <!-- v-model: hace la conexión directa entre input y js, texto escrito en input es detectado por vue//@keyup.enter= para agregar tareas con el enter-->
    <button @click="agregarTarea()" type="button" class="btn btn-danger ms-4">Añade tu Tarea</button>  <!--evento click  -->
    </section>
    <Hijo :tareaHijo="misTareas" @quitarTarea="eliminarTarea" />
  </div>
</template>

<script>
import Hijo from "./components/Hijo.vue";

export default {
  name: "App",
 data(){
   return{
     misTareas:[
       /*
       {tarea:"", cantidad:""},
       {tarea:"",cantidad:""},
       {tarea:"",cantidad:""}
       */
     ],
     tarea:"",
     cantidad:""
   }
 },
  components: {
    Hijo,
  },
  methods:{
    agregarTarea(){
    if(this.tarea !== ""){ 
          this.misTareas.push({
          tarea: this.tarea
          })
      this.tarea = "" }else{ /* this.tarea="" --> para que se limpie el imput al momento de escribir*/
        alert("Debes escribir tu tarea"); 
    }
    },
    eliminarTarea(eliminar){
      this.misTareas.splice(eliminar,1); /*con slice puedo extraer la parte que quiera de un array*/
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
