<template>
  <div class="tile news">
    <h2 class="tile-header">
      Related News
    </h2>
    <div class="news-block" v-for="(item, key) in news">
      <img :src="require(`@/assets/images/news/${ item.picture }.jpg`)" class="news-pic">
      <div class="news-info">
        <h4 class="title">
          {{ item.title }}
        </h4>
        <div class="description">
          {{ item.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'News',
  data () {
    return {
      news: [
        {
          title: 'Welcome to Nethernite',
          text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt',
          picture: 'nethernite',
        },
        {
          title: 'Welcome to Nethernite',
          text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt',
          picture: 'nethernite',
        },
        {
          title: 'Welcome to Nethernite',
          text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt',
          picture: 'nethernite',
        },
      ]
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
