<template>
  <div id="app">
    <div v-if="page === 0 || page === 1">
      <div id="orange-line">
      <p id="header">מעגל החניכה</p>
    </div>
    <div id="yellow-line"></div>
    <div id="blue-line"></div>
    <div id="dark-blue-line">
      <img src="./assets/red-book-1.png" id="red-book-1"/>
      <img src="./assets/orange-book-1.png" id="orange-book-1"/>
      <img src="./assets/yellow-book-1.png" id="yellow-book-1"/>
      <img src="./assets/blue-book-1.png" id="blue-book-1"/>
      <img src="./assets/red-book-2.png" id="red-book-2"/>
      <img src="./assets/orange-book-2.png" id="orange-book-2"/>
      <div>
        <img src="./assets/man.png" id="man"/>
      </div>
      <img src="./assets/yellow-book-2.png" id="yellow-book-2"/>
    </div>
    </div>
    
    <button v-show="page === 0" @click="showHome" id="btn">התחלה</button>
    <div v-show="page === 1">
      <button @click="showExplanations" id="btn1">ללמוד</button>
      <button @click="showExercises" id="btn2">לתרגל</button>
    </div>
    <explanations
      v-show="page === 2"
      @back-to-options="page = 1"
    ></explanations>
    <exercises v-show="page === 3" @showStart="showStart"></exercises>
  </div>
</template>

<script>
import Explanations from "./components/Explanations.vue";
import Exercises from "./components/Exercises.vue";

// Vuetify
import "vuetify/styles";
import * as components from "vuetify/components";
import * as directives from "vuetify/directives";

export default {
  name: "app",
  // props: ],
  components: {
    Explanations,
    Exercises,
  },
  data() {
    return {
      page: 0,
      // redBook1: require("@/assets/red-book-1.png"),
    };
  },
  methods: {
    showHome() {
      this.page = 1;
    },
    showExplanations() {
      this.page = 2;
    },
    showExercises() {
      this.page = 3;
    },
    showStart() {
      this.page = 0;
    }
  },
};
</script>

<style scoped>
@font-face {
  font-family: "assistant";
  src: url("./assets/font/Assistant-Regular.ttf");
}
@font-face {
  font-family: "assistant-bold";
  src: url("./assets/font/Assistant-Bold.ttf");
}
* {
  overflow-x: hidden;
  text-align: center;
  /* direction: rtl; */
}
body {
  /* background-size: 100% 100%; */
  background-color: #e76f51;


}
#app {
  overflow-x: hidden;
  font-family: "assistant";
}
#btn1 {
  font-size: 10vmin;
    z-index: 10;
    background-color: bisque;
    position: absolute;
    bottom: 3vh;
    border-radius: 0px;
    left: 10vw;
    padding: 20px;
}
#btn2 {
  font-size: 10vmin;
    z-index: 10;
    background-color: bisque;
    position: absolute;
    top: 85.5vh;
    border-radius: 0px;
    padding: 20px;
    right: 10vw;
}
#btn {
  font-size: 10vmin;
  z-index: 10;
  background-color: bisque;
  position: absolute;
  top: 85.5vh;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 0px;
}
#header {
  font-size: 11vmin;
  margin: -12px;
}
#orange-line {
  background-color: #f4a261;
    position: absolute;
    top: 10%;
    left: 0%;
    width: 100vw;
    height: 72vh;
    z-index:2;
}
#yellow-line {
  background-color: #e9c46a;
    position: absolute;
    top: 15%;
    left: 0%;
    width: 100vw;
    height: 60vh;
    z-index:3;
}
#blue-line {
  background-color: #2a9d8f;
  position: absolute;
  top: 19%;
  left: 0%;
  width: 100vw;
  height: 47vh;
  z-index: 3;
}
#dark-blue-line {
  background-color: #264653;
  position: absolute;
  top: 24%;
  left: 0%;
  width: 100vw;
  height: 40vh;
  z-index: 4;
}
#red-book-1 {
  position: absolute;
    top: 13%;
    width: 20%;
    left: 38%;
    z-index: 3;
}
#orange-book-1 {
  position: absolute;
  top: 17%;
  width: 32%;
  left: 42%;
  z-index: 1;
}
#yellow-book-1 {
  position: absolute;
    top: 37%;
    width: 42%;
    left: 44%;
}
#blue-book-1 {
  position: absolute; 
  top: 47%; 
  width: 38%; 
  left: 38%;
}
#red-book-2 {
  position: absolute;
    top: 50%;
    width: 21%;
    left: 32%;
}
#orange-book-2 {
  position: absolute;
    top: 49%;
    width: 34%;
    left: 14%;
}
#yellow-book-2 {
  position: absolute;
    top: 44%;
    width: 43%;
    left: 5%;
}
#man {
  position: absolute;
  width: 15%;
  z-index: 3;
  top: 7vh;
  left: 18vw;

}
/* @media only screen and (max-width: 512px) {
  body {
    -webkit-overflow-scrolling: touch;
    height: auto;
    overflow: scroll;
  } 
} */
</style>
