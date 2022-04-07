<template>
  <div class="select-block">
    <div class="select-block__selected-field">
      <input
        class="select-block__selected-field_btn"
        type="button"
        :value="!checkcheck[0] ? 'Выберите период' : checkcheck[0]"
        v-on:click="openList"
        placeholder="Выберите период"
      />
    </div>
    <div v-if="isShowList" class="select-block__list">
      <div class="select-block__list_search">
        <input class="search__input" type="text" v-model="search" />
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
          <span class="item-block__item_name">{{ item }}</span>
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
      this.list = this.listConsts.filter((el) => {
        return el.toLowerCase().startsWith(this.search);
      });
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
}
.select-block__selected-field {
  width: 300px;
  height: 34px;
}
.select-block__selected-field_btn {
  width: 100%;
  height: 100%;
  background: #ffffff;
  border: 1px solid #86d4e8;
  box-sizing: border-box;
  border-radius: 5px;

  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 15px;

  color: #181f29;

  mix-blend-mode: normal;
  padding: 10px;
  display: flex;
  justify-content: flex-start;
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

.items-block::-webkit-scrollbar-thumb {
  opacity: 0.6;
  background: #828282;
}
.items-block__item {
  display: flex;
  align-items: center;
  width: 100%;
  min-height: 40px;
  color: #2c3848;
}
.items-block__item:hover {
  background: rgba(134, 212, 232, 0.5);
}
.items-block__item_checkbox {
  margin: 0 10px 0 18px;
}
.search__input {
  padding: 10px;
  font-family: 'Roboto';
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 15px;
  color: #181f29;
}
</style>
