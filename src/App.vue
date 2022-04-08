<script>
import Theme from './components/Theme.vue';
import Select from './components/Select.vue';
import { listConsts, listConstsTwo } from './constants/listItems';

export default {
  name: 'App',
  data() {
    return { isDark: false };
  },
  methods: {
    setDarkTheme(val) {
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
    this.listConstsTwo = listConstsTwo;
  },
};
</script>

<template>
  <div v-bind:class="{ 'dark-theme': isDark }" class="wrapper">
    <div class="content">
      <Theme v-on:setDarkTheme="setDarkTheme" />
      <p class="content__select-title">SEARCHABLE DROPDOWN</p>
      <div class="content__selects">
        <Select :listConsts="listConsts" :isDark="isDark" />
        <Select :listConsts="listConstsTwo" :isDark="isDark" />
        <Select :listConsts="listConsts" :isDark="isDark" />
      </div>
    </div>
  </div>
</template>

<style>
* {
  padding: 0;
  margin: 0;
}
input {
  outline: none;
}
.wrapper {
  overflow: hidden;
  background: #fff;
  position: relative;
  min-height: 100vh;
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
  margin-top: 12px;
}
</style>
