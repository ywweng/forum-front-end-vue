<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">美食達人</h1>
    <hr />
    <div class="row text-center">
      <div class="col-3" v-for="user in users" :key="user.id">
        <a href="#">
          <img :src="user.image" width="140px" height="140px" />
        </a>
        <h2>{{ user.name }}</h2>
        <span class="badge badge-secondary"
          >追蹤人數：{{ user.FollowerCount }}</span
        >
        <p class="mt-3">
          <button
            type="button"
            class="btn btn-danger"
            v-if="user.isFollowed"
            @click.prevent.stop="deleteFollow(user)"
          >
            取消追蹤
          </button>
          <button
            type="button"
            class="btn btn-primary"
            v-else
            @click.prevent.stop="addFollow(user)"
          >
            追蹤
          </button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
const dummyData = {
  users: [
    {
      id: 1,
      name: 'root',
      email: 'root@example.com',
      password: '$2a$10$/pXYqaEE24k4RAfLSItXfuXbDV4bNawnZwie9229hMzPEe/ZbDx3G',
      isAdmin: true,
      image:
        'https://www.yikaojixun.com/uploads/f1434e23c4559c1800d5323987c1c33f.jpg',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 2,
      name: 'user1',
      email: 'user1@example.com',
      password: '$2a$10$rdYNUx3AFBhT0ACgV9rE1uplKv/1I8THZO0RGx.9kPKTi.oba7pRW',
      isAdmin: false,
      image: 'https://inews.gtimg.com/newsapp_match/0/13110670170/0',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 3,
      name: 'user2',
      email: 'user2@example.com',
      password: '$2a$10$JPhaLC4JdTUH08gPRSI07esdEadoY7t1e0GGytt05hqfVeQBiNJ5i',
      isAdmin: false,
      image:
        'https://img.itw01.com/images/2020/02/06/00/2652_apMIiq_8HXAKE9.jpg',
      createdAt: '2022-01-29T14:03:44.000Z',
      updatedAt: '2022-01-29T14:03:44.000Z',
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
  ],
}

import NavTabs from './../components/NavTabs.vue'

export default {
  name: 'UsersTop',
  components: {
    NavTabs,
  },
  data() {
    return {
      users: [],
    }
  },
  methods: {
    fetchUsers() {
      this.users = dummyData.users
    },
    addFollow(user) {
      user.isFollowed = true //改變原有資料
    },
    deleteFollow(user) {
      user.isFollowed = false
    },
  },
  created() {
    this.fetchUsers()
  },
}
</script>
