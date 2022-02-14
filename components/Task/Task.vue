<template>
  <div :is="isTag" :class="[task.checked && 'lineThrough', 'task']">
    <component
      :is="!task.checked ? 'IconNotChecked' : 'IconIsChecked'"
      class="task-check"
      @click.native="$emit('changeIcon', { checked: task.checked, order })"
    />
    <p class="task-text">
      {{ `${order}. ${task.text}` }}
    </p>
    <button :disabled="!task.checked" class="remove" @click="$emit('remove', order - 1)">
      remove
    </button>
  </div>
</template>

<script>
import IconIsChecked from './UI/IconIsChecked/IconIsChecked'
import IconNotChecked from './UI/IconNotChecked/IconNotChecked'

export default {
  components: {
    IconIsChecked,
    IconNotChecked
  },
  props: {
    task: {
      type: Object,
      required: true
    },
    order: {
      type: [String, Number],
      required: true
    },
    isTag: {
      type: String,
      default: 'div'
    }
  }
}
</script>

<style lang="scss" scoped>
@import "Task.scss";
</style>
