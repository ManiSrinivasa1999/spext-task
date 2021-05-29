<template>
  <div class="flex items-center justify-center">
    <!-- component -->
    <div class="bg-white card rounded-3xl p-10 flex flex-row z-10">
      <div class="w-3/5 rounded-3xl bg-img">
        <img
          src="../assets/codex-omega.png"
          alt="Music album photo"
          class="object-cover rounded-3xl p-3"
        />
      </div>
      <div class="flex flex-col py-6 px-4">
        <span class="text-md text-color-1">Now Playing</span>
        <div class="flex flex-col text-color-2 my-auto">
          <span class="font-extrabold text-2xl"> Purple Haze</span>
          <span class="font-bold text-md opacity-40">Jimi Hendrix</span>
          <span class="font-semibold opacity-40 text-sm">Woodstock</span>
        </div>
        <div class="w-full flex justify-between">
          <button
            class="
              bg-img
              font-bold
              button-shadow
              p-2
              rounded-full
              inline-flex
              items-center
              focus:outline-none
            "
          >
            <img src="../assets/like.svg" class="w-4 h-4" />
          </button>
          <button
            class="
              bg-img
              font-bold
              p-2
              rounded-full
              inline-flex
              button-shadow
              items-center
              focus:outline-none
            "
          >
            <img src="../assets/playlist.svg" class="w-4 h-4" />
          </button>
          <button
            class="
              bg-img
              font-bold
              p-2
              button-shadow
              rounded-full
              inline-flex
              items-center
              focus:outline-none
            "
          >
            <img src="../assets/share.svg" class="w-4 h-4" />
          </button>
        </div>
      </div>
    </div>
    <div class="bg-white side-card rounded-3xl pl-8 pr-4 flex flex-row -ml-12">
      <div class="flex flex-col p-4 ml-12">
        <div class="flex">
          <button
            class="
              font-bold
              p-2
              rounded-full
              inline-flex
              items-center
              focus:outline-none
            "
          >
            <img src="../assets/shuffle.svg" class="w-4 h-4" />
          </button>
          <button
            class="
              font-bold
              p-2
              rounded-full
              inline-flex
              items-center
              focus:outline-none
            "
          >
            <img src="../assets/repeat.svg" class="w-4 h-4" />
          </button>
          <button
            class="
              font-bold
              rounded-full
              inline-flex
              items-center
              focus:outline-none
            "
          >
            <img src="../assets/playback.svg" class="w-4/5 h-4/5" />
          </button>
          <button class="-mx-6 focus:outline-none">
            <img src="../assets/playpause.svg" class="w-4/5 h-4/5" />
          </button>
          <button
            class="
              font-bold
              rounded-full
              inline-flex
              items-center
              focus:outline-none
            "
          >
            <img src="../assets/playnext.svg" class="w-4/5 h-4/5" />
          </button>
          <button
            class="
              font-bold
              p-2
              rounded-full
              inline-flex
              items-center
              focus:outline-none
            "
          >
            <img src="../assets/reshuffle.svg" class="w-4 h-4" />
          </button>
          <button
            class="
              font-bold
              p-2
              rounded-full
              inline-flex
              items-center
              focus:outline-none
            "
          >
            <img src="../assets/filter.svg" class="w-4 h-4" />
          </button>
        </div>
        <div class="w-full">
          <div class="h-4 mb-4 w-full">
            <div class="h-2 w-full playlist-bar relative">
              <img
                src="../assets/scroll.svg"
                class="absolute w-8 h-8 -mt-2 -ml-2"
              />
            </div>
          </div>
          <div class="flex justify-between w-full">
            <span class="font-normal text-color-1">2:01:00</span>
            <span class="font-normal text-color-1">4:16:00</span>
          </div>
        </div>
      </div>
      <span class="h-16 bg-vertical w-1 my-auto bg-pink-100 ml-8"></span>
    </div>
  </div>
</template>

<style>
.bg-img {
  background-color: #f8f8f8;
}
.bg-vertical {
  background: #e1deea;
  border-radius: 13px;
}
.text-color-1 {
  font-feature-settings: 'liga' off;
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
</style>
