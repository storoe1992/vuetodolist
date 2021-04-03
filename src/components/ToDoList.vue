<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <form class="tareaform">
      <h2>Tarea</h2>
      <input v-model="tarea" placeholder="Ingresa una nueva tarea"/>
      <button @click="addTarea($event)">Crear</button>
    </form>
    <h3>Lista</h3>
    <ul>
      <li v-for="(tarear,index) in todolist" :key="index">{{tarear}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ToDoList',
  props: {
    msg: String
  },
  data() {
    return {
      todolist : [],
      tarea : ""
    }
  },
  methods : {
    addTarea(event){
      event.preventDefault();
      if(!(this.tarea.trim() === "")){
        this.todolist.push(this.tarea);
        this.tarea = "";
      }else{
        alert("Escriba una tarea")
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss" scoped>
.tareaform{
  display: flex;
  align-items: center;
  justify-content: center;

  button{
    margin-left: 5px;
  }

  h2 {
    margin-right: 5px;
  }
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style: none;
  padding: 0;
}
</style>
