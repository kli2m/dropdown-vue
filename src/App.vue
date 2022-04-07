<script>
import Theme from './components/Theme.vue';
import Select from './components/Select.vue';
import listConsts from './constants/listItems';

export default {
  name: 'App',
  data() {
    return { isDark: true };
  },
  methods: {
    setDarkTheme(val) {
      console.log(val);
      if (this.isDark !== val) {
        this.isDark = val;
      }
    },
  },
  components: {
    Theme,
    Select,
  },
  created() {
    this.listConsts = listConsts;
  },
};
</script>

<template>
  <div v-bind:class="{ 'dark-theme': isDark }" class="wrapper">
    <div class="content">
      <Theme v-on:setDarkTheme="setDarkTheme" />
      <p class="content__select-title">SEARCHABLE DROPDOWN</p>
      <div class="content__selects">
        <Select v-bind:listConsts="listConsts" />
        <Select v-bind:listConsts="listConsts" />
      </div>
    </div>
  </div>
</template>

<style>
* {
  padding: 0;
  margin: 0;
}

.wrapper {
  overflow: hidden;
  background: #fff;
  position: relative;
  max-height: 100vh;
  min-height: 100%;
}
.wrapper.dark-theme {
  background: #12171f;
}
.wrapper.dark-theme * {
  color: #fff;
}
.content {
  padding: 60px 25px;
}
.content__select-title {
  margin-top: 52px;
}
.content__selects {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
