<template>
  <div class="container">
    <img src="https://cdn2.jianshu.io/assets/web/recommend-author-03cc8798d5cc3f986e49cbcb2eb63079.png"
         class="bt">
    <p class="rh">如何成为签约作者？</p>
    <div class="down">
      <div class="row">
        <div class="col-md-4" v-for="user in userList" :key="user.userId">
          <b-card class="card">
            <a :href="'/ou/'+ user.userId ">
              <img v-bind:src="user.avatar" class="pic">
              <p class="name">{{user.nickname}}</p>
              <p class="title">{{user.description}}</p>
            </a>
            <b-button size="size" variant="success">关注</b-button><hr>
            <!--<p class="work">{{user.userWork1}}</p>-->
            <!--<p class="work">{{user.userWork2}}</p>-->
            <!--<p class="work">{{user.userWork3}}</p>-->
          </b-card>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
    export default {
        name: "Users",
      data(){
          return{
            userList:[]
          }
      },
      created() {
        var that = this;
        this.$http
          .get('http://localhost:8080/user/hot')
          .then(function (response) {
            // alert(JSON.stringify(response.data.data));
            that.userList = response.data.data;
          })
      }
    }
</script>

<style scoped>
  .work{
    font-size: 13px;
  }
  .bt{
    width: 1080px;
    height: 100px;
  }
  .name{
    font-size: 20px;
    color: black;
  }
  .title{
    color: #3C3C3C;
  }
  .card{
    background-color: #EEEEEE;
    height: 330px;
  }
  .col-md-4 {
    text-align: center;
    float:left;
    margin-top: 80px;
  }
  .rh{
    margin-left: 780px;
    margin-top: -62px;
    color: white;
  }
  .down{
    margin-top: 50px;
  }
  .pic{
    width: 80px;
    height: 80px;
    border-radius: 50%;
    margin-top: -70px;
  }
</style>
