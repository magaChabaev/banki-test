<template>
  <div class="container">
    <div class="header">
      <div class="navigation">
        <ul class="list">
          <li class="list_item">Каталог</li>
          <li class="list_item">Доставка</li>
          <li class="list_item">Оплата</li>
          <li class="list_item">Контакты</li>
          <li class="list_item">О компании</li>
        </ul>
      </div>
      <div class="search">
        <input
          class="search_input"
          placeholder="Поиск по названию картины"
          v-model="inputValue"
          @input="onValueChange"
        />
        <button class="search_button">Найти</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  methods: {
    onValueChange(e) {
      this.inputValue = e.target.value;
      this.$emit("onInputChange", this.inputValue);
    },
  },
  data() {
    return {
      inputValue: "",
    };
  },
};
</script>

<style>
.container {
  border-bottom: 1px solid #e1e1e1;
}

.header {
  max-width: 1216px;
  margin: 0 auto;
  height: 97px;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
}

ul {
  margin: 0;
  list-style-type: none;
  color: #343030;
  font-size: 14px;
  line-height: 21px;
  padding: 0px;
}

.list {
  display: flex;
}

.list_item:not(:first-child) {
  margin-left: 48px;
}

.navigation {
  margin: 0 auto;
}

.search_button {
  padding: 14px 36px 13px;
  font-weight: 700;
  line-height: 21px;
  background-color: #403432;
  color: white;
  border: none;
  font-size: 14px;
  font-family: "Merriweather", sans-serif;
}

.search_input {
  border: 1px solid #e1e1e1;
  width: 294px;
  padding: 13px 0px 14px 16px;
  line-height: 21px;
  background-color: #f6f3f3;
  font-family: "Merriweather", sans-serif;
}

.search_input:focus {
  outline: none;
}

@media screen and (min-width: 321px) and (max-width: 1215px) {
  .list {
    flex-direction: column;
  }
  .list_item:not(:first-child) {
    margin-left: 0;
  }
  .header {
    height: auto;
  }
  .search_button {
    display: none;
  }
}
</style>
