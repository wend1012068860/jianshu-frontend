<template>
  <div class="container recommend">
    <img class="recommend-banner" src="https://cdn2.jianshu.io/assets/web/recommend-collection-58f8968955ecbeb8f8f3b4cd95ec76be.png">
    <a target="_blank" class="help" href="https://www.jianshu.com/p/9e6397e3e921">
      如何创建并玩转专题
    </a>
    <br>
    <br>
    <br>
    <b-tabs class="zuoxia">
    <b-tab title="推 荐"class="pages">
      <br>
    </b-tab>
    <b-tab title="热 门" class="pages">
      <br>
    </b-tab>
    <b-tab title="城 市" class="pages">
      <br>
    </b-tab>
    <b-tab title="校园" class="pages">
    </b-tab>
    </b-tabs>
    <div class="row" >
      <div class="col-xs-8" v-for="topic in topList" :key="topic.id">
        <div class="collection-wrap">
          <a target="_blank">
            <router-link :to=" '/c/' + topic.id ">
            <img class="avatar-collection" v-bind:src="topic.topicUrl">
            <h4 class="name" v-text="topic.topicName"></h4>
            </router-link>
            <p class="collection-description" v-text="topic.summary"></p>
          </a>
          <a class="btn btn-success follow"><span>关注</span></a>
          <hr>
          <div class="count"><a target="_blank">{{topic.articleCount}}篇文章</a> · {{topic.fans}}K人关注</div>
        </div>
      </div>

  </div>
  </div>
</template>

<script>
    export default {
        name: "Collections",
      data(){
          return{
            text:"",
          topList:[
            {
              "id": 1,
              "topicName": "读书",
              "topicUrl": "//upload.jianshu.io/collections/images/4/sy_20091020135145113016.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/180/h/180",
              "summary": "投稿须知:读书专题仅收录与读书有关的书评、读书笔记...",
              "articleCount": 49535,
              "fans": 1601,
            },
            {
              "id": 2,
              "topicName": "旅行·在路上",
              "topicUrl": "//upload.jianshu.io/collections/images/13/%E5%95%8A.png?imageMogr2/auto-orient/strip|imageView2/1/w/180/h/180",
              "summary": "邂逅一个国家，讲述一座城市，这里有你期待的诗与远方。1.投稿请查看...",
              "articleCount": 104217,
              "fans": 2553,
            },
            {
              "id": 3,
              "topicName": "简书电影",
              "topicUrl": "//upload.jianshu.io/collections/images/21/20120316041115481.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/180/h/180",
              "summary": "欢迎关注公众号简宝玉( 公众号ID : jianshu4321 )后台...",
              "articleCount": 104217,
              "fans": 2553,
            },
            {
              "id": 4,
              "topicName": "手绘",
              "topicUrl": "//upload.jianshu.io/collections/images/283250/%E6%BC%AB%E7%94%BB%E4%B8%93%E9%A2%98.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/180/h/180",
              "summary": "欢迎关注公众号简宝玉( 公众号ID : jianshu4321 )后台...",
              "articleCount": 129044,
              "fans": 1634,
            },
            {
              "id": 5,
              "topicName": "连载小说",
              "topicUrl": "//upload.jianshu.io/collections/images/61/0__15815600_401_00.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/180/h/180",
              "summary": "欢迎关注公众号简宝玉( 公众号ID : jianshu4321 )后台...",
              "articleCount": 162671,
              "fans": 1273,
            },
            {
              "id": 6,
              "topicName": "自然科普",
              "topicUrl": "//upload.jianshu.io/collections/images/76/12.jpg?imageMogr2/auto-orient/strip|imageView2/1/w/180/h/180",
              "summary": "欢迎关注公众号简宝玉( 公众号ID : jianshu4321 )后台...",
              "articleCount": 5412,
              "fans": 1116,
            }

          ]
      }
      }
    }

</script>

<style scoped>
  .recommend {
    position: relative;
    padding: 30px 0 50px;
    text-align: center;
  }
  .pages{
    color: gray;
  }
  .container {
    width: 980px;
    margin-right: auto;
    margin-left: auto;
  }
  .recommend-banner {
    min-height: 78px;
    border-radius: 4px;
    width: 100%;
    background-color: hsla(0,0%,71%,.2);
    vertical-align: middle;
    border: 0;
  }
  .help {
    top: 56px;
    position: absolute;
    right: 30px;
    color: #fff;
  }
  .avatar-collection {
    border-radius: 8px;
    width: 80px;
    height: 80px;
    margin: -40px 0 10px;
    display: inline-block;
    border: 1px solid #ddd;
    background-color: #fff;
    cursor: pointer;
    vertical-align: middle;
  }
  .row {
    margin-left: -15px;
    margin-right: -15px;
  }

  .col-xs-8 {
    width: 33.33333%;
    float: left;
    position: relative;
    min-height: 1px;
    padding-left: 15px;
    padding-right: 15px;
  }
  .collection-wrap {
    height: 300px;
    margin-top: 80px;
    padding: 0 20px;
    border: 1px solid #e6e6e6;
    border-radius: 4px;
    background-color: hsla(0,0%,71%,.1);
    -webkit-transition: .2s ease;
  }
  .btn {
    width: 100px;
    padding: 8px 0;
  }
  .follow {
    border-color: #42c02e;
    font-size: 16px;
    font-weight: 400;
    line-height: normal;
  }
  .btn-success {
    border-radius: 40px;
    color: #fff;
    background-color: #42c02e;
    border-color: #42c02e;
  }
  .btn {
    display: inline-block;
    margin-bottom: 0;
    font-weight: 400;
    text-align: center;
    vertical-align: middle;
    -ms-touch-action: manipulation;
    touch-action: manipulation;
    cursor: pointer;
    background-image: none;
    border: 1px solid transparent;
    white-space: nowrap;
    user-select: none;
  }
  .count {
    font-size: 14px;
  }
</style>
