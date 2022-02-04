<template>
  <div class="container">
    <div class="footer">
      <div class="navigation">
        <ul class="list">
          <li class="list_item">Каталог</li>
          <li class="list_item">Доставка</li>
          <li class="list_item">Оплата</li>
          <li class="list_item">Контакты</li>
          <li class="list_item">О компании</li>
        </ul>
      </div>
      <div class="address">
        <div class="address_item">
          <img src="../assets/Phone.png" class="image" />
          <p class="address_item_text">+7 (812) 555-55-55</p>
        </div>
        <div class="address_item">
          <img src="../assets/Address.png" class="image" />
          <p class="address_item_text">г. Санкт-Петербург, ул. Ефимова, 3</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style scoped>
.container {
  background-color: #eceaea;
}
.footer {
  max-width: 1216px;
  margin: 0 auto;
  height: 96px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: #555555;
  line-height: 21px;
  flex-wrap: wrap;
}

ul {
  margin: 0;
  list-style-type: none;
  font-size: 14px;
  line-height: 21px;
  padding: 0px;
}

.address {
  display: flex;
}

.address_item {
  display: flex;
  font-size: 14px;
  align-items: center;
  flex-wrap: wrap;
}

.address_item:not(:first-child) {
  margin-left: 54px;
}

.address_item_text {
  margin: 0;
  margin-left: 10px;
}

.image {
  width: 14px;
  height: 14px;
}

@media screen and (min-width: 321px) and (max-width: 1215px) {
  .footer {
    height: auto;
  }
  .address {
    flex-direction: column;
    width: 100%;
    justify-content: center;
    align-items: center;
  }
  .address_item:not(:first-child) {
    margin-left: 0px;
  }
}
</style>
