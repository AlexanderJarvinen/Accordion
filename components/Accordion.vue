<template>
  <div class="accordion" id="accordion">
    <div class="accordion-item"  v-for="item of content" :key="item.title">
      <h3 class="accordion-item-head" @click="switchAccordion">
        {{item.title}}
      </h3>
      <div class="accordion-item-body">
         Кто, по-вашему, этот мощный старик? Не говорите, вы не можете этого знать. Это — гигант мысли, отец русской демократии и особа, приближенная к императору.
      </div>
    </div>
  </div>
</template>

<script>
    export default {
      name: "Accordion",
      props: {
          content: Array
      },
        methods: {
          switchAccordion: function (event) {
               let matches = document.querySelectorAll('.accordion-item-head');
               for(let i = 0; i < matches.length; i++) {
                   matches[i].classList.remove('active');
                }

            event.target.classList.toggle('active');
          }
      }
    }
</script>

<style scoped>
  .accordion {
    width: 400px;
    border-top: 2px solid #000000;
    border-left: 2px solid #000000;
    border-right: 2px solid #000000;
  }

  .accordion-item{
    cursor: pointer;
    position: relative;
  }

  .accordion-item-head{
    background-color: #526488;
    padding: 20px 0;
    border-bottom: 2px solid #000000;
  }


  .accordion-item-body{
    display: none;
    opacity: 0;
  }

  .accordion-item-head.active + .accordion-item-body {
    display: block !important;
    transition: 1s;
    animation: show 2s 1;
    animation-fill-mode: forwards;
    border-bottom: 2px solid #000000;
  }


  @keyframes show {
    0%{
      height:0;
    }
    40% {
      opacity: 0;
    }
    100% {
      height:100px;
      opacity: 1;
    }
  }

</style>
