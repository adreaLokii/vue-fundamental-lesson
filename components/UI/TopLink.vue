<template>
  <nuxt-link :to="link">
    <slot></slot>
  </nuxt-link>
</template>

<script>
export default {
  name: "TopLink",
  props: {
    link: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>

</style>