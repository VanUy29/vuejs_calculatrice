<template>
  <div class="main-body">
    <div class="container">
      <div class="display">
        <input v-model="screen" id="screen" type="text" placeholder="0" readonly>
      </div>

      <div class="btns">
        <div class="row">
          <button @click="sin">sin</button>
          <button @click="cos">cos</button>
          <button @click="tan">tan</button>
          <button @click="log">log</button>
          <button @click="e">e</button>
        </div>

        <div class="row">
          <button @click="fact">x!</button>
          <button @click="sqrt">√</button>
          <button @click="pow">x <span style="position: relative; bottom: .4em; right: .1em;">y</span>
          </button>
          <button class="btn">(</button>
          <button class="btn">)</button>
        </div>

        <div class="row">
          <button class="btn">7</button>
          <button class="btn">8</button>
          <button class="btn">9</button>
          <button id="ce" @click="backspc">CE</button>
          <button id="ac" @click="clearScreen">AC</button>
        </div>

        <div class="row">
          <button class="btn">4</button>
          <button class="btn">5</button>
          <button class="btn">6</button>
          <button class="btn">×</button>
          <button class="btn">/</button>
        </div>

        <div class="row">
          <button class="btn">3</button>
          <button class="btn">2</button>
          <button class="btn">1</button>
          <button class="btn">+</button>
          <button class="btn">-</button>
        </div>

        <div class="row">
          <button class="btn">0</button>
          <button class="btn">.</button>
          <button class="btn">%</button>
          <button @click="pi">π</button>
          <button id="eval" @click="evaluate">=</button>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        screen: ""
      };
    },
    methods: {
      addText(event) {
        let btntext = event.target.innerText;
        if (btntext === "×") btntext = "*";
        if (btntext === "÷") btntext = "/";
        this.screen += btntext;
      },
      clearScreen() {
        this.screen = "";
      },
      backspc() {
        this.screen = this.screen.toString().slice(0, -1);
      },
      sin() {
        this.screen = Math.sin(this.screen).toString();
      },
      cos() {
        this.screen = Math.cos(this.screen).toString();
      },
      tan() {
        this.screen = Math.tan(this.screen).toString();
      },
      pow() {
        this.screen = Math.pow(this.screen, 2).toString();
      },
      sqrt() {
        this.screen = Math.sqrt(this.screen).toString();
      },
      log() {
        this.screen = Math.log(this.screen).toString();
      },
      pi() {
        this.screen = "3.14159265359";
      },
      e() {
        this.screen = "2.71828182846";
      },
      fact() {
        let num = parseInt(this.screen);
        let f = 1;
        for (let i = 1; i <= num; i++) {
          f *= i;
        }
        this.screen = f.toString();
      },
      evaluate() {
        try {
          this.screen = eval(this.screen).toString();
        } catch (error) {
          this.screen = "Error";
        }
      }
    },
    mounted() {
      const btns = document.querySelectorAll('.btn');
      btns.forEach(btn => {
        btn.addEventListener('click', this.addText);
      });
    }
  };
</script>

<style lang="scss" scoped>
  .main-body {
    overflow: hidden;
    padding: 0;
    margin: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    user-select: none;
    background: #4e4d4d;
  }

  .container {
    margin-left: 1.8em;
    padding: 20px;
    padding-left: 2px;
    padding-right: 2px;
    border-radius: 8px;
    box-shadow: 13px 13px 20px #444343, -13px -13px 20px #464545;
  }

  .content {
    width: auto;
    margin-top: 1.7em;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .row {
    button {
      width: 60px;
      height: 30px;
      font-size: 16px;
      border: none;
      outline: none;
      margin: 5px;
      border-radius: 4px;
      transition: 0.1s;
      box-shadow: 5px 5px 8px #00000020, -5px -5px 8px #444343;

      &:hover {
        box-shadow: inset 5px 5px 8px rgba(16, 16, 16, 0.1), inset -5px -5px 8px #444343;
        background: #444343;
      }
    }
  }

  .display {
    #screen {
      margin-bottom: 0.5em;
      width: 70%;
      height: 60px;
      font-size: 35px;
      outline: none;
      border: none;
      text-align: right;
      padding-right: 0.5em;
      background: #ecf0f3;
      border-radius: 6px;
      box-shadow: inset 8px 8px 8px #cbced1, inset -8px -8px 8px #ffffff;
    }
  }

  #eval {
    background: #aca24c;
    color: #fff;

    &:hover {
      box-shadow: inset 5px 5px 8px #5f5a2a, inset -5px -5px 8px #69632f;
    }
  }

  #ac {
    background: #aca24c;
    color: #fff;

    &:hover {
      box-shadow: inset 5px 5px 8px #5f5a2a, inset -5px -5px 8px #69632f;
    }
  }

  #ce {
    background: #aca24c;
    color: #fff;

    &:hover {
      box-shadow: inset 5px 5px 8px #5f5a2a, inset -5px -5px 8px #69632f;
    }
  }

  h2 {
    font-size: 40px;
    position: relative;
    bottom: 1em;
    margin-left: 1.2em;
    font-family: sans-serif;
    color: #fff;
    text-transform: uppercase;
    text-shadow:
      1px 1px 1px #d1d9e6;
    letter-spacing: 6px;

    span {
      color: #33cc33;
      font-size: 45px;
      text-shadow:
        1px 1px 1px #d1d9e6
    }

    .fa {
      position: absolute;
      top: 1.5em;
      color: #33ccff;
    }
  }
</style>