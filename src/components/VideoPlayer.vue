<template>
  <div class="container">
    <div class="container-gradient">
      <div class="video-player">
        <timer date-props="December 20, 2019"></timer>
        <div class="video-container">
          <iframe width="1400" height="800" :src="this.activeVideo.youtubeURL" frameborder="0" allow="autoplay=yes; encrypted-media" allowfullscreen></iframe>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Timer from './timer.vue'
export default {
  name: 'VideoPlayer',
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
  }
}
let videos = [
  {
    id: 1,
    title: '18-core iMac Pro Review: Not a Trap!',
    thumbnail:
      'https://i.ytimg.com/vi/jn9mHzXJIV0/hqdefault.jpg?sqp=-oaymwEZCNACELwBSFXyq4qpAwsIARUAAIhCGAFwAQ==&rs=AOn4CLAvJvk4k_UNB9nst4pFP-txM1TLZA',
    youtubeURL: 'https://www.youtube.com/embed/3n1T3HxHd7Y?rel=0,&autoplay=1&mute=1&loop=1&playlist=3n1T3HxHd7Y'
  },
  {
    id: 2,
    title: '18-core iMac Pro Review: Not a Trap!',
    thumbnail:
      'https://i.ytimg.com/vi/jn9mHzXJIV0/hqdefault.jpg?sqp=-oaymwEZCNACELwBSFXyq4qpAwsIARUAAIhCGAFwAQ==&rs=AOn4CLAvJvk4k_UNB9nst4pFP-txM1TLZA',
    youtubeURL: 'https://www.youtube.com/embed/i6pbI9niN4k?rel=0,&autoplay=1&mute=1&loop=1&playlist=i6pbI9niN4k'
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
      background: url('../assets/img/sw2.jpg') center center no-repeat;
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
