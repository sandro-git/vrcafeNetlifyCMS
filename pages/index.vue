<template>
  <div>
    <li v-for="game of games" :key="game.slug">
      <NuxtLink :to="game.slug">{{ game.title }}</NuxtLink>
    </li>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const games = await $content('game').fetch()

    return {
      games,
    }
  },
  head() {
    return {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' },
      ],
    }
  },
}
</script>
