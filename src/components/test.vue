<template>
  <div>
    <div v-for="item in lists">
      <input v-if="item.type == 'input'" v-modal type="text" />
      
    </div>
    <div class="video">

      </div> 
      <video width="500" height="400">
        <source src='http://127.0.0.1:8080/02-音视频类-我是一个mp4.mp4'>
      </video>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      lists: []
    };
  },
  mounted() {
    this.lists = [
      {
        tpye: "input",
        name: "name",
        value: ""
      },
      {
        tpye: "input",
        name: "age",
        value: ""
      },
      {
        tpye: "input",
        name: "sex",
        value: ""
      },
      {
        tpye: "input",
        name: "id",
        value: ""
      }
    ];
    this.$nextTick(()=>{
this.initFlash();
    })
    
  },
  methods: {
    initFlash() {
      var SWF_ID = "KwVideo";
      var SWF_NAME = "http://www.kuwo.cn/yy/jsp/webMv/KwVideo.swf?05";
      /**
       * create live swf
       * @param	msg
       */
      function EmbedSWF_SWF(divId, mp4Url) {
        var flashvars = {
          url: mp4Url
        };
        var params = {
          allowFullscreen: "true",
          allowScriptAccess: "always",
          wmode: "transparent" // can cause issues with FP settings & webcam
        };
        var attributes = {
          id: SWF_ID,
          name: SWF_ID
        };
        swfobject.embedSWF(
          SWF_NAME,
          //这里可以设置播放设置播放视频宽高
          divId,
          "685",
          "420",
          "10.0.0",
          "expressInstall.swf",
          flashvars,
          params,
          attributes
        );
      }

      function playflashmv(urlmp4) {
        var html = [];

        html[html.length] = '<div id="videoDiv">';
        html[html.length] =
          `<a href="javascript:playflashmv('${urlmp4}');" class="butm_middle"></a>`;
        html[html.length] = "</div>";
        document.querySelector('.video').innerHTML = html.join("");
        try{
          EmbedSWF_SWF("videoDiv", urlmp4);

        }catch(e){
          console.log(e);
        }
      }
      playflashmv(
        'http://127.0.0.1:8080/02-音视频类-我是一个mp4.mp4'
      );
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
</style>
