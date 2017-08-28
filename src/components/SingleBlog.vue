<template>
	<div id="single-blog">
		<h1>{{blog.title}}</h1>
		<article>{{blog.content}}</article>
		<p>作者: {{blog.author}}</p>
		<p>分类:</p>
		<ul>
			<li v-for="category in blog.categories">
				{{category}}
			</li>
		</ul>
	</div>
</template>

<script>
	export default{
		name:"single-blog",
		data(){
			return{
				id:this.$route.params.id,
				blog:{}
			}
		},
		created(){
			this.$http.get('https://myfeels-52480.firebaseio.com/posts/' + this.id + ".json")
				.then(function(data){
					console.log(data);
					return data.json();
					// this.blog = data.body;
				})
				.then(function(data){
					this.blog = data;
				})
		}
	}
</script>
<style>
	#single-blog{
		max-width: 1040px;
		margin: 20px auto;
		padding: 20px;
		background: #eee;
		border: 1px dotted #aaa;
		box-sizing: border-box;
	}
	#single-blog ul li {
		list-style: none;
		display: inline;
	}
</style>