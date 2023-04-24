<template>
  <div class="border-2 rounded-3xl border-indigo-400 p-6 mt-4">
    <h2 class="text-2xl">
      <strong>Title: </strong>
      <span>
        {{ post.title }}
      </span>
    </h2>
    <p class="text-xl">
      <strong> Body: </strong>
      <span>
        {{ post.body }}
      </span>
    </p>
    <div class="flex justify-end">
      <UIButton class="mr-4" @click="$emit('createPost', post.id)">
        Edit
      </UIButton>
      <UIButton @click="$emit('deleteTodo', post.id)">
        Delete
      </UIButton>
    </div>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: {
    post: {
      type: Object,
      default: () => {}
    }
  },
  methods: {
    deleteTodo () {

    }
  }
}
</script>

<style scoped>

</style>