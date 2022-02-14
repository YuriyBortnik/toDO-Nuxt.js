<template>
  <div class="container">
    <div class="app">
      <h1 style="margin-bottom: 10px;">
        List of tasks
      </h1>
      <ui-input :plus="true" @addTask="addTask" />
      <ul v-if="!!tasks.length" style="margin-top: 10px;">
        <task
          v-for="(item, index) of tasks"
          :key="item.id"
          :task="item"
          :order="index + 1"
          is-tag="li"
          @changeIcon="changeIcon"
          @remove="removeTask"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import UiInput from '~/components/UI/Input/UiInput'
import Task from '~/components/Task/Task'

export default {
  components: {
    UiInput,
    Task
  },
  data () {
    return {
      tasks: []
    }
  },
  methods: {
    addTask (text) {
      this.tasks.push({
        id: this.tasks.length + 1,
        text,
        checked: false
      })
    },
    changeIcon ({ checked, order }) {
      this.tasks[order - 1].checked = !checked
    },
    removeTask (index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

.app {
  padding: 20px;
  width: 400px;
  height: auto;
  border-radius: 5px;
  background-color: #eaddcf;
  box-sizing: border-box;
}
</style>
