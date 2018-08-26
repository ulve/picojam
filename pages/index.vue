<template>
  <div class="container">
    <div>
      <h1 class="title">PicoJam</h1>
      
      <presenter title="Genre" :value="v1" @presented="t1Presented" color="#F00"/>      
      <transition name="t2" enter-active-class="animated tada">
        <presenter v-if="t2Enabled" title="Tema" :value="v2" @presented="t2Presented" color="#0F0"/>
      </transition>
      <transition name="t2" enter-active-class="animated tada">
        <presenter v-if="t3Enabled" title="Quirk" :value="v3" color="#00F"/>   
      </transition>
  </div>
  </div>

</template>

<script>
import Presenter from "~/components/Presenter.vue";

function seddedRnd() {
  /* Here is where you configure the event. Should perhaps be through url */
  const eventStart = new Date("September 1, 2010 00:00:00");
  const eventStop = new Date("September 2, 2010 23:59:99");
  const currentDate = new Date().setHours(1, 0, 0, 0);
  let seed = currentDate;
  if (currentDate > eventStart && currentDate < eventStop) {
    seed = eventStart;
  }
  const x = Math.sin(seed) * 10000;

  return x - Math.floor(x);
}

export default {
  components: {
    Presenter
  },
  data: function() {
    return {
      t2Enabled: false,
      t3Enabled: false
    };
  },
  methods: {
    t1Presented: function() {
      this.t2Enabled = true;
    },

    t2Presented: function() {
      this.t3Enabled = true;
    }
  },
  beforeMount: function() {
    const genres = [
      "Rollspel",
      "Simulator",
      "JRPG",
      "Plattform",
      "Shooter",
      "Survival",
      "Rythm",
      "Stealth",
      "Beat 'em up",
      "Horror",
      "Tactical RPG",
      "4X",
      "Sport",
      "Racing"
    ];

    const themes = [
      "mörker och ljus",
      "dimma",
      "att vara rolig",
      "vind",
      "förr och nu",
      "sjunker",
      "upp och ner",
      "grader och vinklar",
      "sand",
      "switch",
      "kopplingar",
      "städer och landsbygd",
      "upp",
      "råvarubrist"
    ];

    const quirks = ["inget rött", "går ej att backa", "risk att bli blind"];

    this.v1 = genres[Math.floor(seddedRnd() * genres.length)];
    this.v2 = themes[Math.floor(seddedRnd() * themes.length)];
    this.v3 = quirks[Math.floor(seddedRnd() * quirks.length)];
  }
};
</script>

<style>
body {
  background: url("~/assets/bg.png");
  background-repeat: no-repeat;
  background-size: cover;
}
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Press Start 2P", cursive;
  display: block;
  font-weight: 300;
  font-size: 82px;
  color: #35495e;
  letter-spacing: 1px;
}

@media only screen and (min-device-width: 300px) and (max-device-width: 700px) {
  .title {
    font-family: "Press Start 2P", cursive;
    display: block;
    font-weight: 300;
    font-size: 40px;
    color: #35495e;
    letter-spacing: 1px;
  }
}
</style>
