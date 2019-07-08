<template>
  <div>

      <h3>Если случайное число четное - промис вернет рыбий текст,
        если нечетное - будет ошибка!</h3>
      <h2>Случайное число {{randomNumber}}</h2>
    <div class="wrapper">
      <div class="accordion" id="accordion">
        <div class="accordion-item"  v-for="item of content" :key="item.title">
          <h3 class="accordion-item-head" @click="switchAccordion">
            {{item.title}}
          </h3>
          <div class="accordion-item-body">
            {{contentText}}
          </div>
        </div>
      </div>
    </div>
    </div>
</template>

<script>
    export default {
      name: "Accordion",
      data () {
        return {
          contentText: "",
          randomNumber: 0
        }
      },
      props: {
          content: Array
      },
        methods: {
          switchAccordion: async function (event) {
               this.contentText = "Ошибка запроса!";
               let matches = document.querySelectorAll('.accordion-item-head');

               Object.keys(matches).map((i) => {
                 matches[i].classList.remove('active');
               });

                event.target.classList.toggle('active');

            let randomNumber = Math.floor(Math.random() * (100 - 1 + 1)) + 1;

            this.randomNumber = randomNumber;

            let promise = new Promise((resolve, reject) => {
              setTimeout(() => {
                if ( randomNumber%2 == 0 ) {
                  resolve("Lorem ipsum dolor sit amet, consectetuer adipiscing elit. ")
                } else {
                   reject(
                     alert("Ошибка запроса!")
                 )
                }
              }, 1000)
            });

            let result = await promise;

            this.contentText = result;
          }
      }
    }
</script>

<style scoped>
  .wrapper {
    display: flex;
    flex-direction: row;
    justify-content: center;
    padding-top: 40px;
  }

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
      padding: 0;
    }
    40% {
      opacity: 0;
    }
    100% {
      height:80px;
      opacity: 1;
      padding: 20px;
    }
  }

</style>
