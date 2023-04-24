<template>
  <div class="mt-24">
    <UITitleCenter>
      Home
    </UITitleCenter>
    <BlockLeftContent />
  </div>
</template>

<script>
export default {
  name: "index",
  mounted() {
    console.log(this.$store)
  }
}
</script>

<style scoped>

</style>