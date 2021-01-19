<template>
  <Layout>
    <div class="project">
      <div class="container">
        <div class="project-header">
          <h1 class="project-title">Pineapple</h1>
          <div class="project-info">
            <div class="categories-container">
              <div class="categories">
                <span class="label">Categories</span>
                <span class="category" v-for="item in $page.post.categories" :key='item.id'>{{item.title}}&nbsp;&nbsp;</span>
              </div>
            </div>
            <div class="year-container">
              <span class="label">Year</span>
              <div>{{$page.post.year}}</div>
            </div>
          </div>
        </div>
        <div class="content">
          <p v-html="mdToHtml($page.post.content)">
            <!-- <img
              class="g-image g-image--lazy g-image--loaded"
              :src="'http://localhost:1337'+$page.post.cover.url"
              width="2560"
            /> -->
          </p>
        </div>
      </div>
    </div>
  </Layout>
</template>
<page-query>
   query($id:ID!) {
		post:strapiPost(id:$id) {
            id
            content
            title
            year
            categories {
                id
                title
                color
            }
		}
	} 
</page-query>
<script>
import MarkdownIt from 'markdown-it'
const md = new MarkdownIt()
export default {
    name:'detail',
    methods:{
        mdToHtml(markdown){
            return md.render(markdown)
        }
    }
}
</script>
<style scoped>
.project-header {
    padding: 20vh 0 4rem;
}
.project-title {
    font-size: 4rem;
    margin: 0 0 4rem;
    padding: 0;
}
.project-info {
    display: flex;
    flex-wrap: wrap;
    font-size: .8rem;
}
.project-info>div {
    margin-right: 4rem;
}
.project-info>div:last-of-type {
    margin: 0;
}
.label {
    display: block;
    font-weight: 700;
    margin-bottom: .5rem;
}
</style>
