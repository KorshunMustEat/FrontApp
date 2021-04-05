<template>
<h1>Список дел</h1>
<h4>Добавьте в список новые значения</h4>
<form @submit.prevent="appNewTask">
  <input type="text" v-model.trim="newTask" placeholder="Введите текст">
  <button >Добавить дело</button>
</form>
<div id="tasks">
  <div class="showTasks" v-for="post in tasks" :key="post.id">
    <p>{{ post.text }} <button  @click="deletePost(post.id)">Удалить</button></p>

  </div>
</div>

</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      newTask: '',
      tasks: []
    }
    },
    methods: {
      deletePost() {
        let newArr = [];
        this.tasks.forEach(item => {
          if( newArr)
          newArr.push(item);
        });
        this.tasks = newArr;
      },
    appNewTask() {
      if(this.newTask.length > 3) {
        this.tasks.unshift({
          id: this.tasks.length + 1,
          text: this.newTask
        });
        this.newTask = ''
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.showTasks{

  margin: 10px 0;
  display: flex;
  justify-content: center;
}
input {
  border-radius: 5px;
}
p {font-weight: 700}
button {
  background: black;
  color: white;
  border: 1px solid silver;
  border-radius: 10px;
  transition: 0.25s ease;
}
button:hover{
  background: #3d3454;
  border: 2px solid #726c82;
  font-weight: 500;
  color: #e67070;
}
form > button {border-radius: 5px}
form > button:hover {
  background: #3d3454;
  border: 2px solid #726c82;
  font-weight: 500;
  color: white;
}
</style>
