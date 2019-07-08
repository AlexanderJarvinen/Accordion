<template>
  <div class="accordion" :class="{'is-open': isOpen}">
    <div class="accordion-title" @click="switchAccordion">
      {{title}}
    </div>
    <div class="accordion-body" :class="{'is-open': isOpen}" v-if="isOpen">
      <div class="accordion-body-content">
        <h1>Тело</h1>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: "Accordion",
        data() {
          return {
            isOpen: false,
            title: "Header",
            style: {
              height: 20
            }
          }
        },
        methods: {
          switchAccordion() {
              this.isOpen = ! this.isOpen;
        }
      }
    }
</script>

<style scoped>
  .accordion-title {
    background-color: #526488;
    padding: 20px 0;
    border: 2px solid #000000;
  }
  .accordion {

  }

  .accordion-body {
    padding: 0 16px;
    height:0;
    background-color: darkgray;
    border-color: #000000;
    border-style: solid;
    border-width: 0 2px 2px 2px;


  }

  .accordion-body-content {
    font-size: 1.3rem;
    opacity: 0;
    padding: 25px 0;
  }

  .is-open .accordion-body-content {
    transition: 1s; /*Скорость перехода состояния элемента*/
    animation: show-content 2s 1; /* Указываем название анимации, её время и количество повторов*/
    animation-fill-mode: forwards; /* Чтобы элемент оставался в конечном состоянии анимации */
  }

  .is-open .accordion-body {
    transition: 1s; /*Скорость перехода состояния элемента*/
    animation: show-back 2s 1; /* Указываем название анимации, её время и количество повторов*/
    animation-fill-mode: forwards; /* Чтобы элемент оставался в конечном состоянии анимации */
  }

  @keyframes show-back{
    0%{
      height:0;
    }
    100% {
      height:100px;
    }
  }

  @keyframes show-content{
    50% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

</style>
