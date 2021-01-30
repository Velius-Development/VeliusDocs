<template>
  <div>
        <div class="featured-title">Changelog</div>

        <changelog-entry v-for="entry in this.$page.frontmatter.entries" :entry="entry"></changelog-entry>
  </div>
</template>

<script>
import ChangelogEntry from './changelog/ChangelogEntry.vue'
export default {
  components: { ChangelogEntry },
    name: "ChangelogPage",
    data() {
        return {
            
        };
    }
}
</script>

<style scoped>

    html{
        background: #2D3142; font-family: 'Raleway', sans-serif;
        color: #bcc9cf;
    }

    body{
    	padding: 10px;
    }

    .featured-container {
    	background-color: #37445a;
    	border-radius: 6px;
    	padding: 18px 20px;
    	margin: 20px;
    	margin-bottom: 30px;
    	margin-left:auto;
    	margin-right:auto;
    	max-width: 700px;
    	min-width: 200px;
	position: relative;
    }

    .featured-title {
    	font-size: 20px; 
    	line-height: 25px; 
    	font-family: Helvetica Neue, Arial, sans-serif; 
    	color: #EF8354;
    	text-transform: uppercase;
    	text-align: center;
    	padding-bottom: 10px;
    }

    ::-webkit-scrollbar {
      display: none;
    }
</style>