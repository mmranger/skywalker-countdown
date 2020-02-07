<template>
  <div class="container">
    <div class="container-gradient">
      <div class="video-player">
         <!-- The Mandalorian release date -->
        <!-- <timer date-props={{ calculateCountdownDay() }}></timer> -->
         <!-- Rise of Skywalker release date -->
        <timer></timer>
        <div class="video-container">
          <!-- <video ref="videoPlayer" class="video-js"></video> -->
          <!-- <vue-core-video-player src="../assets/rise-of-skywalker-1080p.mp4"></vue-core-video-player> -->
          <iframe width="1400" height="800" :src="this.activeVideo.youtubeURL" frameborder="0" allow="autoplay=yes; encrypted-media" allowfullscreen></iframe>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Timer from './timer.vue'
// import videojs from 'video.js'
// import VueCoreVideoPlayer from 'vue-core-video-player'
export default {
  name: 'VideoPlayer',
  props: {
    options: {
      type: Object,
      default () {
        return {}
      }
    }
  },
  mounted () {
    // this.player = videojs(this.$refs.videoPlayer, this.options, function onPlayerReady () {
    //   console.log('onPlayerReady', this)
    // })
  },
  beforeDestroy () {
    if (this.player) {
      this.player.dispose()
    }
  },
  data () {
    return {
      videos,
      activeVideo: videos[0]
    }
  },
  methods: {
    chooseVideo (video) {
      // SET VIDEO AS ACTIVE VIDEO
      this.activeVideo = video
      // INCREASE THE VIDEOS VIEWS BY 1
      video.views += 1
    }
  },
  components: {
    Timer
    // VueCoreVideoPlayer
  }
}
let videos = [
  {
    id: 1,
    title: 'Godzilla vs Kong',
    youtubeURL: 'https://www.youtube.com/embed/msY80njA8Rg?start=1&autoplay=1&mute=1&loop=1&playlist=msY80njA8Rg'
  }
]
</script>
<style scoped>
  body {
      margin: 0;
      padding: 0
  }
  .container {
      width: 100%;
      background: url('../assets/img/gvk.jpg') center center no-repeat;
      background-size: cover;
      background-color: #190206;
      height: 100vh;
      min-height: 100%;
      position: relative;
      overflow: hidden;
  }

  .container-gradient {
      z-index: 0;
      width: 100%;
      height: 100%;
      position: absolute;
      background: -webkit-linear-gradient(top left, rgba(0,0,0,0.3), rgba(0,0,0,0.3));
      background: linear-gradient(top left, rgba(0,0,0,0.3), rgba(0,0,0,0.3));
  }
  /* .video-player{
    display:flex;
    width:1400px;
    margin:auto;
  }
*/
  .video-container{
    display:flex;
    width:1400px;
    margin:4% auto auto auto;
  }
  .row{
      display:flex;
      justify-content:space-between;
  }

  button{
      background:#D0021B;
      color:white;
      border:none;
      padding:10px 20px;
  }
</style>
