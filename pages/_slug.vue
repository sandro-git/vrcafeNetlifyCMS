<template>
  <div class="flex bg-gray-900 text-white flex-col items-center">
    <nuxt-link to="/">Acceuil</nuxt-link>
    <h2>{{ game.title }}</h2>
    <nuxt-content :document="game" />
    <img :src="game.image" :alt="game.title" class="h-20 w-auto" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let game
    try {
      game = await $content('game', params.slug).fetch()
      // OR const article = await $content(`articles/${params.slug}`).fetch()
    } catch (e) {
      error({ message: 'Game not found' })
    }

    return {
      game,
    }
  },
}
</script>