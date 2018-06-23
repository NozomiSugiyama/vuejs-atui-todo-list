<template>
  <div class="container" id="app">
    <div class="app">
      <h1>TODO List</h1>
      <div class="row">
        <div class="column">
          <at-input v-model="inputTitle" placeholder="Input Title"></at-input>
          <at-input v-model="inputDescription" placeholder="Input description"></at-input>
        </div>
        <at-button @click="addTODO">ADD</at-button>
      </div>
      <div class="card-wrapper">
        <at-card style="width: 300px; margin: 1rem 0;" v-for="(item, index) in todoList" :key='index'>
          <h4 slot="title">{{ item.title }}</h4>
          <div slot="extra">
            <at-button type="text" @click="deleteTODO(item)">Delete</at-button>
          </div>
          <div>
            {{ item.description }}
          </div>
        </at-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: {
    inputTitle: "",
    inputDescription: "",
    todoList: [],
  },
  methods: {
    addTODO: function () {
      this.todoList = this.todoList.concat(({ title: this.inputTitle, description: this.inputDescription }))
      this.inputTitle = ""
      this.inputDescription = ""
    },
    deleteTODO: function (item) {
      this.todoList = this.todoList.filter(x => x !== item)
    }
  }
}
</script>

<style lang="scss">
  .container {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: -apple-system, BlinkMacSystemFont, "Helvetica Neue", Helvetica, "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", "微软雅黑", Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  .app {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: 100%;
    color: #2c3e50;
    text-align: center;
  }
  .card-wrapper {
    width: 100%;
    margin-top: 4rem;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
  }
  h1, h2 {
    font-weight: normal;
    margin: 16px 0;
  }
</style>
