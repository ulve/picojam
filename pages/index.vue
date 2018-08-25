<template>
  <section class="container">
    <div>
      <!-- <logo/> -->
      <h1 class="title">
        PicoJam
      </h1>
      <presenter title="Genre" value="rollspel" @presented="t1Presented" color="#F00"/>      
          <transition name="t2" enter-active-class="animated tada">
            <presenter v-if="t2Enabled" title="Tema" value="...när monstren kommer" @presented="t2Presented" color="#0F0"/>
          </transition>
          <transition name="t2" enter-active-class="animated tada">
            <presenter v-if="t3Enabled" title="Quirk" value="kan en backa" color="#00F"/>   
          </transition>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Presenter from '~/components/Presenter.vue'

export default {
  components: {
    Logo,
    Presenter
  },
  data: function() {
    return {
      t1: 'Titel t1',
      v1: 'Value v1',
      t2Enabled: false,

      t2: 'Titel t2',
      v2: 'Value v2',
      t3Enabled: false,

      t3: 'Titel t3',
      v3: 'Value v3'
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

