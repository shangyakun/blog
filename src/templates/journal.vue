<template>
  <Layout>
    <div class="project">
      <div class="container">
        <div class="project-header">
          <h1 class="project-title">{{$page.journal.name}}</h1>
          <div class="project-info">
            <div class="categories-container">
              <div class="categories">
                <span class="label">Author</span>
                <div>{{$page.journal.author}}</div>
              </div>
            </div>
            <div class="year-container">
              <span class="label">Date</span>
              <div>{{getDate($page.journal.created_at)}}</div>
            </div>
            <div class="year-container">
              <span class="label">Time</span>
              <div>{{getTime($page.journal.created_at)}}</div>
            </div>
          </div>
        </div>
        <div class="content">
          <p v-html="mdToHtml($page.journal.article)">
          </p>
        </div>
      </div>
    </div>
  </Layout>
</template>
<page-query>
   query($id:ID!) {
        journal:strapiArticles(id:$id) {
            id
            author
            article
            name
            created_at
		}
	} 
</page-query>
<script>
import MarkdownIt from 'markdown-it'
const md = new MarkdownIt()
export default {
    name:'journal',
    methods:{
        mdToHtml(markdown){
            return md.render(markdown)
        },
        getDate(date){
            const d = new Date(date);
            const y = d.getUTCFullYear();
            const m = d.getMonth()+1;
            const day = d.getDate();
            return y +'-'+ m + '-' + day
        },
        getTime(date){
            const d = new Date(date);
            return d.getHours() + ':' + d.getMinutes()
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
.content p{
    line-height: 1.5;
    font-size: 1.15rem;
}

</style>
