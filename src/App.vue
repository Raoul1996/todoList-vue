<template>
  <div id="app">
    <h1 v-html='title'></h1>
    <input v-model="newItem" @keyup.enter="addNew(newItem)"/>
    <ul>
      <li v-for="item in items" v-bind:class="{finished: item.isFinished}" @click="toggleFinish(item)">
        {{item.label+'------'+item.isFinished}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      title: 'this is a todo list',
      items: [],
      newItem: ''
    }
  },
  methods: {
    toggleFinish: function (item) {
      console.log(item)
      item.isFinished = !item.isFinished
    },
    addNew: function (newItem) {
      // body...
      this.items.push({
        label: this.newItem,
        isFinished: false

      })
      console.log(this.newItem)
      this.newItem = ''
    }
  }
}
</script>

<style>
.finished{
  text-decoration: line-through;
}




html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}

#app a {
  color: #42b983;
  text-decoration: none;
}

.logo {
  width: 100px;
  height: 100px
}
</style>
