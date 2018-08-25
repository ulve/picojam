<template>
  <section class="container">
    <div>
      <h1 class="title">
        PicoJam
      </h1>
      <presenter title="Genre" :value="v1" @presented="t1Presented" color="#F00"/>      
      <transition name="t2" enter-active-class="animated tada">
        <presenter v-if="t2Enabled" title="Tema" :value="v2" @presented="t2Presented" color="#0F0"/>
      </transition>
      <transition name="t2" enter-active-class="animated tada">
        <presenter v-if="t3Enabled" title="Quirk" :value="v3" color="#00F"/>   
      </transition>
    </div>
  </section>
</template>

<script>
import Presenter from '~/components/Presenter.vue'

export default {
  components: {
    Presenter
  },
  data: function() {
    return {
      v1: 'rollspel',
      t2Enabled: false,

      v2: '...när monstren kommer',
      t3Enabled: false,

      v3: '...kan ej backa'
    }
  },
  methods: {
    t1Presented: function() {
      this.t2Enabled = true;
    },

    t2Presented: function() {
      this.t3Enabled = true;
    }
  } 
}
</script>

<style>
body {
  background: url('~/assets/bg.png');
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
  font-family: 'Press Start 2P', cursive;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
</style>