<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">人氣餐廳</h1>

    <hr />
    <div
      class="card mb-3"
      v-for="restaurant in restaurants"
      :key="restaurant.id"
      style="max-width: 540px; margin: auto"
    >
      <div class="row no-gutters">
        <div class="col-md-4">
          <a href="#">
            <img class="card-img" :src="restaurant.image" />
          </a>
        </div>
        <div class="col-md-8">
          <div class="card-body">
            <h5 class="card-title">{{ restaurant.name }}</h5>
            <span class="badge badge-secondary"
              >收藏數：{{ restaurant.FavoriteCount }}</span
            >
            <p class="card-text">
              {{ restaurant.description }}
            </p>
            <router-link
              :to="{
                name: 'restaurant-dashboard',
                params: { id: restaurant.id },
              }"
              :restaurant="restaurant"
              class="btn btn-primary mr-2"
              >Show
            </router-link>
            <button
              type="button"
              class="btn btn-danger mr-2"
              @click.stop.prevent="deleteFavorite(restaurant)"
              v-if="restaurant.isFavorited"
            >
              移除最愛
            </button>
            <button
              type="button"
              class="btn btn-primary"
              @click.stop.prevent="addFavorite(restaurant)"
              v-else
            >
              加到最愛
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from './../components/NavTabs.vue'

const dummyData = {
  restaurants: [
    {
      id: 50,
      name: 'Amos Watsica DVM',
      tel: '405-070-8707 x94722',
      address: '361 Bernier Bridge',
      opening_hours: '08:00',
      description: 'Ea voluptates quia error. Ipsam doloribus aut et q',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=15.462560142937187',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 4,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 49,
      name: 'Dr. Savanna Corwin',
      tel: '862.285.3332 x18047',
      address: '191 Witting Expressway',
      opening_hours: '08:00',
      description: 'Minus a accusantium ea nisi. Omnis voluptate cumqu',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=55.368569709951856',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 48,
      name: 'Camryn Cassin',
      tel: '(301) 879-3648 x345',
      address: '6752 Johnston Creek',
      opening_hours: '08:00',
      description: 'Optio inventore et quo ab.',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=3.7642515000532395',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 4,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 47,
      name: 'Gerhard Jones',
      tel: '781.925.8240 x91233',
      address: '7023 Orlo Locks',
      opening_hours: '08:00',
      description: 'Deleniti dolorem hic. Enim illum doloribus et iure',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=29.887750416729308',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 46,
      name: 'Scarlett Dickinson V',
      tel: '059.781.3123',
      address: '088 Jarvis Causeway',
      opening_hours: '08:00',
      description: 'Nesciunt explicabo quo sit quo molestias ut cum vo',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=18.65723833481725',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 45,
      name: 'Marcelina Lehner',
      tel: '(519) 529-5619 x257',
      address: '1045 Conor Mill',
      opening_hours: '08:00',
      description: 'Consequatur molestias eum reiciendis. Atque adipis',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=50.58640111967381',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 44,
      name: 'Monty Turner',
      tel: '(159) 668-2566 x671',
      address: '5741 Kutch Bridge',
      opening_hours: '08:00',
      description: 'Quia odio error saepe iusto facilis aperiam. Nisi ',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=37.36949906654361',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 43,
      name: 'Ryley Smith',
      tel: '1-599-733-4536 x703',
      address: '0721 Johnson Causeway',
      opening_hours: '08:00',
      description: 'Repudiandae a sapiente voluptatem est sit et conse',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=53.94593295145847',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 1,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 42,
      name: 'Keanu Dare',
      tel: '286.187.9115 x302',
      address: '26045 Mueller Run',
      opening_hours: '08:00',
      description: 'Harum fuga veritatis aut ea blanditiis tempora rer',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=82.17405710295714',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 3,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
    {
      id: 41,
      name: 'Lavina Grady',
      tel: '174-885-6444 x9125',
      address: '311 Theodora Estate',
      opening_hours: '08:00',
      description: 'quo expedita provident',
      image:
        'https://loremflickr.com/320/240/restaurant,food/?random=0.4435475449487969',
      viewCounts: 0,
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      CategoryId: 2,
      FavoritedUsers: [],
      isFavorited: false,
      FavoriteCount: 0,
    },
  ],
}

export default {
  components: {
    NavTabs,
  },
  data() {
    return {
      restaurants: {},
    }
  },
  methods: {
    fetchRestaurants() {
      this.restaurants = dummyData.restaurants
    },
    deleteFavorite(restaurant) {
      restaurant.isFavorited = false
    },
    addFavorite(restaurant) {
      restaurant.isFavorited = true
    },
  },
  created() {
    this.fetchRestaurants()
  },
}
</script>
