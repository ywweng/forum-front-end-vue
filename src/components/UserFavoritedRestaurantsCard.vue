<template>
  <div>
    <div class="card">
      <div class="card-header">
        <strong>{{ favoritedRestaurants.length }}</strong> 收藏的餐廳
      </div>
      <div class="card-body">
        <router-link
          :to="{
            name: 'restaurant-show',
            params: { id: restaurant.Favorite.RestaurantId },
          }"
          class="mr-1"
          v-for="restaurant in favoritedRestaurants"
          :key="restaurant.id"
        >
          <img :src="restaurant.image" width="60" height="60" class="avatar" />
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    favoritedRestaurants: {
      type: Array,
      required: true,
    },
  },
}

</script>
