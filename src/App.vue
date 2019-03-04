<template>
  <div class="full-width full-height center-content">
    <Menu :menu-data="[menus]" />
  </div>
</template>

<script>
import Menu from './components/menu.vue'
import menus from './menus.json'

export default {
  components: {
    Menu
  },
  data () {
    return {
      menus
    }
  }
}
</script>
