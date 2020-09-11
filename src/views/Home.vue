<template>
  <div class="home">
    <h1>Crea una nueva tarea</h1>
    <h2>Tarea</h2>
    <input type="text" v-model="tarea">
    <button @click="crear" v-bind:class="{'disabled':tarea==''}">Crear</button>
    <ul>
      <li v-for="(tarea,index) in tareas" v-bind:key="index">{{index}}: {{tarea}}
        <button @click="eliminar(index)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
    
  },
  data() {
    return {
      tarea:"",
      tareas:[]
    }
  },
  methods:{
    crear() {
      this.tareas.push(this.tarea);
      this.tarea="";
    },
    eliminar(indice){
      this.tareas.splice(indice,1);
    }
  }
}
</script>

<style lang="scss" scoped>
button{
  &.disabled{
    opacity: 0.5;
    pointer-events: none;
  }
}
</style>