<template>
<div>
    <div class="section-8-bit">
        <div class="wrapper" :style="{ 'background-color': color }">   
            <div>
                <h1 class="title">{{title}}</h1>          
                <transition name="apa" enter-active-class="animated lightSpeedIn">
                    <h2 v-if="presented" :class="{'bounce animated': rerolled, 'value': true}">{{val}}</h2>
                </transition>
                <transition name="apa2" leave-active-class="animated flash">
                    <eight-bit-button v-if="selecting" title="Visa" @clicked="onPresent"/>
                </transition>

                <transition name="apa3" enter-active-class="animated lightSpeedIn" leave-active-class="animated flash">
                  <eight-bit-button v-if="presented && rerolls > 0" title="Njae" @clicked="onReroll"/>
                </transition>
            </div>
        </div>
    </div>
</div>
</template>

<script>
import EightBitButton from "~/components/EightBitButton.vue";
import { setTimeout } from "timers";

export default {
  components: {
    EightBitButton
  },
  props: ["value", "title", "color", "rerolls"],
  data: function() {
    return {
      presented: false,
      selecting: true,
      rerolled: false,
      val: this.value
    };
  },
  watch: {
    value: function(newValue) {
      this.val = newValue;
      this.rerolled = true;
    }
  },
  methods: {
    onPresent: function() {
      this.selecting = false;

      setTimeout(() => {
        this.presented = true;
        setTimeout(() => this.$emit("presented"), 1000);
      }, 1000);
    },
    onReroll: function() {
      this.$emit("reroll");
    }
  }
};
</script>

<style scoped>
@media only screen and (min-device-width: 300px) and (max-device-width: 700px) {
  .title {
    font-family: "Press Start 2P", cursive;
    color: #fafafa;
    font-size: 24px;
  }

  .value {
    font-family: "Press Start 2P", cursive;
    size: 12px;
    color: #fa7dfa;
  }

  .section-8-bit {
    width: 100%;
    float: left;
    border-left: 10px solid #ff6600;
    border-right: 10px solid #ff6600;
    position: relative;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    margin-bottom: 30px;
    width: 300px;
  }

  .section-8-bit .wrapper {
    display: block;
    color: #ff6600;
    padding: 24px;
    margin: -10 px 0;
    border-top: 10px solid #ff6600;
    border-bottom: 10px solid #ff6600;
    height: 138px;
  }

  .section_8bit::before,
  .section_8bit::after,
  .section_8bit .wrapper::before,
  .section_8bit .wrapper::after {
    content: "";
    width: 10px;
    height: 10px;
    display: block;
    position: absolute;
    background: #ff6600;
  }
  .section_8bit::before {
    top: -5px;
    left: -5px;
  }
  .section_8bit::after {
    top: -5px;
    right: -5px;
  }
  .section_8bit .wrapper::before {
    bottom: -5px;
    left: -5px;
  }
  .section_8bit .wrapper::after {
    bottom: -5px;
    right: -5px;
  }
}

@media only screen and (min-device-width: 668px) {
  .title {
    font-family: "Press Start 2P", cursive;
    color: #fafafa;
    font-size: 42px;
  }

  .value {
    font-family: "Press Start 2P", cursive;
    size: 20px;
    color: #fa7dfa;
  }

  .section-8-bit {
    width: 100%;
    float: left;
    border-left: 10px solid #ff6600;
    border-right: 10px solid #ff6600;
    position: relative;
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    margin-bottom: 50px;
    width: 600px;
  }

  .section-8-bit .wrapper {
    display: block;
    color: #ff6600;
    padding: 40px;
    margin: -10px 0;
    border-top: 10px solid #ff6600;
    border-bottom: 10px solid #ff6600;
    height: 200px;
  }

  .section_8bit::before,
  .section_8bit::after,
  .section_8bit .wrapper::before,
  .section_8bit .wrapper::after {
    content: "";
    width: 10px;
    height: 10px;
    display: block;
    position: absolute;
    background: #ff6600;
  }
  .section_8bit::before {
    top: -5px;
    left: -5px;
  }
  .section_8bit::after {
    top: -5px;
    right: -5px;
  }
  .section_8bit .wrapper::before {
    bottom: -5px;
    left: -5px;
  }
  .section_8bit .wrapper::after {
    bottom: -5px;
    right: -5px;
  }
}
</style>
