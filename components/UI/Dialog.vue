<template>
  <div class="fixed flex inset-x-0 inset-y-0 z-10 w-full h-full dialog-wind justify-center items-center" @click="disabledDialogWindow" v-show="modelValue">
    <div @click.stop class="flex flex-col border-2 p-8 rounded-indigo-200 w-[32] h-[32] bg-white">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dialog",
  props: {
    modelValue: {
      type: Boolean,
      required: true,
      default: false
    }
  },
  methods: {
    disabledDialogWindow () {
      event.stopPropagation()
      this.$emit('update:modelValue', false)
    }
  }
}
</script>

<style scoped>
.dialog-wind{
  background-color: rgba(0, 0, 0, 0.5);
}
</style>