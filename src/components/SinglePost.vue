<template>
  <div class="post">
    <router-link :to="{ name: 'Detail', params: { id: post.id } }">
      <h3>{{ post.title }}</h3>
    </router-link>
    <p>{{ snippet }}</p>
    <span v-for="tag in post.tags" :key="tag"> #{{ tag }} </span>
  </div>
</template>

<script>
import { computed } from 'vue'
export default {
  name: 'SinglePost',
  props: {
    post: {
      type: Object
    }
  },
  setup(props) {
    const snippet = computed(() => {
      return props.post.body.substring(0, 100) + '...'
    })

    return {
      snippet
    }
  }
}
</script>

<style scoped>
.post {
  margin: 0 40px 30px;
  padding-bottom: 30px;
  border-bottom: 1px solid #e7e7e7;
}
.post h3 {
  display: inline-block;
  font-size: 26px;
  color: blueviolet;
  margin-bottom: 10px;
  max-width: 400px;
}
</style>