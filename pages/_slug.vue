<template>
  <div>
    <h2>{{ game.title }}</h2>
    <nuxt-content :document="game" />
    <pre>{{ game }}</pre>
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