<script setup>
import { defineComponent, defineProps, onMounted, ref } from "vue";

let frecuencyFake = ref(false);

defineComponent({
  name: "RadioComponent",
});

const props = defineProps({
  img: {
    type: String,
  },
  altName: {
    type: String,
  },
  title: {
    type: String,
  },
});

const fakePlay = () => {
  let playMusic = document.querySelector("#play_music");
  if (playMusic.classList.contains("active")) {
    playMusic.classList.remove("active");
    playMusic.innerHTML = "<i class='fas fa-play-circle'></i>";
    return;
  }
  playMusic.innerHTML = "<i class='fas fa-pause-circle'></i>";
  playMusic.classList.add("active");
  frecuencyFake.value = true;
};

const verify = () => {
  let dateStart, dateEnd;
  let iframe = document.querySelector("iframe");

  iframe.addEventListener("mouseenter", () => {
    dateStart = new Date();
  });

  iframe.addEventListener("mouseleave", () => {
    dateEnd = new Date();
    let duration = (dateEnd - dateStart) / 1000;
    if (duration > 0.8) {
      fakePlay();
    }
  });
};

const fakeFrecuency = () => {
  let frecuencyPlay = document.querySelector("#frecuencyFakePlay");
  let count = 0;
  frecuencyPlay.innerHTML = "";
  let fakeFrecuencyCreate = 0;

  if (window.matchMedia("(min-width: 300px)").matches) {
    fakeFrecuencyCreate = 14;
  }

  if (window.matchMedia("(min-width: 425px)").matches) {
    fakeFrecuencyCreate = 18;
  }

  if (window.matchMedia("(min-width: 768px)").matches) {
    fakeFrecuencyCreate = 25;
  }

  if (window.matchMedia("(min-width: 900px)").matches) {
    fakeFrecuencyCreate = 25;
  }

  if (window.matchMedia("(min-width: 1024px)").matches) {
    fakeFrecuencyCreate = 30;
  }

  if (window.matchMedia("(min-width: 1280px)").matches) {
    fakeFrecuencyCreate = 30;
  }

  if (window.matchMedia("(min-width: 1536px)").matches) {
    fakeFrecuencyCreate = 28;
  }
  while (count < fakeFrecuencyCreate) {
    let height = Math.floor(Math.random() * 75);
    /*   let rgba =
      "rgba(" +
      Math.floor(Math.random() * 255) +
      ", " +
      Math.floor(Math.random() * 255) +
      ", " +
      Math.floor(Math.random() * 255) +
      ", " +
      1 +
      ")"; */
    frecuencyPlay.innerHTML += `
     <div>
      <span style="height:${height}px;  background-color: #000; border: 5px solid #3333; display: block;"></span>
      </div
  `;
    count++;
  }
};

onMounted(() => {
  setInterval(fakeFrecuency, 1000);
});
</script>

<template>
  <div class="2xl:w-2/6 xl:w-5/12 lg:w-3/5 md:w-4/5 sm:w-11/12 title-content">
    <div>
      <h1 class="text-white text-aton text-4xl text-center my-4">
        {{ props.title }}
      </h1>
    </div>
    <div class="flex w-full flex-row" id="radio_content">
      <div class="relative basis-full shadow-lg">
        <div class="flex flex-row bg-white rounded-xl py-4 px-5">
          <div>
            <span class="text-7xl" id="play_music"
              ><i class="fas fa-play-circle"></i
            ></span>
            <iframe
              @load="verify()"
              src="https://dominicanplayers.com/audio-player/1596/1/0"
              frameborder="0"
              class="absolute top-0 cursor-pointer"
            ></iframe>
          </div>
          <div class="mx-5">
            <div
              class="flex flex-row gap-1 h-full items-center"
              id="frecuencyFakePlay"
            ></div>
          </div>
          <div class="box-logo">
            <img
              :src="require(`@/assets/${props.img}`)"
              alt="{{ props.altName}}"
              class="2xl:w-60 xl:w-60 lg:w-60 md:w-56 sm:w-44 h-auto"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.box-logo {
  position: absolute;
  top: -100px;
  right: -200px;
}

iframe {
  left: 14px;
  top: 4px;
  height: 90px;
  width: 70px;
  margin-left: 30px;
  padding: 0;

  opacity: 0;
}

.frecuency {
  background-color: #000;
  border: 5px solid #3333;
  display: block;
}

@media screen and (min-width: 300px) and (max-width: 424px) {
  .box-logo {
    top: -270px;
    right: 90px;
  }
  .box-logo img {
    width: 10rem;
  }
  .title-content {
    margin-left: 1rem;
    margin-right: 1rem;
  }
  .external-links {
    justify-content: center;
  }
}

@media screen and (min-width: 425px) and (max-width: 767px) {
  .box-logo {
    top: -240px;
    right: 95px;
  }
  .box-logo img {
    width: 10rem;
  }
  .title-content {
    margin-left: 1rem;
    margin-right: 1rem;
  }
  .external-links {
    justify-content: center;
  }
}

@media screen and (min-width: 768px) and (max-width: 996px) {
  .box-logo {
    top: -50px;
    right: -70px;
  }
}

@media screen and (min-width: 996px) and (max-width: 1023px) {
  .box-logo {
    top: -50px;
    right: -140px;
  }
}

@media screen and (min-width: 1024px) and (max-width: 1279px) {
  .box-logo {
    top: -75px;
    right: -150px;
  }
}

@media screen and (min-width: 1280px) and (max-width: 1535px) {
  .box-logo {
    top: -78px;
    right: -160px;
  }
}

@media screen and (min-width: 1536px) {
  .box-logo {
    top: -90px;
    right: -160px;
  }
}
</style>
