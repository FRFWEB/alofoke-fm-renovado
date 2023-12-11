<script setup>
import { defineComponent, defineProps } from "vue";

defineComponent({
  name: "SocialNetworks",
});

const props = defineProps({
  networks: {
    type: Array,
  },
});

const modeDisc = () => {
  let getDocumentBody = document.querySelector("body");
  let getButton = document.querySelector("#mode_disc");
  if (getDocumentBody.classList.contains("mode-disc") == false) {
    getDocumentBody.style.backgroundColor = "";
    getDocumentBody.classList.add("mode-disc");
    getButton.innerHTML = "DESACTIVAR MODO DISCO";

    //CREATE STARTS LIST
    let createImgStars1 = document.createElement("img");
    createImgStars1.setAttribute("src", require("@/assets/stars/star1.png"));

    let createImgStars2 = document.createElement("img");
    createImgStars2.setAttribute("src", require("@/assets/stars/star2.png"));

    let createImgStars3 = document.createElement("img");
    createImgStars3.setAttribute("src", require("@/assets/stars/star3.png"));

    let createImgStars4 = document.createElement("img");
    createImgStars4.setAttribute("src", require("@/assets/stars/star4.png"));

    let createDivStars = document.createElement("div");
    createDivStars.classList.add("stars");

    //ADD STAR IMAGES
    createDivStars.appendChild(createImgStars1);
    createDivStars.appendChild(createImgStars2);
    createDivStars.appendChild(createImgStars3);
    createDivStars.appendChild(createImgStars4);
    //OUTPUT IN BODY
    getDocumentBody.appendChild(createDivStars);

    return;
  }

  if (getDocumentBody.classList.contains("mode-disc") == true) {
    getDocumentBody.classList.remove("mode-disc");
    getDocumentBody.style.backgroundColor = "#000";
    getButton.innerHTML = "ACTIVAR MODO DISCO";

    let getDivStars = document.querySelector(".stars");
    getDivStars.remove();
    return;
  }
};
</script>

<template>
  <div class="2xl:w-5/12 xl:w-5/12 lg:w-3/5 md:w-4/5 sm:w-11/12">
    <div class="flex flex-row external-links gap-5 my-4">
      <div
        v-for="(item, index) in props.networks"
        :key="index"
        class="2xl:basis-1/2 xl:basis-1/2 lg:basis-1/2 md:flex-1 sm:flex-1 shadow-lg"
      >
        <a
          :href="item.url"
          :class="[item.bg_network, item.text_color_network]"
          class="w-full block py-1 rounded-xl text-aton text-2xl"
          target="_blank"
        >
          <div class="flex flex-row text-center items-center gap-7 px-4">
            <div>
              <span class="text-4xl"><i :class="item.icon"></i></span>
            </div>
            <div>
              <p class="text-2xl">{{ item.title }}</p>
            </div>
          </div>
        </a>
      </div>
    </div>
    <div class="flex flex-row">
      <div class="flex-1 btn-mode-disc">
        <button
          type="button"
          @click="modeDisc()"
          id="mode_disc"
          class="bg-white shadow-lg text-center text-dark w-full text-lg rounded-xl px-4 py-2 text-aton block"
        >
          ACTIVAR MODO DISCO
        </button>
      </div>
    </div>
  </div>
</template>

<style>
.mode-disc .stars img:nth-child(1) {
  animation: generateBackground 0.8s alternate infinite;
}
.mode-disc .stars img:nth-child(2) {
  animation: generateBackground 1.5s alternate infinite 0.3s;
}
.mode-disc .stars img:nth-child(3) {
  animation: generateBackground 2s alternate infinite 0.3s;
}
.mode-disc .stars img:nth-child(4) {
  animation: generateBackground 2.5s alternate infinite 0.3s;
}

.mode-disc .stars img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  z-index: -1;
  filter: brightness(0.5);
}

@keyframes generateBackground {
  0%,
  40%,
  60%,
  80%,
  100% {
    opacity: 0;
  }
  20%,
  60%,
  80% {
    opacity: 1;
  }
}

@media screen and (min-width: 300px) and (max-width: 767px) {
  .external-links {
    justify-content: center !important;
    flex-wrap: wrap;
  }
  .btn-mode-disc {
    margin-left: 1rem;
    margin-right: 1rem;
  }
}

@media screen and (min-width: 768px) {
  .external-links {
    justify-content: space-between !important;
    flex-wrap: nowrap;
  }
}
</style>
