<template>
  <div name="hello">
    <ul v-for="post in posts" :key=post.id>
      <li>{{post.title}}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data(){
    return {
      posts: [],
    }
  },
  mounted() {
      let vue = this;
      axios.get('https://jsonplaceholder.typicode.com/posts')
       .then(function (response) {
       // handle success
         vue.posts = response.data;
         console.log(vue.posts)
       })
       .catch(function (error) {
        // handle error
       console.log(error);
       })
       .then(function () {
       // always executed
      });
    },
  props: {
    msg: String
  }
}

//axios.get('https://jsonplaceholder.typicode.com/todos/1')
  //.then(function (response) {
    // handle success
    //console.log(response);
 // })
  //.catch(function (error) {
    // handle error
    //console.log(error);
  //})
 // .then(function () {
    // always executed
  //});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
