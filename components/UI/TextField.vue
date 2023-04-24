<template>
  <div>
    <label :for="id"></label>
    <input :type="typeInput" :id="id" @input="$emit('update:modelValue', $event.target.value)" :value="modelValue" :placeholder="placeholderInput" class="p-2 text-xl border-2 border-indigo-200 mt-2">
  </div>
</template>

<script>
let uid = 0
export default {
  name: "TextField",
  data: () => {
    return {
      id: uid++,
    }
  },
  props: {
    typeInput: {
      type: String,
      default: 'text'
    },
    placeholderInput: {
      type: String,
      default: ''
    },
    modelValue: {
      type: String,
      default: ''
    }
  },
}
</script>

<style scoped>

</style>