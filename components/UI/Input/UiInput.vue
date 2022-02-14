<template>
  <div class="input">
    <input v-model="value" class="input__type" type="text" placeholder="Write something">
    <div v-if="showPlus" class="addText" @click="emitValue">
      +
    </div>
  </div>
</template>

<script>
export default {
  props: {
    plus: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      value: ''
    }
  },
  computed: {
    showPlus () {
      return this.plus ? this.value.length > 3 : false
    }
  },
  methods: {
    emitValue () {
      this.$emit('addTask', this.value)
      this.value = ''
    }
  }
}
</script>

<style lang="scss" scoped>
@import "UiInput.scss";
</style>
