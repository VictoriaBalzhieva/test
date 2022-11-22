<template>
  <div>
    <h1>Главное меню</h1>
    <ListMenu />

  </div>
</template>

<script>
import ListMenu from '@/components/ListMenu'

export default {
  name: 'HomeView',
  components: {
    ListMenu
  }
  
}
</script>
