<template>
  <div class="container mx-auto min-h-screen">
    <SidebarTopMenu class="flex items-center ml-auto justify-between pt-6">
      <CreativeLightSwitcher />
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
      },
      {
        id: 4,
        title: 'Vue fundamental',
        location: '/vueFundamental'
      }]
    }
  },
  computed: {

  }
}
</script>

<style scoped>

</style>