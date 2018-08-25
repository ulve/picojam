<template>
  <section class="container">
    <div>
      <logo/>
      <h1 class="title">
        PicoJam
      </h1>
      <presenter title="Titel" value="Värde" />
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
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

