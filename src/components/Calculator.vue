<template>
  <div class='calculator'>
    <div class="display">{{display}}</div>
    <div @click='clear' class="button darker">C</div>
    <div class="button darker">+/-</div>
    <div @click="percent" class="button darker">%</div>
    <div class="button operator">+</div>
    <div class="button">7</div>
    <div class="button">8</div>
    <div class="button">9</div>
    <div class="button operator">x</div>
    <div class="button">4</div>
    <div class="button">5</div>
    <div class="button">6</div>
    <div class="button operator">-</div>
    <div class="button">1</div>
    <div class="button">2</div>
    <div class="button">3</div>
    <div class="button operator">+</div>
    <div class="button zero">0</div>
    <div class="button">.</div>
    <div class="button operator result">=</div>
  </div>
</template>


<script>
  export default {
    data() {
      return {
        previous: null,
        display: 0,
        operator: null,
        operatorClicked: false
      }
    },
    methods: {
      clear() {
        this.display = 0;
      },
      sign() {
        this.display = this.display < 0 
                ? (this.display = this.display - this.display *2 )
                : (this.display = this.display - this.display *2 );
      },
      // append(number) {
      //   if (this.operatorClicked === true) {}
      // },
      percent() {
        this.display = this.display/100;
      }
    }
  }
</script>

<style scoped>
.calculator {
  margin: 0 auto;
  width: 400px;
  min-height: 600px;
  font-size: 2rem;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(100px, auto);
  box-shadow: -3px 3px 15px rgba(17,17,17,0.4);
  line-height: 10vh;
  color:rgb(239, 71, 111) ;
}
.display {
  grid-column: 1 / 5;
  background: #073B4C;
  border-bottom: solid 1px rgb(239, 71, 111) ;
  font-size: 2.5rem;
  font-weight: 700;
  cursor: default;
  overflow: hidden;
  text-overflow: ellipsis;
  padding: 0 1rem;
  text-align: right;
  padding-right:40px;
}
.zero {
  grid-column: 1 / 3;
}
.button {
  background: #063341;
  cursor: pointer;
}

.button:active {
  outline:none;
  box-shadow: inset 0px 0px 5px #00000080; 
  -moz-box-shadow: inset 0px 0px 5px #00000080;
  -webkit-box-shadow: inset 0px 0px 5px #00000080;
}
.darker {
  background: #073B4C;
}
.operator {
  background: #073B4C;
  font-weight: 700;
}
.result {
  background: rgb(239, 71, 111) ;
  color: #063341;
  font-weight: 700;
}

.result:active { background-color:rgb(224, 62, 100);}

@media only screen and (min-width: 768px) {
  .calculator {
    width: 42vw;
    grid-auto-rows: minmax(7.5vh, auto);
    line-height: 7.5vh;
  }
}
@media only screen and (min-width: 1024px) {
  .calculator {
    width: 32vw;
    line-height: 14vh;
  }
}
@media only screen and (min-width: 1280px) {
  .calculator {
    width: 25vw;
  }
}
@media only screen and (min-width: 1600px) {
  .calculator {
    width: 20vw;
  }
}
</style>