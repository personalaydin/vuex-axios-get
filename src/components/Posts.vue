<template>
  <div class="posts container">
    <div class="card">
      <div class="card-body" v-for="post of posts" :key="post.id">
        <img
          class="card-img-top"
          src="../assets/user-avatar.jpg"
          alt="Vue logo"
        />
        <div class="card-content-area">
          <h3 class="card-title">{{ post.title }}</h3>

          <p class="card-text">
            {{ post.body }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async created() {
    await this.getPostsAsync();
  },
  data() {
    return {
      posts: [],
      errors: [],
    };
  },
  methods: {
    async getPostsAsync() {
      try {
        const response = await this.$axios.get("/posts");

        this.posts = response.data;
      } catch (error) {
        this.errors.push(error);
      }
    },
  },
};
</script>

<style>
.card {
  width: 100% !important;
  padding: 1rem 0;
  background-color: rgb(236, 213, 184);
}

.card-body {
  display: flex;
  flex-direction: row;
  align-items: center;
}

.card-content-area {
}

.card-img-top {
  width: 25%;
}
</style>
