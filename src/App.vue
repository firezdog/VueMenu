<template>
  <div class="full-width full-height center-content">
    <hello-component :menu-data="[menus]" />
  </div>
</template>

<script>
import HelloComponent from './components/HelloComponent.vue'
import menus from './menus.json'

export default {
  components: {
    HelloComponent
  },
  data () {
    return {
      menus
    }
  }
}
</script>
