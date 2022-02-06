<template>
  <div class="card">
    <div class="card-header">
      <strong>{{ followings.length }}</strong> followings (追蹤者)
    </div>
    <div class="card-body">
      <router-link
        :to="{ name: 'user', params: { id: following.id } }"
        class="mr-1"
        v-for="following of followings"
        :key="following.key"
      >
        <img :src="following.image" width="60" height="60" class="avatar" />
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    followings: {
      type: Array,
      required: true,
    },
  },
}
</script>
