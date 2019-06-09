<template>
  <section class="section">
    <div class="video-content">
      <video id="video" height="460" width="620" autoplay style="border-radius: 50px;"></video>
    </div>
  </section>
</template>

<script>
  export default {
    layout: 'login',
    mounted() {
      this.getVideo();
    },
    methods: {
      getVideo() {
        var video = document.getElementById("video");
        if(navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
          // Not adding `{ audio: true }` since we only want video now
          navigator.mediaDevices.getUserMedia({ video: true }).then(function(stream) {
            //video.src = window.URL.createObjectURL(stream);
            video.srcObject = stream;
            video.play();
          });
        }
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');
  .video-content {
    font-family: Roboto, sans-serif;
    border: 2px solid rgba(255, 255, 255, .2);
    border-radius: 50px;
    position: absolute;
    top: 50%;
    left: 50%;
    width: 620px;
    height: 460px;
    margin-left: -310px;
    margin-top: -230px;
    text-align: center;
  }
</style>
