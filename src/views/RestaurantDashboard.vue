<template>
  <div class="container py-5">
    <div>
      <h1>{{ restaurant.name }}</h1>
      <span class="badge badge-secondary mt-1 mb-3">
        {{ restaurant.categoryName }}
      </span>
    </div>

    <hr />

    <ul>
      <li>評論數： {{ restaurant.commentsLength }}</li>
      <li>瀏覽次數： {{ restaurant.viewCounts }}</li>
    </ul>

    <button type="button" class="btn btn-link" @click="$router.back()">
      回上一頁
    </button>
  </div>
</template>

<script>
const dummyData = {
  restaurant: {
    id: 1,
    name: 'Johathan Jerde V',
    tel: '(557) 395-3396 x572',
    address: '70351 Gleichner Harbor',
    opening_hours: '08:00',
    description:
      'Asperiores nam accusamus. Dolorem itaque aut est. Fugiat in omnis expedita est accusantium natus.\n \rEum molestiae id recusandae mollitia consequatur nesciunt voluptates. Fugit at autem. Doloremque minima aspernatur. Facilis quidem autem ad quod. Et dignissimos repellat nihil enim et aliquam accusantium dolorum.\n \rIusto aliquam beatae dignissimos et ut voluptatum. Debitis laborum rerum possimus est. Atque doloremque iure.',
    image:
      'https://loremflickr.com/320/240/restaurant,food/?random=40.77230905171263',
    viewCounts: 0,
    createdAt: '2022-01-29T14:03:44.000Z',
    updatedAt: '2022-01-29T14:03:44.000Z',
    CategoryId: 4,
    Category: {
      id: 4,
      name: '墨西哥料理',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
    },
    Comments: [
      {
        id: 1,
        text: 'Vero et est est sed accusantium consequatur iusto ipsa.',
        UserId: 3,
        RestaurantId: 1,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        User: {
          id: 3,
          name: 'user2',
          email: 'user2@example.com',
          password:
            '$2a$10$JPhaLC4JdTUH08gPRSI07esdEadoY7t1e0GGytt05hqfVeQBiNJ5i',
          isAdmin: false,
          image: null,
          createdAt: '2022-01-29T14:03:44.000Z',
          updatedAt: '2022-01-29T14:03:44.000Z',
        },
      },
      {
        id: 51,
        text: 'Aliquid ratione est et quia perspiciatis et.',
        UserId: 3,
        RestaurantId: 1,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        User: {
          id: 3,
          name: 'user2',
          email: 'user2@example.com',
          password:
            '$2a$10$JPhaLC4JdTUH08gPRSI07esdEadoY7t1e0GGytt05hqfVeQBiNJ5i',
          isAdmin: false,
          image: null,
          createdAt: '2022-01-29T14:03:44.000Z',
          updatedAt: '2022-01-29T14:03:44.000Z',
        },
      },
      {
        id: 101,
        text: 'Quisquam totam quae qui quam quo.',
        UserId: 2,
        RestaurantId: 1,
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
        User: {
          id: 2,
          name: 'user1',
          email: 'user1@example.com',
          password:
            '$2a$10$rdYNUx3AFBhT0ACgV9rE1uplKv/1I8THZO0RGx.9kPKTi.oba7pRW',
          isAdmin: false,
          image: null,
          createdAt: '2022-01-29T14:03:44.000Z',
          updatedAt: '2022-01-29T14:03:44.000Z',
        },
      },
    ],
  },
}

export default {
  data() {
    return {
      restaurant: {
        id: -1,
        name: '',
        categoryName: '',
        commentsLength: -1,
        viewCounts: -1,
      },
    }
  },
  methods: {
    fetchRestaurant(restaurantId) {
      console.log(restaurantId)
      const { name, viewCounts } = dummyData.restaurant
      const { name: categoryName } = dummyData.restaurant.Category
      const commentsLength = dummyData.restaurant.Comments.length

      this.restaurant = {
        name,
        categoryName,
        commentsLength,
        viewCounts,
      }
    },
  },
  created() {
    const { id: restaurantId } = this.$route.params
    this.fetchRestaurant(restaurantId)
  },
}
</script>
