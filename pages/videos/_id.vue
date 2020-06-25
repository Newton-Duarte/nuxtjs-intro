<template>
  <div>
    <nuxt-child :video="video" />
  </div>
</template>

<script>
import { mapState } from 'vuex';
export default {
  head() {
    return {
      title: '',
      titleTemplate: `%s ${this.video.name} - Vue Screencasts`
    }
  },
  async fetch({$axios, params, store}) {
    let response = await $axios.get(`https://jsonplaceholder.typicode.com/users/${params.id}`);
    let video = response.data;

    store.commit('SET_CURRENT_VIDEO', video);
  },
  computed: {
    ...mapState({
      video: 'currentVideo'
    })
  }
}
</script>

<style>

</style>