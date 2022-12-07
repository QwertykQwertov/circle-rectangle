<template>
  <div
    class="left-menu no-display"
    id="leftMenu"
  >
    <div class="options-field">
      <input
        type="checkbox"
        style="accent-color: red"
        v-model="store.red"
      > <span class="label">Красные</span>
    </div>
    <div class="options-field">
      <input
        type="checkbox"
        style="accent-color: green"
        v-model="store.green"
      > <span class="label">Зеленые</span>
    </div>
    <div class="options-field">
      <input
        type="checkbox"
        v-model="store.blue"
      >
      <span class="label">Синие</span>
    </div>
    <div class="options-field">
      <input
        type="checkbox"
        style="accent-color: yellow"
        v-model="store.yellow"
      > <span class="label">Желтые</span>
    </div>
    <hr />
    <!--  -->
    <div class="options-field">
      <input
        ref="radioAll"
        type="radio"
        value="all"
        name="dark"
        @change="radioChanged('all')"
      > <span class="label">Все</span>
    </div>
    <div class="options-field">
      <input
        type="radio"
        value="dark"
        name="dark"
        @change="radioChanged('dark')"
      >
      <span class="label">Темные</span>
    </div>
    <div class="options-field">
      <input
        type="radio"
        value="light"
        name="dark"
        @change="radioChanged('light')"
      >
      <span class="label">Светлые</span>
    </div>
  </div>
</template>
<script>
import store from '../store'
export default {
  name: 'LeftMenu',
  data () {
    return {
      store,
    }
  },
  created () {
    this.$nextTick(() => {
      this.$refs.radioAll.checked = true
    })
  },
  methods: {
    radioChanged (value) {
      this.store.darkMode = value
      // console.log(this.store.darkMode)
    }
  },

}
</script>
<style scoped>
.left-menu {
  position: fixed;
  left:0;
  width: 30%;
  height: 100%;
  background-color: rgba(208, 201, 201, 0.4);
  -webkit-transition: left 0.5s linear;
  -moz-transition: left 0.5s linear;
  transition: left 0.5s linear;
}
.no-display {
  position: absolute;
  left: -700px;
  /* display: none; */
  -webkit-transition: left 0.5s linear;
  -moz-transition: left 0.5s linear;
  transition: left 0.5s linear;
}
.options-field {
  margin-top: 50px;
  text-align: left;
  padding-left: 50px;
}
.options-field input {
  zoom: 1.5;
}
.label {
  color: black;
  font-size: 1.5em;
  font-weight: bold;
}
hr {
  margin: 50px 0;
}
</style>