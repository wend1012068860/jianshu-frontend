<template>
  <div>
    <div class="H">
      <span>推荐作者</span>
      <span @click="replace" class="hyp">换一批</span>
    </div>
    <div>
      <div v-for="index in arr" class="row" style="margin-top: 15px">
        <div class="col-md-2">
           <a :href="'/ou/'+ hotUsers[index].userId ">
              <img :src="hotUsers[index].avatar" class="tx">
          </a>
        </div>
        <div class="col-md-8">
          <div>{{hotUsers[index].nickname}}</div>
          <div class="jj">写了{{hotUsers[index].wordsCount}}k字 · {{hotUsers[index].likeCount}}k喜欢</div>
        </div>
        <div class="col-md-2"><span class="gz">关注</span></div>
      </div>

      <div>
        <router-link to="/users">
          <b-button variant="outline-secondary" class="qb">
            查看全部&nbsp;&nbsp;>
          </b-button>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
      name: "Author",
      data() {
        return {
          hotUsers: [],
          arr:[0,1,2,4,5]
        }
      },
      created() {
        var that = this;
        this.$http
          .get('http://localhost:8080/user/hot')
          .then(function (response) {
            // alert(JSON.stringify(response.data.data));
            that.hotUsers = response.data.data;
          })
      },
      methods:{
        replace(){
          var a = [];
          var j= 0;
          while(j<5){
            var b = Math.floor((Math.random()*this.hotUsers.length));
            if(a.indexOf(b)==-1){
              a.push(b);
              j++;
            }
          };
          this.arr = a;
        }
      }

    }

</script>

<style scoped>
  .H{
    width: 280px;
    display: inline-block;
  }
  span{
    color: darkgray;
  }
  .hyp{
    color: darkgray;
    margin-left: 160px;
  }
  .gz{
    color: green;
    font-size: 15px;
    margin-left: -80px;
  }
  .jj{
    color: darkgray;
    font-size: 13px;
  }
  .tx{
    width: 50px;
    height: 50px;
    border-radius: 50%;
  }
  .qb{
    margin-top: 15px;
    width: 270px;
    height: 35px;
  }
  .avatar {
    width: 40px;
    height: 40px;
    float: left;
    border-radius: 20px;
  }

  .follow {
    clear: both;
    float: right;
    margin-top: -30px;
    margin-right: 60px;
    padding: 0;
    font-size: 13px;
    color: #42c02e;
  }
  .author-box {
    clear: both;
    margin-bottom: 10px;
    padding-left: 10px;
  }

  .author-info {
    margin-left: 60px;
    font-size: 11px;
    text-align: left;
    color: #999;
    margin-bottom: 10px;
    padding-right: 20px;
  }
  .view-all {
    background-color: #EFEFEF;
    width: 80%;
    margin-left: 20px;
    height: 30px;
    text-align: center;
    vertical-align: center;
    padding: 1px;
  }
</style>
