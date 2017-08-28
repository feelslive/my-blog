<template>
	<nav>
		<ul>
			<li>
				<router-link to="/" exact>我的博客</router-link>
				<router-link to="/add" exact>添加博客</router-link>
			</li>
		</ul>
	</nav>
</template>

<script>
	export default{
		name:"blog-header"
	}
</script>

<style scoped>
ul{
	list-style-type: none;
	text-align: center;
	margin: 0;
}
li{
  display: inline-block;
  margin: 0 10px;
}

a{
  color: #fff;
  text-decoration: none;
  padding: 12px;
  border-radius: 5px;
}
nav{
	max-width: 1040px;
	background: #666;
	padding: 30px 0;
	margin: 0 auto;
	box-sizing: border-box;
	/*margin-bottom: 40px;*/
}

.router-link-active{
	background: rgba(255,255,255,0.8);
	color: #444;
}

</style>