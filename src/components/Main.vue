<template>
  <div class="main">
    <div>
      <p class="main_header">Картины эпохи возрождения</p>
    </div>
    <div class="content">
      <div
        v-for="(item, index) in filteredValue"
        class="content_item"
        :key="index"
      >
        <Card :item="item" :index="index" />
      </div>
    </div>
  </div>
</template>

<script>
import Card from "./Card.vue";

export default {
  name: "Main",
  props: ["inputValue"],
  components: {
    Card,
  },
  mounted() {
    this.filteredValue = this.images;
  },

  methods: {
    onUpdate() {
      console.log(this.inputValue);
      if (this.inputValue === "") {
        this.filteredValue = this.images;
        return;
      }
      this.filteredValue = this.images.filter((item) => {
        console.log(item);
        if (
          item.name.includes(this.inputValue) ||
          item.author.includes(this.inputValue)
        )
          return item;
      });
    },
  },
  watch: {
    inputValue: "onUpdate",
  },
  data() {
    return {
      filteredValue: [],
      images: [
        {
          name: "Рождение Венеры",
          author: "Сандро Боттичелли",
          sold: false,
          img: ["image1"],
          oldPrice: "2 000 000 ",
          newPrice: "1 000 000 ",
        },
        {
          name: "Тайная вечеря",
          author: "Леонардо да Винчи",
          img: ["image2"],
          sold: false,
          newPrice: "3 000 000 ",
        },
        {
          name: "Сотворение Адама",
          author: "Микеланджело",
          img: ["image3"],
          sold: false,
          oldPrice: "6 000 000 ",
          newPrice: "5 000 000 ",
        },
        {
          name: "Урок анатомии",
          author: "Рембрандт",
          img: ["image4"],
          sold: true,
          newPrice: "7 000 000 ",
        },
      ],
    };
  },
};
</script>

<style>
.main {
  min-width: 1216px;
  flex: 1 1 auto;
  margin: 0 auto;
  margin-top: 45px;
}

.main_header {
  font-size: 24px;
  font-weight: bold;
  line-height: 36px;
  margin: 0;
}

.content {
  display: flex;
  justify-content: space-between;
  margin-top: 40px;
}

.content_item {
  border: 1px solid #e1e1e1;
  flex-shrink: 1;
}

@media screen and (min-width: 321px) and (max-width: 1215px) {
  .main {
    max-width: 1216px;
    min-width: 0;
    flex: 1 1 auto;
    margin: 0 auto;
    margin-top: 45px;
  }
  .content {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    margin-top: 40px;
  }
  .content_item:not(:last-child) {
    margin-bottom: 10px;
  }
  .main_header {
    text-align: center;
  }
}
</style>
