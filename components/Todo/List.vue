<template>
  <div class="none-scrollbar mt-10 mb-10 flex flex-col items-center border-2 p-4 overflow-scroll overflow-x-hidden
              max-h-[40rem] overscroll-none rounded-3xl w-3/4 border-indigo-500">
    <slot></slot>

  </div>
</template>

<script>
export default {
  name: "List"
}
</script>

<style scoped>
  .none-scrollbar::-webkit-scrollbar {
    width: 0;
  }
</style>