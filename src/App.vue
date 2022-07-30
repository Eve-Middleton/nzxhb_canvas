<template>
  <div id="app">

    <div ref="imageTofile" id="chat">
　　<!-- 这里放需要截图的元素,自定义组件元素也可以 -->
<div class="lite-chatbox" id="chatBox">
        <div class="tips">
            <span>2022-7-30 10:00</span>
        </div>
        <div class="cleft cmsg">
            <img class="headIcon radius" ondragstart="return false;"  oncontextmenu="return false;"  src="./assets/xhb.jpg" />
            <span class="name">&nbsp;<span class="htitle admin">提问</span></span>
            <span class="content">
            
              <div>
              这里是投稿内容，下面是投稿图片<br><br><br><br>1</div>
              <!-- <img class="img" src="./assets/xhb.jpg"> -->
              </span>
        </div>
        <div class="cright cmsg">
            <img class="headIcon radius" ondragstart="return false;"  oncontextmenu="return false;"  src="./assets/xhb.jpg" />
            <span class="name">南中小黑板</span>
            <span class="content">板板收到~</span>
        </div>

        
	</div>
  <div class="banner">
          <img src="./assets/xhb_bottom_mini_cut.jpg" width="100%">
<!--           
          <img src="./assets/xhb_bottom.jpg" width="100%"> -->
        </div>
		</div>

    <img :src="htmlUrl"/>
     <button @click="toImage">截取</button>
  </div>
</template>

<script>
import html2canvas from 'html2canvas';


export default {
  name: 'App',
  data() {
　　return {
　　　　htmlUrl: ''
　　}
},

  
  methods:{
　　// 页面元素转图片
　　toImage() {
　　　　// 第一个参数是需要生成截图的元素,第二个是自己需要配置的参数,宽高等
　　　　html2canvas(this.$refs.imageTofile, {
　　　　　　backgroundColor: null
　　　　}).then((canvas) => {
　　　　　　let url = canvas.toDataURL('image/png');
　　　　　　this.htmlUrl = url;
　　　　　　// 把生成的base64位图片上传到服务器,生成在线图片地址
　　　　　　//this.sendUrl();
　　　　})
　　},
  }
}
</script>
<style>
@import './assets/styles/litewebchat.min.css';
</style>
<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#chatBox{
 min-height: 300px!important;
}
 #chat{
  width: 500px;
 
  /* 移除视图内，达到隐藏效果 */
  transform: translateX(-520px);
  background-color: #fff;
}
/* 聊天内图片最大宽度 */
.img{
  max-width: 50%!important
}

</style>
