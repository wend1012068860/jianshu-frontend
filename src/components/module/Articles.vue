<template>
    <div>
      <div class="row" v-for="article in articles" :key="article.articleId">
        <div class="col-md-8">
          <p v-text="article.articleTitle" class="title"></p>
          <p v-text="article.articleContent" class="content"></p>
          <p v-text="article.articleAuthor" class="nickname"></p>
        </div>
        <div class="col-md-4">
          <img v-bind:src="article.articlePic" class="picture"/>
        </div>
      </div>
    </div>
</template>

<script>
    export default {
      data(){
        return{
          articles:[]
        }
      },
      created(){
        var that = this;
        this.$http
          .get('http://localhost:8080/article/hot')
          .then(function (response) {
            // alert(JSON.stringify(response.data.data));
            that.articles = response.data.data;
          })
      },
        name: "Article"
    }
</script>

<style scoped>
.picture{
  width: 130px;
  height: 100px;
}
  .title{
    font-size: 19px;
    font-weight: bold;
  }
  .content{
    font-size: 15px;
    color: grey;
  }
  .nickname{
    font-size: 11px;
    color: darkgray;
  }
</style>
