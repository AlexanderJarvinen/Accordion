<template>
  <section class="container">
    <div>
      <app-logo/>
      <h1 class="title">
        accordion
      </h1>
      <h2 class="subtitle">
        Test task for Ulmart
      </h2>
      <accordion
       :content="content"
      />
    </div>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue'
import Accordion from '~/components/Accordion.vue'

export default {
  components: {
    AppLogo,
    Accordion
  },
  data() {
    return {
      content: [
        {title: "Заголовок №1"},
        {title: "Заголовок №2"},
        {title: "Заголовок №3"},
        {title: "Заголовок №4"}
      ]
    }
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: start;
  align-items: center;
  text-align: center;
  padding-top: 2%;
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

