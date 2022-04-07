<template>
  <div class="choose-topic">
    <p class="choose-topic_title">THEME</p>
    <button v-on:click="$emit('setDarkTheme', true)" class="choose-topic_dark">
      DARK
    </button>
    <button
      v-on:click="$emit('setDarkTheme', false)"
      class="choose-topic_light"
    >
      LIGHT
    </button>
  </div>
</template>

<script>
export default {
  name: 'Choose-theme',
};
</script>

<style>
.choose-topic {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  margin-right: 29px;
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 15px;
  color: #000000;
}

.choose-topic_title {
  margin-right: 29px;
}
.choose-topic_dark,
.choose-topic_light {
  cursor: pointer;
  border: none;
  background: inherit;
  margin-right: 15px;
}
</style>
