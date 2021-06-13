<template>
  <div class="flex items-center justify-center">
    <!-- component -->
    <div class="z-10 flex flex-row p-10 bg-white card rounded-3xl">
      <div class="w-3/5 rounded-3xl bg-img">
        <img
          src="../assets/codex-omega.png"
          alt="Music album photo"
          class="object-cover p-3 rounded-3xl"
        />
      </div>
      <div class="flex flex-col px-4 py-6">
        <span class="text-md text-color-1">Now Playing</span>
        <div class="flex flex-col my-auto text-color-2">
          <span class="text-2xl font-extrabold"> Purple Haze</span>
          <span class="font-bold text-md opacity-40">Jimi Hendrix</span>
          <span class="text-sm font-semibold opacity-40">Woodstock</span>
        </div>
        <div class="flex justify-between w-full">
          <button
            class="inline-flex items-center p-2 font-bold rounded-full  bg-img button-shadow focus:outline-none"
          >
            <img src="../assets/like.svg" class="w-4 h-4" />
          </button>
          <button
            class="inline-flex items-center p-2 font-bold rounded-full  bg-img button-shadow focus:outline-none"
          >
            <img src="../assets/playlist.svg" class="w-4 h-4" />
          </button>
          <button
            class="inline-flex items-center p-2 font-bold rounded-full  bg-img button-shadow focus:outline-none"
          >
            <img src="../assets/share.svg" class="w-4 h-4" />
          </button>
        </div>
      </div>
    </div>
    <div class="flex flex-row pl-8 pr-4 -ml-12 bg-white side-card rounded-3xl">
      <div class="flex flex-col p-4 ml-12">
        <div class="flex">
          <button
            class="inline-flex items-center p-2 font-bold rounded-full  focus:outline-none"
          >
            <img src="../assets/shuffle.svg" class="w-4 h-4" />
          </button>
          <button
            class="inline-flex items-center p-2 font-bold rounded-full  focus:outline-none"
          >
            <img src="../assets/repeat.svg" class="w-4 h-4" />
          </button>
          <button
            class="inline-flex items-center font-bold rounded-full  focus:outline-none"
            @click="pre"
          >
            <img src="../assets/playback.svg" class="w-4/5 h-4/5" />
          </button>
          <button class="-mx-6 focus:outline-none" @click="toggleAudio">
            <img :src="image" class="w-4/5 h-4/5" />
          </button>
          <button
            class="inline-flex items-center font-bold rounded-full  focus:outline-none"
            @click="next"
          >
            <img src="../assets/playnext.svg" class="w-4/5 h-4/5" />
          </button>
          <button
            class="inline-flex items-center p-2 font-bold rounded-full  focus:outline-none"
          >
            <img src="../assets/reshuffle.svg" class="w-4 h-4" />
          </button>
          <button
            class="inline-flex items-center p-2 font-bold rounded-full  focus:outline-none"
          >
            <img src="../assets/filter.svg" class="w-4 h-4" />
          </button>
        </div>
        <div class="w-full">
          <div class="w-full h-4 mb-8">
            <input
              type="range"
              min="0"
              max="100"
              value="0"
              id="duration_slider"
              class="w-full"
            />
          </div>
          <div class="flex justify-between w-full">
            <span class="font-normal text-color-1" v-html="elapsedTime()">
              00:00
            </span>
            <span class="font-normal text-color-1" v-html="totalTime()">
              00:00
            </span>
          </div>
        </div>
      </div>
      <span class="w-1 h-16 my-auto ml-8 bg-pink-100 bg-vertical"></span>
      <audio ref="player" class="hidden" id="audio-player">
        <source
          src="https://raw.githubusercontent.com/muhammederdem/mini-player/master/mp3/1.mp3"
          type="audio/mpeg"
        />
      </audio>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      playbtn: require("../assets/playbtn.svg"),
      playpause: require("../assets/playpause.svg"),
      play: false,
    };
  },
  computed: {
    image() {
      return this.play ? this.playbtn : this.playpause;
    },
  },
  methods: {
    toggleAudio() {
      this.play = !this.play;
      var audio = document.getElementById("audio-player");
      if (audio.paused) {
        audio.play();
      } else {
        audio.pause();
      }
    },
    convertTime(seconds) {
      const format = (val) => `0${Math.floor(val)}`.slice(-2);
      var hours = seconds / 3600;
      var minutes = (seconds % 3600) / 60;
      return [minutes, seconds % 60].map(format).join(":");
    },
    totalTime() {
      var audio = this.$refs.player;
      if (this.play) {
        var seconds = audio.duration;
        return this.convertTime(seconds);
      }
    },
    elapsedTime() {
      var audio = this.$refs.player;
      if (audio) {
        var seconds = audio.currentTime;
        return this.convertTime(seconds);
      } else {
        return "00:00";
      }
    },
  },
};
</script>
<style>
.bg-img {
  background-color: #f8f8f8;
}
.bg-vertical {
  background: #e1deea;
  border-radius: 13px;
}
.text-color-1 {
  font-feature-settings: "liga" off;
  color: #aeaeae;
  height: 22px;
  font-family: Roboto;
  line-height: 21px;
  text-shadow: 1px 1px 1px #ffffff;
}
.text-color-2 {
  color: #86748d;
  text-shadow: 1px 1px 1px #ffffff;
}
.bg-like {
  background: linear-gradient(327.56deg, #5f30c1 19.23%, #968ef1 81.76%);
}
.button-shadow {
  box-shadow: -10px -10px 15px #ffffff, 10px 10px 10px rgba(0, 0, 0, 0.05),
    inset 10px 10px 10px rgba(0, 0, 0, 0.05), inset -10px -10px 20px #ffffff;
}
.card {
  box-sizing: border-box;
  box-shadow: 40px 30px 80px rgba(54, 48, 116, 0.3);
}
.side-card {
  box-sizing: border-box;
  box-shadow: 0px 60px 100px rgba(65, 44, 100, 0.3);
}
.playlist-bar {
  background: #dedde3;
  box-shadow: -3px -3px 5px #ffffff, 3px 3px 5px rgba(0, 0, 0, 0.05),
    inset 3px 3px 5px rgba(0, 0, 0, 0.05), inset -3px -3px 5px #ffffff;
  border-radius: 37px;
  background: #dedde3;
}
input[type="range"] {
  height: 35px;
  -webkit-appearance: none;
  margin: 10px 0;
  width: 100%;
}
input[type="range"]:focus {
  outline: none;
}
input[type="range"]::-webkit-slider-runnable-track {
  width: 100%;
  height: 10px;
  cursor: pointer;
  animate: 0.2s;
  box-shadow: 0px 0px 0px #222222;
  background: #5d24d6;
  border-radius: 19px;
  border: 3px solid #dedde3;
}
input[type="range"]::-webkit-slider-thumb {
  box-shadow: 0px 0px 0px #a7aaa7;
  border: 5px solid #ffffff;
  height: 24px;
  width: 24px;
  border-radius: 14px;
  background: #5d24d6;
  cursor: pointer;
  -webkit-appearance: none;
  margin-top: -11px;
}
input[type="range"]:focus::-webkit-slider-runnable-track {
  background: #5d24d6;
}
input[type="range"]::-moz-range-track {
  width: 100%;
  height: 10px;
  cursor: pointer;
  animate: 0.2s;
  box-shadow: 0px 0px 0px #222222;
  background: #5d24d6;
  border-radius: 19px;
  border: 3px solid #dedde3;
}
input[type="range"]::-moz-range-thumb {
  box-shadow: 0px 0px 0px #a7aaa7;
  border: 5px solid #ffffff;
  height: 24px;
  width: 24px;
  border-radius: 14px;
  background: #5d24d6;
  cursor: pointer;
}
input[type="range"]::-ms-track {
  width: 100%;
  height: 10px;
  cursor: pointer;
  animate: 0.2s;
  background: transparent;
  border-color: transparent;
  color: transparent;
}
input[type="range"]::-ms-fill-lower {
  background: #5d24d6;
  border: 3px solid #dedde3;
  border-radius: 38px;
  box-shadow: 0px 0px 0px #222222;
}
input[type="range"]::-ms-fill-upper {
  background: #5d24d6;
  border: 3px solid #dedde3;
  border-radius: 38px;
  box-shadow: 0px 0px 0px #222222;
}
input[type="range"]::-ms-thumb {
  margin-top: 1px;
  box-shadow: 0px 0px 0px #a7aaa7;
  border: 5px solid #ffffff;
  height: 24px;
  width: 24px;
  border-radius: 14px;
  background: #5d24d6;
  cursor: pointer;
}
input[type="range"]:focus::-ms-fill-lower {
  background: #5d24d6;
}
input[type="range"]:focus::-ms-fill-upper {
  background: #5d24d6;
}
</style>
