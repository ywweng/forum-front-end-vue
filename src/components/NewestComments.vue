<template>
  <div class="card">
    <div class="card-header">最新評論</div>
    <div class="card-body" v-for="comment in comments" :key="comment.id">
      <div>
        <h4>
          <router-link
            :to="{
              name: 'restaurant-show',
              params: { id: comment.Restaurant.id },
            }"
          >
            {{ comment.Restaurant.name }}
          </router-link>
        </h4>
        <p>{{ comment.text }}</p>
        by
        <router-link :to="{ name: 'user', params: { id: comment.User.id } }">
          {{ comment.User.name }}
        </router-link>
        {{ comment.createdAt | fromNow }}
        <hr />
      </div>
    </div>
  </div>
</template>

<script>
import { fromNowFilter } from './../utils/mixins'

export default {
  mixins: [fromNowFilter],
  props: {
    comments: {
      type: Array,
      // 因父元件RestaurantsFeeds中有做v-bind，所以應該要帶資料進來
      required: true,
    },
  },
}
</script>
