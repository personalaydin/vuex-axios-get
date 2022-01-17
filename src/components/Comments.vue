<template>
  <div class="comments container">
    <div class="card" v-for="comment of comments" :key="comment.id">
      <div class="card-body">
        <h3 class="card-title">{{ comment.name }}</h3>
        <h5 class="card-subtitle mb-2 text-muted">{{ comment.email }}</h5>
        <h6 class="card-subtitle mb-2">{{ comment.id }}</h6>
        <p class="card-text">
          {{ comment.body }}
        </p>
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
      comments: [],
      errors: [],
    };
  },
  methods: {
    async getPostsAsync() {
      try {
        const response = await this.$axios.get("/comments");
        this.comments = response.data;
      } catch (error) {
        this.errors.push(error);
      }
    },
  },
};
</script>

