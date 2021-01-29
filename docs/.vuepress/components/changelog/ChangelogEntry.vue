<template>
      	<div class="featured-container">
		    <table>
                <changelog-item v-for="item in entry.items" :item="item"></changelog-item>

                <div class="changelog-date">
                    {{entry.date}}
                </div>
            </table>
        </div>
</template>

<script>
import ChangelogItem from './ChangelogItem.vue'

export default {
  components: { ChangelogItem },
  props: ['entry'],
}
</script>

<style scoped>
    .changelog-date {
    	text-align: left;
    	font-size: 25px; 
    	line-height: 35px; 
    	font-family: monospace;
    	font-weight: 300; 
    	padding-left: 3px;
    	position: absolute;
      	bottom: 10px;
      	right: 10px;
        background: #37445a;
    }
</style>