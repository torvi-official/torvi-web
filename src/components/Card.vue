<template>
  <div class="custom-card">
    <div class="poster">
      <img :src="image" alt="">
      <img :src="image" alt="">
    </div>
    <div class="group">
      <div class="title">{{ truncate(title, 20) }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    title: {
      type: String,
      default: () => '',
    },
    image: {
      type: String,
      default: () => '',
    },
    detail: {
      type: String,
      default: () => '',
    },
    rank: {
      type: Number,
      default: () => 0,
    },
  },
  methods: {
    truncate(text, limit = 20) {
      const str = text.slice(0, limit);
      return text.length > limit ? `${str}...` : str;
    },
  },
};
</script>

<style scoped>
.custom-card {
  width: 230px;
  display: block;
  box-sizing: border-box;
  padding: 1rem;
  color: #232329;
}

.custom-card .poster {
  position: relative;
}

.custom-card .poster img:first-child {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100%;
  filter: blur(30px);
  opacity: .5;
}

.custom-card .poster img:last-child {
  width: 100%;
  position: relative;
  z-index: 1;
  border-radius: 10px;
  display: block;
}

.custom-card .group {
  width: 100%;
  text-align: center;
  padding-top: 1rem;
}

.custom-card .title {
  font-size: 18px;
}
</style>
