<template>
  <div class="mt-5">
    <ul>
    <li v-for="(resultadoTareas,index) in tareaHijo" :key="index">Tarea {{index+1}}: {{resultadoTareas.tarea}}
      <input type="number" placeholder="Nº repetición tarea" v-model.number="resultadoTareas.cantidad"/>
      <button class="btn-info"  @click="resultadoTareas.cantidad ++">+</button>
    <button class="btn-danger" @click.prevent="quitarTarea(index)">Eliminar</button>

    </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Hijo",
  props: {
    tareaHijo:{
      type:Array,
      default: () => []
    }
  },
  methods:{
    quitarTarea(eliminar){ /*a traves de metodos el hijo se comunica o envia datos al padre*/
      this.$emit('quitarTarea',eliminar)/*emit=emite un metodo*/
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
