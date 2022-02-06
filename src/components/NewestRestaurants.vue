<template>
  <div class="card">
    <div class="card-header">最新餐廳</div>
    <div
      class="card-body"
      v-for="restaurant in restaurants"
      :key="restaurant.id"
    >
      <div>
        <h4>
          <router-link
            :to="{ name: 'restaurant-show', params: { id: restaurant.id } }"
          >
            {{ restaurant.name }}
          </router-link>
          <small>{{
            restaurant.Category ? restaurant.Category.name : '未分類'
          }}</small>
        </h4>
        <p>
          {{ restaurant.description }}
        </p>
        {{ restaurant.Category.createdAt | fromNow }}
        <hr />
      </div>
    </div>
  </div>
</template>

<script>
// moment.js套件
import { fromNowFilter } from './../utils/mixins'

export default {
  mixins: [fromNowFilter],
  props: {
    restaurants: {
      type: Array,
      // 因父元件RestaurantsFeeds中有做v-bind，所以應該要帶資料進來
      required: true,
    },
  },
}
</script>

<style scoped>
small {
  font-size: 10px;
}
</style>
