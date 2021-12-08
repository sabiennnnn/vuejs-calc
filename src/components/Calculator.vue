<template>
<div class="container">
    <div class='calculator'>
      <div class="display">{{display}}</div>
      <div @click='clear' class="button darker">C</div>
      <div @click='sign' class="button darker">+/-</div>
      <div @click="percent" class="button darker">%</div>
      <div @click='divide' class="button operator">+</div>
      <div @click='append(7)' class="button">7</div>
      <div @click='append(8)' class="button">8</div>
      <div @click='append(9)' class="button">9</div>
      <div @click='multiply' class="button operator">x</div>
      <div @click='append(4)' class="button">4</div>
      <div @click='append(5)' class="button">5</div>
      <div @click='append(6)' class="button">6</div>
      <div @click='substract' class="button operator">-</div>
      <div @click='append(1)' class="button">1</div>
      <div @click='append(2)' class="button">2</div>
      <div @click='append(3)' class="button">3</div>
      <div @click='add' class="button operator">+</div>
      <div @click='append(0)' class="button zero">0</div>
      <div @click='decimal' class="button">.</div>
      <div @click='equal' class="button operator result">=</div>
    </div>
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
      append(number) {
        if (this.operatorClicked === true) {
          this.display = '';
          this.operatorClicked = false;
        } this.display = this.display === 0 
                  ? (this.display = number) 
                  : '' + this.display + number;
      },
      percent() {
        this.display = this.display/100;
      },
      decimal() {
        if (this.display.indexOf('.') === -1) {
          this.append('.');
        }
      },
      divide() {
        this.operator = (a, b) => a / b;
        this.previous = this.display;
        this.operatorClicked = true;
      },
      multiply() {
        this.operator = (a, b) => a * b;
        this.previous = this.display;
        this.operatorClicked = true;
      },
      substract() {
        this.operator = (a, b) => a - b;
        this.previous = this.display;
        this.operatorClicked = true;
      },
      add() {
        this.operator = (a, b) => a + b;
        this.previous = this.display;
        this.operatorClicked = true;
      },
      equal() {
        this.display = this.operator(Number(this.previous), Number(this.display));
        this.previous = null;
        this.operatorClicked = true; 
      }
    }
  }
</script>

<style scoped>
.container {
  padding-top: 10%
}
.calculator {
  margin: 0 auto;
  width: 400px;
  min-height: 600px;
  max-height: 700px;
  font-size: 2rem;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(100px, auto);
  box-shadow: -3px 3px 15px rgba(17,17,17,0.4);
  line-height: 10vh;
  color:rgb(205, 255, 204) ;
}
.display {
  grid-column: 1 / 5;
  background: #055a5b;
  border-bottom: solid 1px rgb(205, 255, 204)  ;
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
  background: rgb(205, 255, 204) ;
  color: #063341;
  font-weight: 700;
}

.result:active { background-color:rgb(186, 226, 185) }

@media only screen and (min-width: 768px) {
  .calculator {
    width: 42vw;
    grid-auto-rows: minmax(80px, auto);
    line-height: 90px;
  }
}
@media only screen and (min-width: 1024px) {
  .calculator {
    width: 32vw;
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