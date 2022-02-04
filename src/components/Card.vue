<template>
  <div class="card_content">
    <img
      :src="require(`../assets/${item.img}.png`)"
      v-if="!item.sold"
      class="img"
      @click="() => (showModal = true)"
    />
    <img
      v-else
      :src="require(`../assets/${item.img}.png`)"
      class="sold img"
      @click="() => (showModal = true)"
    />
    <template v-if="!item.sold">
      <div class="describe" @click="() => (showModal = true)">
        <p class="describe_item">«{{ item.name }}»</p>
        <p class="describe_item">{{ item.author }}</p>
      </div>
      <div class="buy">
        <div v-if="item.oldPrice" class="price">
          <p class="price_item_old">{{ item.oldPrice }}$</p>
          <p class="price_item_new">{{ item.newPrice }}$</p>
        </div>
        <div v-else class="price">
          <p class="price_item_new">{{ item.newPrice }}$</p>
        </div>
        <button v-if="!inCartValue" class="buy_button" @click="clickHandler">
          {{ text }}
        </button>
        <button v-else class="bought_buttom">✔ В корзине</button>
      </div>
    </template>
    <template v-else>
      <div class="describe" @click="() => (showModal = true)">
        <p class="describe_item sold">«{{ item.name }}»</p>
        <p class="describe_item sold">{{ item.author }}</p>
      </div>
      <div class="buy">
        <p class="sold">Продана на аукционе</p>
      </div>
    </template>
    <template v-if="showModal">
      <div class="modal" @click="() => (showModal = false)">
        <div class="modal_content" @click.stop>
          <div class="image_slider">
            <template v-if="slideToShow === 1">
              <div class="slides_show fade">
                <img :src="require(`../assets/image1.png`)" />
              </div>
            </template>

            <template v-else-if="slideToShow === 2">
              <div class="slides_show fade">
                <img :src="require(`../assets/image2.png`)" />
              </div>
            </template>

            <template v-else-if="slideToShow === 3">
              <div class="slides_show fade">
                <img :src="require(`../assets/image3.png`)" />
              </div>
            </template>
            <div class="slider_buttons">
              <a
                class="prev"
                @click="
                  () => {
                    if (slideToShow === 1) return;
                    slideToShow -= 1;
                  }
                "
                >&#10094;</a
              >
              <a
                class="next"
                @click="
                  () => {
                    if (slideToShow === 3) return;
                    slideToShow += 1;
                  }
                "
                >&#10095;</a
              >
            </div>
          </div>
          <div class="modal_desc">
            <p>Описание:</p>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Sit quo
              reiciendis sunt maxime, rerum deleniti iste ex voluptatibus
              incidunt adipisci! Vitae possimus, odio sequi provident magni aut
              dolores? Reprehenderit, fugiat?
            </p>
          </div>
          <div class="modal_price">
            <p>Цена: {{ item.newPrice }} $</p>
          </div>
        </div>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["item", "index"],
  data() {
    return {
      text: "Купить",
      inCartValue: false,
      showModal: false,
      slideToShow: 1,
    };
  },
  created() {
    this.inCartValue = localStorage.getItem(this.index);
  },
  methods: {
    clickHandler() {
      setTimeout(() => {
        this.text = "Покупается";
        setTimeout(() => {
          localStorage.setItem(this.index, true);
          this.inCartValue = true;
        }, 2000);
      }, 0);
    },
  },
};
</script>

<style>
.card_content {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.sold {
  opacity: 50%;
}

.describe {
  margin-top: 20px;
  color: #343030;
  padding: 0 24px;
  flex: 1 1 auto;
  cursor: pointer;
}
.describe_item {
  margin: 0;
  font-size: 18px;
  line-height: 27px;
}

.img {
  cursor: pointer;
}

.buy {
  display: flex;
  padding: 24px;
  justify-content: space-between;
  align-items: center;
}

.price_item_new {
  margin: 0;
  font-size: 16px;
  line-height: 24px;
}
.price_item_old {
  margin: 0;
  font-size: 14px;
  line-height: 21px;
  color: #a0a0a0;
  text-decoration: line-through;
}

.buy_button {
  font-family: "Merriweather", sans-serif;
  width: 118px;
  height: 48px;
  background-color: #382e2b;
  color: white;
  border: none;
  cursor: pointer;
}

.buy_button:hover {
  background-color: #776763;
}

.bought_buttom {
  font-family: "Merriweather", sans-serif;
  width: 118px;
  height: 48px;
  background-color: #5b3a32;
  color: white;
  border: none;
}

.modal {
  height: 100vh;
  width: 100vw;
  background-color: rgba(0, 0, 0, 0.4);
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}
.modal_content {
  padding: 20px;
  border-radius: 12px;
  background-color: #f6f3f3;
  width: 30vw;
}

.image_slider {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.slider_buttons {
  margin-top: 5px;
}

.prev,
.next {
  cursor: pointer;
  padding: 6px;
  color: #403432;
  font-weight: bold;
  font-size: 18px;
}
.prev:hover,
.next:hover {
  background-color: white;
}

.modal_price {
  font-weight: bold;
}
</style>
