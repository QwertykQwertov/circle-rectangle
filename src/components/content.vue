<template>
  <div>
    <LeftMenu />
    <div class="container">
      <div
        :style="{width: countColumns}"
        v-for="(figure, index) in filteredFigure"
        :key="index"
      >
        <div
          class="geometry"
          :style="{'background-color': whatColor(figure), 'border-radius': whatFigure(figure)}"
        >
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import LeftMenu from './left-menu.vue'
import store from "../store"
export default {
  name: 'Content',
  components: {
    LeftMenu,
  },
  props: {},
  data () {
    return {
      store
    }
  },
  computed: {
    filteredFigure () {
      let initArr = this.store.figures
      console.log(this.store.darkMode)
      if (this.store.darkMode === 'dark') {
        initArr = initArr.filter((el) => el.dark == true)
      } else if (this.store.darkMode === 'light') {
        initArr = initArr.filter((el) => el.dark == false)
      }
      if (!this.store.isCircle) {
        initArr = initArr.filter((el) => el.form != 'circle')
      }
      if (!this.store.isSquare) {
        initArr = initArr.filter((el) => el.form != 'square')
      }
      if (!this.store.red) {
        initArr = initArr.filter((el) => el.color != 'red')
      }
      if (!this.store.green) {
        initArr = initArr.filter((el) => el.color != 'green')
      }
      if (!this.store.blue) {
        initArr = initArr.filter((el) => el.color != 'blue')
      }
      if (!this.store.yellow) {
        initArr = initArr.filter((el) => el.color != 'yellow')
      }
      return initArr
    },
    countColumns () {
      return Math.floor(100 / this.store.columns) + '%'
    }
  },
  methods: {
    whatColor ({ color, dark }) {
      if (dark) {
        if (color === 'yellow') {
          return 'orange'
        }
        return 'dark' + color
      }
      return color
    },
    whatFigure ({ form }) {
      if (form == 'circle') {
        return '50%'
      } else if (form == 'square') {
        return '0%'
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  margin: 0 5%;
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
}
.geometry {
  height: 200px;
  width: 200px;
  margin: 5px auto;
}
.triangle-top {
  width: 0;
  height: 0;
  border-left: 100px solid transparent;
  border-right: 100px solid transparent;
  border-bottom: 200px solid #f95959;
}
</style>
