<template>
  <div class="container h-screen bg-slate-200">
    <SidebarTopMenu class="flex w-1/2 ml-auto justify-end pt-6">
      <UITopLink v-for="item in links" :link="item.location" class="text-grey-500 pr-10 text-2xl last:pr-0">
          {{ item.title }}
      </UITopLink>
    </SidebarTopMenu>
    <NuxtPage />
  </div>
</template>

<script>
export default {
  data: () => {
    return {
    links: [
      {
        id: 1,
        title: 'Home',
        location: '/'
      },
      {
        id: 2,
        title: 'Works',
        location: '/works'
      },
      {
        id: 3,
        title: 'Creative',
        location: '/creative'
      }]
    }
  },
  computed: {

  }
}
</script>

<style scoped>

</style>