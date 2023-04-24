<template>
  <div>
    <UITitleCenter class="mt-24">
      Todo list
    </UITitleCenter>
  </div>
  <UIButton @click="openPopup">
    Create
  </UIButton>
  <BlockCenterContent>
    <TodoList>
      <TodoItem v-for="item in posts" :key="item.id" :post="item" @deleteTodo="deleteTodo" @createPost="createPost" />
    </TodoList>
  </BlockCenterContent>
  <UIDialog v-model="dialogVisible">
    <h2 class="text-2xl">Create todo</h2>
    <UITextField placeholderInput="Playing title" v-model="templateNewPost.title" />
    <UITextField placeholderInput="Playing body" v-model="templateNewPost.body"/>
    <UIButton @click="createPost(templateNewPost)">
      {{ nameButton }}
    </UIButton>
  </UIDialog>
</template>

<script>
export default {
  name: "vueFundamental",
  data: () => {
    return{
      posts: [],
      dialogVisible: false,
      templateNewPost: {
        title: '',
        body: '',
        id: 0
      },
      nameButton: 'Create'
    }
  },
  async mounted () {
    const response = await $fetch('https://jsonplaceholder.typicode.com/posts?_limit=10')
    this.posts = response
  },
  methods: {
    deleteTodo (id) {
      this.posts = this.posts.filter(item => item.id !== id)
    },
    openPopup (id) {
      this.dialogVisible = true
    },
    openRedactor (id) {
      this.dialogVisible = true
      this.nameButton = 'Edit'
    },
    createPost (newPost) {
      console.log(this.posts.filter(item => item.id === newPost.id).length);
      if (this.posts.filter(item => item.id === newPost.id).length) {
        const editPost = this.posts.filter(item => item.id === newPost.id)
        editPost.title = this.templateNewPost.title
        editPost.body = this.templateNewPost.body
      } else {
        newPost.id = new Date().getTime()

        this.posts.push(newPost)

        this.templateNewPost = {}
      }


      this.dialogVisible = false
    }
  }
}
</script>

<style scoped>

</style>