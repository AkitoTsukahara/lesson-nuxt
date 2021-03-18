<template>

</template>

<script>
  export default {
    name: "_id.vue",
    loading: {
      continuous: true
    },
    async asyncData(context) {
      const id = context.params.id
      try {
        const post = await context.app.$http.$get(
          `https://api.nuxtjs.dev/posts/${id}`
        )
        return {post}
      } catch (e) {
        context.error(e)
      }
    },
    mounted() {
      this.$nextTick(() => {
        this.$nuxt.$loading.start()
        setTimeout(() => this.$nuxt.$loading.finish(), 500)
      }),
      window.onNuxtReady(() => {
        console.log('Nuxt.js is ready and mounted')
      })
    }

    // middleware({ store, redirect }) {
    //   // 分解したオブジェクトからキーを取得する
    //   const isAuthenticated = store.state.authenticated
    //   if (!isAuthenticated) {
    //     return redirect('/login')
    //   }
    // }

  }
</script>

<style scoped>

</style>
