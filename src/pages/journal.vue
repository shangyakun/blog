<template>
  <Layout>
    <div class="container">
      <div class="journal-hero">
        <h1 class="journal-header">a wise person once said...</h1>
      </div>
    </div>
	<g-link v-for="item in $page.journal.edges" :to="'/journal/'+item.node.id" :key="item.node.id" class="journal-post"><div class="container journal">
          <h2 class="journal-title">{{item.node.name}}</h2>
          <p class="journal-excerpt">
            {{item.node.describe}}
          </p>
        </div>
	</g-link>
  </Layout>
</template>
<page-query>
	query {
		journal:allStrapiArticles {
			edges {
				node {
					id
					describe
					name
				}
			}
		}
	}
</page-query>
<script>
export default {
  metaInfo: {
    title: "About us",
  },
};
</script>
<style>
.journal-hero {
  padding: 4rem 0;
  text-align: center;
  color: var(--color-base-1);
}
.journal-post {
    display: block;
    padding: 2rem 0;
    text-decoration: none;
    transition: background .5s ease;
}
.container.journal {
    max-width: 720px;
}
.journal-post:hover{
	background: #f3f3f3;
}
.journal{
	transition: transform .5s ease;
}
.journal-post:hover .journal{
	transform: translate(50px);
    transition: transform .5s ease;
}
.journal-title {
    font-size: 2rem;
    color: var(--color-contrast);
}
.journal-excerpt {
    color: var(--color-contrast-1);
}
@media (min-width: 860px){
	.journal-post {
		padding: 5rem 0;
	}
}
@media (min-width: 560px){
	.journal-post {
		padding: 3rem 0;
	}
}
</style>
