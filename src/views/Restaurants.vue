<template>
  <div class="container py-5">
    <NavTabs />
    <RestaurantsNavPills :categories="categories" />
    <h1>餐廳論壇首頁</h1>

    <div class="row">
      <!-- <RestaurantCard /> -->
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>

    <RestaurantsPagination
      v-if="totalPage.length > 1"
      :current-page="currentPage"
      :total-page="totalPage"
      :previous-page="previousPage"
      :next-page="nextPage"
      :category-id="categoryId"
    />
  </div>
</template>

<script>
import NavTabs from './../components/NavTabs.vue'
import RestaurantsNavPills from './../components/RestaurantsNavPills.vue'
import RestaurantCard from './../components/RestaurantCard.vue'
import RestaurantsPagination from './../components/RestaurantsPagination.vue'
const dummyData = {
  restaurants: [
    {
      id: 1,
      name: 'Johathan Jerde V',
      tel: '(557) 395-3396 x572',
      address: '70351 Gleichner Harbor',
      opening_hours: '08:00',
      description: 'Asperiores nam accusamus. Dolorem itaque aut est. ',
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
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 2,
      name: 'Tess Morissette PhD',
      tel: '(317) 047-8293 x6144',
      address: '5805 Clark Neck',
      opening_hours: '08:00',
      description: 'Maiores consequuntur dolor et sunt. Deleniti tenet',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=99.41330214292347',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 3,
      name: 'Wanda Sanford',
      tel: '172-955-4446',
      address: '178 Green Point',
      opening_hours: '08:00',
      description: 'Illo voluptatem aspernatur animi repellendus place',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=9.776075201606904',
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
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 4,
      name: 'Lindsay Rowe',
      tel: '(209) 696-8084',
      address: '36024 Ona Locks',
      opening_hours: '08:00',
      description: 'Aut quo qui impedit sed.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=9.83038759675332',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 5,
      name: 'Idella Satterfield',
      tel: '(926) 063-2120 x581',
      address: '889 Janet Square',
      opening_hours: '08:00',
      description: 'Fuga iure quos id saepe ab itaque odit earum occae',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=36.78451119597441',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      Category: {
        id: 1,
        name: '中式料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 6,
      name: 'Angelina Quitzon I',
      tel: '811.077.2683 x24748',
      address: '1213 Nicklaus Trace',
      opening_hours: '08:00',
      description: 'Voluptatem rem molestiae officia doloribus similiq',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=41.887010361261076',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      Category: {
        id: 1,
        name: '中式料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 7,
      name: 'Berneice Herzog',
      tel: '338-580-2426',
      address: '895 Mae Turnpike',
      opening_hours: '08:00',
      description: 'Quod reiciendis itaque iure voluptas quo nulla pro',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=10.746556012930641',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      Category: {
        id: 1,
        name: '中式料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 8,
      name: 'Zena Kuhn V',
      tel: '183.919.3331',
      address: '4856 Upton Via',
      opening_hours: '08:00',
      description: 'odio',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=87.86589893032648',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      Category: {
        id: 1,
        name: '中式料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 9,
      name: 'Florine McLaughlin DVM',
      tel: '(790) 829-4484 x00755',
      address: '39017 Mohammad Lodge',
      opening_hours: '08:00',
      description: 'Autem eaque sed alias nisi aut facere ipsam ut lab',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=9.756850302612353',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 5,
      Category: {
        id: 5,
        name: '素食料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
    {
      id: 10,
      name: 'Jolie Dibbert',
      tel: '962-209-3272 x73704',
      address: '354 Dare Dam',
      opening_hours: '08:00',
      description: 'Aliquid ipsum laboriosam commodi. Veniam tempora d',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=36.11119470075997',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 2,
      Category: {
        id: 2,
        name: '日本料理',
        createdAt: '2022-01-29T14:03:44.000Z',
        updatedAt: '2022-01-29T14:03:44.000Z',
      },
      isFavorited: false,
      isLiked: false,
    },
  ],
  categories: [
    {
      id: 1,
      name: '中式料理',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
    },
    {
      id: 2,
      name: '日本料理',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
    },
    {
      id: 3,
      name: '義大利料理',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
    },
    {
      id: 4,
      name: '墨西哥料理',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
    },
    {
      id: 5,
      name: '素食料理',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
    },
    {
      id: 6,
      name: '美式料理',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
    },
    {
      id: 7,
      name: '複合式料理',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
    },
  ],
  categoryId: '',
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
}

export default {
  name: 'Restaurants',
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination,
  },
  data() {
    return {
      restaurants: [],
      categories: [],
      categoryId: -1,
      currentPage: 1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1,
    }
  },
  methods: {
    fetchRestaurants() {
      const {
        restaurants,
        categories,
        categoryId,
        page,
        totalPage,
        prev,
        next,
      } = dummyData
      this.restaurants = restaurants
      this.categories = categories
      this.categoryId = categoryId
      this.currentPage = page
      this.totalPage = totalPage
      this.previousPage = prev
      this.nextPage = next
    },
  },
  created() {
    this.fetchRestaurants()
  },
}
</script>
