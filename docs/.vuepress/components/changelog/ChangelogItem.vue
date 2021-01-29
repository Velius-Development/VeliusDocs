<template>
    <tr>
        <td align="right" class="featured-label-container">
            <span class="label" :class="item.tag">
                {{item.tag}}
            </span>
        </td>
        <td class="changelog-text">
        <b>{{item.title}}</b><br>
        {{item.text}}
        </td>
    </tr>
</template>

<script>
export default {
    props: ['item']
}
</script>

<style scoped>

    .image {
    	border-radius: 4px;
    }

    .label-container {
    	width: 84px;
    	vertical-align: top;
    	margin-top: 5px;
    }

    .featured-label-container {
    	width: 80px;
    	vertical-align: top;
    	padding-top: 3px;
    }

    .app-version {
    	color: #8b8c8d; 
    	font-size: 13px; 
    	padding: 0 0 0 4px;
    }

    .label {
    	text-align: center;
    	font-size: 12px; 
    	font-family: Helvetica Neue, Arial, sans-serif;
    	border-radius: 4px; 
    	font-weight: 400; 
    	padding: 2px 5px 1px 5px;
    	text-transform: uppercase;
    }

    .fixed {
        /*background-color: #d4773130;*/
    	border: 1px solid #d47731;
    	color: #d47731;
    }

    .new {
    	/*background-color: #a8dca830;*/
    	border: 1px solid #a8dca8;
    	color: #a8dca8;
    }

    .improved {
    	/*background-color: #4d9ff230; */
    	border: 1px solid #4D9FF2;
    	color: #4D9FF2;
    }

	.removed {
    	background-color: #da5151;
    	border: 1px solid #ab4343;
    }

    .hire {
    	background-color: #D63489; 
    	border: 1px solid #B32A72; 
    }

    .blog {
		/*background-color: #f5eac030;*/
	    border: 1px solid #f5eac0;
	    color: #f5eac0;
    }

    .beta {
    	background-color: #333333; 
    	border: 1px solid #000000; 
    }

    .changelog-text {
    	text-align: left;
    	font-size: 16px; 
    	line-height: 25px; 
    	font-family: Helvetica Neue, Arial, sans-serif;
    	padding-left: 10px;
    }

    .changelog-code {
    	padding: 2px 5px; 
    	background-color: #40328e;
	    color: #c9e4ff;
    	font-family: Monospace, Serif; 
    	border-radius: 4px;
    	font-size: 14px;
    	display: inline-block;
    }

    .changelog-note {
		color: #8b8c8d; 
		font-size: 14px;
    }

    .gray-line {
		padding: 10px 50px 10px 50px; 
		border-top: 1px solid #ACACAC;
    }

    
	table {
		border-spacing: 0 20px;
    }

    tr, td {
        border: none;
        background-color: transparent !important;
    }

</style>