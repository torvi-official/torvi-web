<template lang="html">
  <div class="container">
    <div class="detail columns">
      <div class="column is-narrow">
        <div class="poster">
          <img :src="item.poster_url" alt="">
          <img :src="item.poster_url" alt="">
        </div>
      </div>
      <div class="column">
        <h1 class="title is-2">{{ item.title }}</h1>
        <p class="subtitle">{{ item.original_title }}</p>
        <p>{{ item.overview }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Detail',
  data() {
    return {
      item: {},
    };
  },
  mounted() {
    fetch(`http://localhost:3000/movies/${this.$route.params.id}`)
      .then(res => res.json())
      .then((item) => {
        this.item = Object.assign(item, {
          poster_url: `https://image.tmdb.org/t/p/w300_and_h450_bestv2${item.poster_path}`,
        });
      })
      .catch(err => console.log(err));
  },
};
</script>

<style scoped>
.poster {
  position: relative;
  max-width: 300px;
}

.poster img:first-child {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100%;
  filter: blur(30px);
  opacity: .5;
}

.poster img:last-child {
  position: relative;
  width: 100%;
  z-index: 1;
  border-radius: 10px;
  display: block;
}
</style>
