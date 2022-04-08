<template>
  <div class="select-block" v-bind:class="{ 'dark-theme': isDark }">
    <div class="select-block__selected-field">
      <input
        class="select-block__selected-field_btn"
        type="text"
        readonly
        :value="checkcheck[0] && checkcheck[0]"
        v-on:click="openList"
        placeholder="Выберите период"
      />
    </div>
    <div v-if="isShowList" class="select-block__list">
      <div class="select-block__list_search">
        <input
          class="search__input"
          type="text"
          v-model="search"
          placeholder="Поиск"
        />
      </div>
      <div class="items-block">
        <label
          class="items-block__item"
          v-for="(item, key) in list"
          :key="list[key]"
        >
          <input
            class="items-block__item_checkbox"
            type="checkbox"
            v-model="checkcheck"
            :value="item"
          />
          <span class="items-block__item_val-backlight">
            {{ search.slice(0, search.length) }}</span
          >
          <span class="items-block__item_val">
            {{ item.slice(search.length, item.length) }}
          </span>
        </label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'select-block',
  props: {
    listConsts: Array[String],
    isDark: Boolean,
  },
  data() {
    return {
      list: this.listConsts,
      isShowList: false,
      checkcheck: [],
      search: '',
    };
  },
  methods: {
    openList: function () {
      this.isShowList = !this.isShowList;
    },
  },
  watch: {
    search: function () {
      this.list = this.listConsts.filter((el) =>
        el.toLowerCase().startsWith(this.search.toLowerCase())
      );
    },
  },
};
</script>

<style>
.select-block {
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  flex-direction: column;
  color: #181f29;
  margin-right: 20px;
}

.select-block__selected-field {
  width: 300px;
  height: 34px;
  margin-bottom: 11px;
}
.select-block__selected-field_btn {
  width: 100%;
  height: 100%;
  background: #ffffff;
  border: 1px solid #86d4e8;
  box-sizing: border-box;
  border-radius: 5px;
  cursor: pointer;
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 15px;
  mix-blend-mode: normal;
  padding: 10px;
  display: flex;
  justify-content: flex-start;
}

.select-block__selected-field_btn::placeholder,
.search__input::placeholder {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 15px;
  color: #888888;
  opacity: 0.5;
}
.dark-theme .select-block__selected-field_btn::placeholder,
.dark-theme .search__input::placeholder {
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 15px;
  color: #828282;
  opacity: 1;
}
.select-block__list {
  width: 300px;
  height: 255px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  background: #ffffff;
  border: 1px solid #c4c4c4;
  box-sizing: border-box;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
}
.dark-theme .select-block__list {
  background: #181f29;
  border: 1px solid #0e1319;
}
.dark-theme .select-block__list,
.dark-theme .select-block__selected-field_btn {
  background: #181f29;
  color: #fff;
}
.select-block__list_search {
  width: 280px;
  height: 34px;
  margin: 10px;
}
.search__input {
  width: inherit;
  height: inherit;
  background: #ffffff;
  border: 1px solid #c4c4c4;
  box-sizing: border-box;
  border-radius: 4px;
}
.dark-theme .search__input {
  background: #293341;
  border: 1px solid #2c3848;
  box-sizing: border-box;
  border-radius: 4px;
}
.items-block {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 15px;
  overflow-y: scroll;
}
.items-block::-webkit-scrollbar {
  width: 4px;
}
.items-block::-webkit-scrollbar-track {
  opacity: 0.6;
  background: #828282;
}
.items-block::-webkit-scrollbar-thumb {
  background: #4f4f4f;
  opacity: 0.2;
}
.items-block__item {
  display: flex;
  align-items: center;
  width: 100%;
  min-height: 40px;
  cursor: pointer;
}
.items-block__item:hover {
  background: rgba(134, 212, 232, 0.5);
}

.items-block__item_checkbox {
  margin: 0 10px 0 18px;
  cursor: pointer;
}
.search__input {
  padding: 10px;
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 15px;
}

.items-block__item > .items-block__item_checkbox {
  position: relative;
  -webkit-appearance: none;
  -moz-appearance: none;
  -o-appearance: none;
  appearance: none;
  width: 16px;
  height: 16px;
  border: 1px solid #bdbdbd;
  box-sizing: border-box;
  border-radius: 2px;
  cursor: pointer;
}

.items-block__item > input:checked {
  border: none;
  background: #56ccf2;
  border: 1 px solid #56ccf2;
  box-sizing: border-box;
  border-radius: 2px;
}
.items-block__item > input:checked::before {
  content: '\2713';
  display: block;
  color: #181f29;
  position: absolute;
  left: 0.25rem;
  top: -0.15rem;
}
.items-block__item_val-backlight {
  color: #10cf68 !important;
}
</style>
