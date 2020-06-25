<template>
  <div>
    <h1>Videos</h1>
    <div v-for="video in $store.state.videos" :key="video.id">
      <nuxt-link :to="`/videos/${video.id}`">{{ video.name }}</nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  head: {
    title: 'Vue Screencasts - Video List'
  },
  async fetch({$axios, store}) {
    let response = await $axios.get('https://jsonplaceholder.typicode.com/users');
    let videos = response.data;

    store.commit('SET_VIDEOS', videos);
  }
}
</script>

<style>

</style>