<template>
  <div id="app">
    <div ref="imageTofile" id="chat">
      　　<!-- 这里放需要截图的元素,自定义组件元素也可以 -->
      <div class="lite-chatbox" id="chatBox">
        <div class="tips">
          <span>2022-7-30 10:00</span>
        </div>
        <div class="cleft cmsg">
          <img
            class="headIcon radius"
            ondragstart="return false;"
            oncontextmenu="return false;"
            src="./assets/xhb.jpg"
          />
          <span class="name">&nbsp;<span class="htitle admin">提问</span></span>
          <span class="content" id="contenttg">
            <div>学校什么时候开学？短内容测试</div>
            <!-- <img class="img" src="./assets/xhb.jpg"> -->
          </span>
        </div>
        <div class="cleft cmsg">
          <img
            class="headIcon radius"
            ondragstart="return false;"
            oncontextmenu="return false;"
            src="./assets/xhb.jpg"
          />
          <span class="name">&nbsp;<span class="htitle admin">提问</span></span>
          <span class="content" id="contenttg">
            <div>
              一、高度重视核酸检测结果全国互认的重要性。各地区各有关部门要充分认识进一步科学精准做好疫情防控工作的重要性和紧迫性，坚持以人民为中心的发展思想，站在疫情防控“全国一盘棋”的高度，将核酸检测结果全国互认作为高效统筹疫情防控和经济社会发展、切实维护正常生产生活秩序的“关键小事”抓紧抓实，切实便利人员安全有序出行。
              <br />二、不同渠道展示的核酸检测结果具有同等效力。群众通过国务院客户端、国家政务服务平台、各省份健康码、核酸检测机构网站或APP查询到的核酸检测结果及群众持有的纸质核酸检测结果，凡在当地防控政策有效时间内的（以出具报告时间为准），具有同等效力，各地在查验时都应当予以认可，严禁以本地健康码未能查询、未在本地开展核酸检测等为由拒绝通行，拒绝群众进入公共场所、乘坐公共交通工具，不得要求群众重复进行核酸检测。
              <br />三、强化宣传引导和督促落实。各地区要立即行动，将核酸检测结果全国互认的要求落实到基层一线，确保基层管理人员认真执行。各地区要通过公告、新闻报道等多种形式多种途径，加强对核酸检测结果全国互认的宣传解读，让群众知晓，接受群众监督。国务院联防联控机制综合组将会同相关部门加大督促指导力度，对本通知发布后仍不互认、造成不良影响的地方要予以通报。对个人违规使用假冒、篡改等核酸检测结果的，要依法依规处理。
            </div>
            <!-- <img class="img" src="./assets/xhb.jpg"> -->
          </span>
        </div>
        <div class="cright cmsg">
          <img
            class="headIcon radius"
            ondragstart="return false;"
            oncontextmenu="return false;"
            src="./assets/xhb.jpg"
          />
          <span class="name">南中小黑板</span>
          <span class="content">板板收到~</span>
        </div>
      </div>
      <!-- <div class="banner">
        <img src="./assets/xhb_bottom_mini_cut.jpg" width="100%" />
                  
          <img src="./assets/xhb_bottom.jpg" width="100%"> 
      </div> -->
    </div>

    <img :src="htmlUrl" />
    <button @click="toImage">截取</button>
  </div>
</template>

<script>
import html2canvas from "html2canvas";

export default {
  name: "App",
  data() {
    return {
      htmlUrl: "",
    };
  },

  methods: {
    // 页面元素转图片
    toImage() {
      // 第一个参数是需要生成截图的元素,第二个是自己需要配置的参数,宽高等
      html2canvas(this.$refs.imageTofile, {
        backgroundColor: null,
      }).then((canvas) => {
        let url = canvas.toDataURL("image/png");
        this.htmlUrl = url; // 把生成的base64位图片上传到服务器,生成在线图片地址 //this.sendUrl();
      });
    },
  },
};
</script>
<style>
@import "./assets/styles/litewebchat.min.css";
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
#chatBox {
  min-height: 300px !important;
  background-image: url(./assets/bjt.jpg);
  background-size: 100%;
}

.content {
  font-size: 18px !important;
  line-height: 25px !important;
}
#chat {
  width: 500px;

  /* 移除视图内，达到隐藏效果 */
  /* transform: translateX(-520px); */
  /* background-color: #fff; */
  /* background-image: url(./assets/bjt.jpg); */
}
/* 聊天内图片最大宽度 */
.img {
  max-width: 50% !important;
}

#contenttg {
  /* opacity: calc(0.8); */
  background-color: rgba(255, 255, 255, 0.6);
}
</style>
