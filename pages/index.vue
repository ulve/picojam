<template>
  <div class="container">
    <div>
      <h1 class="title">PicoJam</h1>
      
      <presenter title="Genre" 
                :value="v1" 
                @presented="t1Presented" 
                :rerolls="rerollv1 && rerolls > 0" 
                @reroll="t1Reroll" 
                color="#F00"/>      
      <transition name="t2" enter-active-class="animated tada">
        <presenter v-if="t2Enabled" 
                  title="Tema" 
                  :value="v2" 
                  @presented="t2Presented" 
                  :rerolls="rerollv2 && rerolls > 0" 
                  @reroll="t2Reroll" 
                  color="#0F0"/>
      </transition>
      <transition name="t2" enter-active-class="animated tada">
        <presenter v-if="t3Enabled" 
                  title="Quirk" 
                  :value="v3" 
                  @presented="t3Presented" 
                  :rerolls="rerollv3 && rerolls > 0" 
                  @reroll="t3Reroll" 
                  color="#00F"/>   
      </transition>
  </div>
  </div>

</template>

<script>
import Presenter from "~/components/Presenter.vue";

function seddedRnd() {
  /* Here is where you configure the event. Should perhaps be through url */
  const eventStart = new Date("August 31, 2018 19:00:00");
  const eventStop = new Date("September 2, 2018 23:59:99");
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
      t3Enabled: false,
      v1: "",
      v2: "",
      v3: "",
      rerollv1: true,
      rerollv2: true,
      rerollv3: true,
      rerolls: 1
    };
  },
  methods: {
    t1Presented: function() {
      this.t2Enabled = true;
    },

    t1Reroll: function() {
      this.rerolls--;
      this.rerollv1 = false;
      this.v1 = this.v1reroll;
    },

    t2Presented: function() {
      this.t3Enabled = true;
      this.rerollv1 = false;
    },

    t2Reroll: function() {
      this.rerolls--;
      this.rerollv2 = false;
      this.v2 = this.v2reroll;
    },
    t3Presented: function() {
      this.rerollv2 = false;
    },
    t3Reroll: function() {
      this.rerolls--;
      this.rerollv3 = false;
      this.v3 = this.v3reroll;
    }
  },
  beforeMount: function() {
    const genres = [
      "Rollspel",
      "Simulator",
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
      "Racing",
      "Pussel"
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
      "hundar",
      "kopplingar",
      "städer och landsbygd",
      "rymdvarelser",
      "råvarubrist",
      "1700-talet",
      "alkemi",
      "drakar",
      "enhörningar",
      "valar",
      "konst",
      "arkeologi",
      "arkitektur",
      "flygplan",
      "böcker",
      "städer",
      "konspirationer",
      "matlagning",
      "guld",
      "borgar och slott",
      "döden",
      "detektiver",
      "elektronik",
      "landskap",
      "miljö",
      "mat",
      "eld",
      "evolution",
      "rymden",
      "forskning",
      "mafia",
      "mars",
      "mekanik",
      "förhandlingar",
      "förhistoriskt",
      "fängelse",
      "kryddor",
      "magi",
      "tåg",
      "skatter",
      "vinter",
      "pirater",
      "riddare",
      "svensk film",
      "leksak",
      "djungel"
    ];

    const quirks = [
      "inget rött",
      "går ej att backa",
      "risk att bli blind",
      "permadeath",
      "en knapp",
      "svartvit"
    ];

    this.v1 = genres[Math.floor(seddedRnd() * genres.length)];
    this.v1reroll = genres.filter(g => g != this.v1)[
      Math.floor(seddedRnd() * (genres.length - 1))
    ];

    this.v2 = themes[Math.floor(seddedRnd() * themes.length)];
    this.v2reroll = themes.filter(t => t != this.v2)[
      Math.floor(seddedRnd() * (themes.length - 1))
    ];

    this.v3 = quirks[Math.floor(seddedRnd() * quirks.length)];
    this.v3reroll = quirks.filter(q => q != this.v3)[
      Math.floor(seddedRnd() * (quirks.length - 1))
    ];
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
