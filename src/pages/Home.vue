<template>
  <div class="page">
    <div class="page-bg"/>
    <div class="tiles">
      <div class="tile main">
        <breadcrumbs/>
        <article-block/>
      </div>
      <news-block/>
    </div>
  </div>
</template>

<script>
import News from '@/components/News.vue'
import Breadcrumbs from '@/components/Breadcrumbs.vue'
import Article from '@/components/Article.vue'

export default {
  name: 'Home',
  components: {
    'news-block': News,
    'breadcrumbs': Breadcrumbs,
    'article-block': Article,
  },
  data () {
    return {

    }
  }
}
</script>

<style scoped>

</style>
