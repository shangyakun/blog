<template>
  <Layout>
    <div class="container">
      <div class="hero">
        <h1 class="hero-title">Simplicity. Aesthetics. Value.</h1>
        <h2 class="hero-subtitle">
          Hi there, I'm an independent Digital Designer &amp; Art Director focused on
          digital design for brands that like to have fun.
        </h2>
      </div>
      <div class="projects">
        <div class="project" v-for="edge in $page.posts.edges" :key="edge.node.id">
          <g-link :to="'/post/'+edge.node.id" class="project-link">
            <img
              width="2560"
              alt="Banana"
              :src="`${GRIDSOME_API_URL+edge.node.cover[0].url}`"
              class="thumbnail g-image g-image--lazy g-image--loaded"
              sizes="(max-width: 2560px) 100vw, 2560px"
            />
            <h3 class="project-title">{{edge.node.title}}</h3>
            <div class="categories">
              <span class="category" v-for="category in edge.node.categories" :key='category.id'>{{category.title}}</span>
            </div>
          </g-link>
        </div>
      </div>
    </div>
    <div>
      <div class="latest-journals-heading container">
        <span class="label">Latest and greatest</span>
      </div>
      <div class="latest-journals">
        <div class="container">
          	<g-link v-for="item in $page.journal.edges" :to="'/journal/'+item.node.id" :key="item.node.id" class="journal">
		  		<h3 class="journal-title">
              		{{item.node.name}}
            	</h3>
			</g-link>
        </div>
      </div>
    </div>
  </Layout>
</template>
<page-query>
	query {
		posts:allStrapiPost {
			edges {
				node {
					id
					cover {
						url
					}
					title
					categories {
						id
						title
					}
				}
			}
		}
		journal:allStrapiArticles {
			edges {
				node {
					id
					name
				}
			}
		}
	}
</page-query>
<script>
export default {
  	metaInfo: {
    	title: "Hello, world!",
  	},
};
</script>

<style scoped>
.home-links a {
  	margin-right: 1rem;
}

.hero {
  	text-align: center;
  	width: 480px;
  	max-width: 100%;
  	margin: 0 auto;
  	padding: 4rem 0 8rem;
}
.hero-title {
  font-size: 3rem;
  font-weight: 700;
  padding: 0;
  margin: 0 0 2rem;
}
.hero .hero-subtitle {
  font-size: 1.15em;
  font-weight: 400;
  line-height: 1.68;
  opacity: 0.6;
}
.projects {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 4rem;
}
.project {
  grid-column-start: auto;
  grid-column-end: span 2;
  text-align: center;
}
@media (min-width: 920px) {
  .project {
    grid-column-start: auto;
    grid-column-end: span 1;
  }
}
@media (min-width: 920px) {
  .project:nth-child(3n + 1) {
    grid-column-start: auto;
    grid-column-end: span 2;
  }
}
.project-link:hover .g-image{
	transition: all .3s ;
	transform: scale(1.02, 1.02);
}
.project-link .g-image{
	transition: all .3s ;
}
.thumbnail {
  height: 560px;
  object-fit: cover;
  transition: all 0.15s ease;
  box-shadow: 0 0 40px -20px rgba(0, 0, 0, 0.25);
}
.project-title {
  font-size: 1rem;
  color: var(--color-contrast);
  margin: 2rem 0 1rem;
}
.category {
  	font-size: 0.8rem;
	margin-right: .8rem;
  	color: var(--color-contrast-1);
}
.latest-journals-heading {
    margin-top: 6rem;
    margin-bottom: 1rem;
    font-size: .6rem;
    font-weight: 400;
    text-transform: uppercase;
}
.label {
    display: block;
    font-weight: 700;
    margin-bottom: .5rem;
}
.latest-journals {
    max-width: 100%;
    margin: 0 2rem;
    border: 1px solid var(--color-base-1);
}
.latest-journals-heading {
    margin-top: 6rem;
    margin-bottom: 1rem;
    font-size: .6rem;
    font-weight: 400;
    text-transform: uppercase;
}
@media (min-width: 920px){
	.latest-journals { 
		margin: 0;
		border-left: 0;
		border-right: 0;
		border-top: 1px solid var(--color-base-1);
		border-bottom: 1px solid var(--color-base-1);
	}
}
.latest-journals>.container {
    display: flex;
    flex-wrap: wrap;
}
.journal {
    flex: 0 0 100%;
    display: block;
    padding: 2rem;
    transition: background .25s ease;
    text-decoration: none;
    border-bottom: 1px solid var(--color-base-1);
}
.journal-title {
	color: #000;
    font-size: 1rem;
	line-height: 1.35;
}
@media (min-width: 580px){
	.journal:first-child, .journal:nth-child(2) {
		border-bottom: 1px solid var(--color-base-1);
	}
}
@media (min-width: 580px){
	.journal:nth-child(3) {
		border-right: 1px solid var(--color-base-1);
		border-bottom: 0;
		border-bottom-width: 0px;
		border-bottom-style: initial;
		border-bottom-color: initial;
	}
}
@media (min-width: 580px){
	.journal:first-child {
		border-right: 1px solid var(--color-base-1);
	}
}
@media (min-width: 580px){
	.journal {
		flex: 0 0 50%;
	}
}
@media (min-width: 920px){
	.journal {
		flex: 0 0 25%;
	}
}
@media (min-width: 920px){
	.journal:first-child, .journal:nth-child(2), .journal:nth-child(3) {
		border: 0;
		border-right: 1px solid var(--color-base-1);
	}
}
</style>
