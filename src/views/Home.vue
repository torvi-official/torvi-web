<template>
  <div class="container-fluid">
    <div class="card-list">
      <router-link
        v-for="item in movies"
        :key="item.id"
        :to="{ name: 'detail', params: { id: item.id } }">
        <card :title="item.title" :image="item.poster_url"></card>
      </router-link>
    </div>
  </div>
</template>

<script>
import Card from '@/components/Card.vue';

export default {
  name: 'Home',
  data() {
    return {
      movies: [],
    };
  },
  components: {
    Card,
  },
  mounted() {
    fetch('http://localhost:3000/movies')
      .then(res => res.json())
      .then((json) => {
        this.movies = json.map(obj => Object.assign(obj, {
          poster_url: `https://image.tmdb.org/t/p/w300_and_h450_bestv2${obj.poster_path}`,
        }));
      })
      .catch(err => console.log(err));
  },
};
</script>

<style scoped>
.card-list {
  width: 100%;
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
}
</style>
