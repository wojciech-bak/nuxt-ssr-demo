<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        ssr-demo
      </h1>
      <div>
        {{ title }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  head() {
    return { title: this.title }
  },

  async asyncData({ $axios }) {
    const response = await $axios.get('https://api.football-data.org/v2/matches', {
      headers: {
        'X-Auth-Token': '384d5cb5e3e64006ac88b1dc20eb1938'
      }
    });
    const match = response.data.matches[0];
    return {
      title: match.homeTeam.name
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
</style>
