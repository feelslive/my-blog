<template>
  <div id="add-blog" v-theme:colong="'wide'">
    <h2>添加博客</h2>
    <form v-if="!submmited">
      <label>博客标题</label>
      <input type="text" v-model="blog.title" required placeholder="请输入标题" />

      <label>博客内容</label>
      <textarea v-model="blog.content" placeholder="请输入内容" ></textarea>

      <div id="checkboxes">
        <label>设计UI</label>
        <input type="checkbox" value="设计UI" v-model="blog.categories">
        <label>前端</label>
        <input type="checkbox" value="前端" v-model="blog.categories">
        <label>后端</label>
        <input type="checkbox" value="后端" v-model="blog.categories">
        <label>大数据</label>
        <input type="checkbox" value="大数据" v-model="blog.categories">
      </div>
      <label>作者:</label>
      <select v-model="blog.author">
        <option v-for="author in authors">
          {{author}}
        </option>
      </select>
      <label>原文链接:</label>
      <input type="text" v-model="blog.original" required placeholder="请输入原文链接" />
      <button v-on:click.prevent="post">添加博客</button>
    </form>

    <div v-if="submmited">
      <h3>您的博客发布成功!</h3>
    </div>

    <div id="preview">
      <h3>博客总览</h3>
      <p>博客标题: {{blog.title}}</p>
      <p>博客内容:</p>
      <p>{{blog.content}}</p>
      <p>博客分类:</p>
      <ul>
        <li v-for="category in blog.categories">
          {{category}}
        </li>
      </ul>
      <p>作者: {{blog.author}}</p>
      <p>原文链接: {{blog.original}}</p>
    </div>
  </div>
</template>

<script>
export default {
  // https://jsonplaceholder.typicode.com/
  // https://jsonplaceholder.typicode.com/posts
  name: 'add-blog',
  data () {
    return {
      blog:{
        title:"",
        content:"",
        categories:[],
        author:"",
        original:""
      },
      authors:["本人","其他"],
      submmited:false
    }
  },
  methods:{
    post:function(){
      this.$http.post("https://myfeels-52480.firebaseio.com/posts.json",this.blog)
          .then(function(data){
            console.log(data);
            this.submmited = true;
          });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#add-blog *{
  box-sizing: border-box;
}

#add-blog{
  margin: 20px auto;
  max-width: 600px;
  padding: 20px;
}

label{
  display: block;
  margin: 20px 0 10px;
}

input[type="text"],textarea,select{
  display: block;
  width: 100%;
  padding: 8px;
}

textarea{
  height: 200px;
}

#checkboxes label{
  display: inline-block;
  margin-top: 0;
}

#checkboxes input{
  display: inline-block;
  margin-right: 10px;
}

button{
  display: block;
  margin: 20px 0;
  background: crimson;
  color: #fff;
  border: 0;
  padding: 14px;
  border-radius: 4px;
  font-size: 18px;
  cursor: pointer;
}

#preview{
  padding: 10px 20px;
  border: 1px dotted #ccc;
  margin: 30px 0;
}

h3{
  margin-top: 10px;
}

</style>
