<template>
  <div class="app">
    <h1>{{title}}</h1>
    <div class="list">
      <input type="text" v-model="text" v-on:keyup.enter="addTodo" maxlength="10">
      <p v-if="this.list.length === 0">Adicione uma tarefa!</p>
      <p v-else>Adicione mais tarefas!</p>
      <ul>
        <li v-for="(item, index) in list"
            v-bind:key="index"
         >

          <strong>{{item.text}}</strong>
          <button v-on:click="removeTodo(index)">X</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

  export default {
    data () {
      return {
        title: 'To-do List',
        text: '',
        list: []
      }
    },
    methods: {
      addTodo () {
        this.list.push({text: this.text})
        this.text = ''
      },
      removeTodo (index) {
        this.list.splice(index, 1)
      }
    }
   
  }
</script>

<style scoped>
  button {
    margin-left: 5px;
    border: 5px;
    border-radius: 5px;
  }

  button:hover {
    background-color: whitesmoke;
    box-shadow: 1px 3px 2px rgba(95, 93, 93, 0.582);
    transition: 0.3s;
  }
</style>