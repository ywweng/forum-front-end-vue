<template>
  <div>
    <h2 class="my-4">所有評論：</h2>

    <div v-for="comment in restaurantComments" :key="comment.id">
      <blockquote class="blockquote mb-0">
        <button
          type="button"
          class="btn btn-danger float-right"
          v-if="currentUser.isAdmin"
          @click.prevent.stop="handleDeleteButtonClick(comment.id)"
        >
          Delete
        </button>
        <h3>
          <router-link :to="{ name: 'user', params: { id: comment.User.id } }">
            {{ comment.User.name }}
          </router-link>
        </h3>
        <p>{{ comment.text }}</p>
        <footer class="blockquote-footer">
          {{ comment.createdAt | fromNow }}
        </footer>
      </blockquote>
      <hr />
    </div>
  </div>
</template>

<script>
import { fromNowFilter } from './../utils/mixins'

const dummyUser = {
  currentUser: {
    id: 1,
    name: '管理者',
    email: 'root@example.com',
    image: 'https://i.pravatar.cc/300',
    isAdmin: true,
  },
  isAuthenticated: true,
}

export default {
  name: 'RestaurantComments',
  props: {
    restaurantComments: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      currentUser: dummyUser.currentUser,
    }
  },
  // 本段改為使用mixin
  // filters: {
  //   fromNow(datetime) {
  //     if (!datetime) return '-'
  //     return moment(datetime).fromNow()
  //   },
  // },
  mixins: [fromNowFilter],
  methods: {
    handleDeleteButtonClick(commentId) {
      // TODO:請求API伺服器刪除id為commentId的評論
      // 用emit觸發父層事件 $emit('自訂事件名稱',傳遞的資料)
      this.$emit('after-delete-commit', commentId)
    },
  },
}
</script>
