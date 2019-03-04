<template>
  <div
    class="menu"
    @mouseleave="menus = menus.slice(0,1); highlights = [];"
  >
    <ul
      v-for="(menu, menuIndex) in menus"
      :key="menuIndex"
    >
      <li
        v-for="(item, itemIndex) in menu"
        :key="`${menuIndex}-${itemIndex}`"
        :class="[(highlights[menuIndex] === itemIndex) ? 'highlighted' : '']"
        @mouseover="focus(menuIndex, itemIndex)"
      >
        Menu Item {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>
import helper from '../middleware/debounce'

export default {
  props: {
    menuData: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      menus: this.menuData,
      highlights: []
    }
  },
  methods: {
    focus (menuIndex, itemIndex) {
      const item = this.menus[menuIndex][itemIndex]
      const throughNextMenu = menuIndex + 2
      const throughThisMenu = menuIndex + 1
      if (item.children && item.children.length > 0) {
        this.menus[menuIndex + 1] = item.children
        this.menus = this.menus.slice(0, throughNextMenu)
      } else {
        this.menus = this.menus.slice(0, throughThisMenu)
      }
      this.highlights[menuIndex] = itemIndex
      this.highlights = this.highlights.slice(0, throughThisMenu)
    },
    debounce: helper.debounce
  }
}
</script>

<style lang="stylus" scoped>
.menu
  display: flex
  flex-direction: row
  justify-content: start
  ul
    list-style: none
    display: flex
    flex-direction: column
    width: 200px
    background: lightgrey
    padding-left: 0
    li
      padding: 1rem
      text-align: center
      color: black
      &.highlighted
        background: purple
        color: yellow
</style>
