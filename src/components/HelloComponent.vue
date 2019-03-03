<template>
  <div class="menu">
    <ul
      v-for="(menu, menuIndex) in menus"
      :key="menuIndex"
    >
      <li
        v-for="(item, itemIndex) in menu"
        :key="`${menuIndex}-${itemIndex}`"
        @mouseover="focus(menuIndex, itemIndex)"
        :class="[(highlights[menuIndex] === itemIndex) ? 'highlighted' : '']"
      >
        Menu Item {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>
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
      if (item.children && item.children.length > 0) {
        this.menus[menuIndex + 1] = item.children
        this.menus = this.menus.slice()
      } else {
        this.menus = this.menus.slice(0, menuIndex + 1)
      }
      this.highlights[menuIndex] = itemIndex
      this.highlights = this.highlights.slice(0, menuIndex + 1)
    }
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
    width: 150px
    background: lightgrey
    padding: 1rem
    li
      padding: 1rem
      text-align: center
      color: black
      &.highlighted
        background: purple
        color: yellow
</style>
