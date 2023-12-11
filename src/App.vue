<template>
  <div>
    <div class="flex w-full h-screen justify-center items-center flex-col">
      <RadioComponent
        img="logo.png"
        altName="alfoke.fm"
        title="ALOFOKE LA RADIO N° 1 DE RD"
      />
      <SocialNetworks :networks="this.networks" />
    </div>
  </div>
</template>

<script>
import RadioComponent from "@/components/Radio.vue";
import SocialNetworks from "@/components/SocialNetworks.vue";
export default {
  name: "App",
  components: {
    RadioComponent,
    SocialNetworks,
  },
  data() {
    return {
      networks: [
        {
          name: "youtube",
          url: "https://www.youtube.com/@Alofokeradioshow",
          icon: "fab fa-youtube",
          bg_network: "bg-red-700",
          text_color_network: "text-white",
          title: "ALOFOKERADIOSHOW",
        },
        {
          name: "tiktok",
          url: "https://www.tiktok.com/@matiasalofoke",
          icon: "fab fa-tiktok",
          bg_network: "bg-white",
          text_color_network: "text-dark",
          title: "MATIASALOFOKE",
        },
      ],
    };
  },
};
</script>

<style>
body {
  background: #000;
}

.text-aton {
  font-family: "Anton", sans-serif;
}
</style>
