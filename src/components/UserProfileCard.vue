<template>
  <div class="card mb-3">
    <div class="row no-gutters">
      <div class="col-md-4">
        <img :src="user.image" width="300px" height="300px" />
      </div>
      <div class="col-md-8">
        <div class="card-body">
          <h5 class="card-title">{{ user.name }}</h5>
          <p class="card-text">{{ user.email }}</p>
          <ul class="list-unstyled list-inline">
            <li>
              <strong>{{ user.Comments.length }}</strong> 已評論餐廳
            </li>
            <li>
              <strong>{{ user.FavoritedRestaurants.length }}</strong>
              收藏的餐廳
            </li>
            <li>
              <strong>{{ user.Followings.length }}</strong> followings (追蹤者)
            </li>
            <li>
              <strong>{{ user.Followers.length }}</strong> followers (追隨者)
            </li>
          </ul>
          <p></p>
          <form>
            <template v-if="isCurrentUser">
              <button type="submit" class="btn btn-primary">Edit</button>
            </template>
            <template v-else>
              <button
                type="button"
                class="btn btn-danger"
                v-if="isFollowed"
                @click.stop.prevent="deleteFollow"
              >
                取消追蹤
              </button>
              <button
                type="button"
                class="btn btn-primary"
                v-else
                @click.stop.prevent="addFollow"
              >
                追蹤
              </button>
            </template>
          </form>
          <p></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    initialUser: {
      type: Object,
      required: true,
    },
    initialIsFollowed: {
      type: Boolean,
      required: true,
    },
    isCurrentUser: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      user: this.initialUser,
      isFollowed: this.initialIsFollowed,
    }
  },
  methods: {
    addFollowing() {
      this.isFollowed = true
    },
    deleteFollowing() {
      this.isFollowed = false
    },
  },
}
</script>
