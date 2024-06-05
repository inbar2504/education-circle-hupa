<template>
  <div id="explanations">
    <div v-if="step === 0">
      <div id="red-line"></div>
      <p id="start-header">
        הינך צריך לחנוך חייל חדש. טרם, עלייך ללמוד את מעגל החניכה, על מנת להיות
        החונך הטוב ביותר! לחץ על כל שלב במעגל בכדי ללמוד על הנושא
      </p>
      <div id="dark-blue-line">
        <div id="step1" @click="step = 1">
          <p id="step1-header">הכנה עצמית</p>
          <img src="@/assets/step1.png" id="step1-img"/>
        </div>
        <div id="step2" @click="step = 2">
          <p id="step2-header">תדריך</p>
          <img src="@/assets/step2.png" id="step2-img"/>
        </div>
        <div id="step3" @click="step = 3">
          <p id="step3-header">תצפית</p>
          <img src="@/assets/step3.png" id="step3-img"/>
        </div>
        <div id="step4" @click="step = 4">
          <p id="step4-header">עיבוד</p>
          <img src="@/assets/step4.png" id="step4-img"/>
        </div>
       <div id="step5" @click="step = 5">
        <p id="step5-header">משוב</p>
        <img src="@/assets/step5.png" id="step5-img"/>
       </div>
        <div id="step6" @click="step = 6">
          <p id="step6-header">סיכום והפקת לקחים</p>
          <img src="@/assets/step6.png" id="step6-img"/>
        </div>
        <!-- <img src="@/assets/step6.png" id="step6-img"/> -->
        <img src="@/assets/center-man.png" id="center-man-img"/>
      </div>
      <div id="yellow-line"></div>
      <div id="green-line"></div>
      <!-- <button id="step1" @click="step = 1">הכנה עצמית</button>
      <button id="step2" @click="step = 2">תדריך</button>
      <button id="step3" @click="step = 3">תצפית</button>
      <button id="step4" @click="step = 4">עיבוד</button>
      <button id="step5" @click="step = 5">משוב</button>
      <button id="step6" @click="step = 6">סיכום והפקת לקחים</button> -->
      <button id="back-btn" @click="backTo">חזור</button>
    </div>

    <step-one v-if="step === 1" @finish-stop-one="step = 0"></step-one>
    <step-two v-if="step === 2" @finish-stop-two="step = 0"></step-two>
    <step-three v-if="step === 3" @finish-stop-three="step = 0"></step-three>
    <step-four v-if="step === 4" @finish-stop-four="step = 0"></step-four>
    <step-five v-if="step === 5" @finish-stop-five="step = 0"></step-five>
    <step-six v-if="step === 6" @finish-stop-six="step = 0"></step-six>
  </div>
</template>

<script>
import StepOne from "./StepOne.vue";
import StepTwo from "./StepTwo.vue";
import StepThree from "./StepThree.vue";
import StepFour from "./StepFour.vue";
import StepFive from "./StepFive.vue";
import StepSix from "./StepSix.vue";

export default {
  name: "explanations",
  components: {
    StepOne,
    StepTwo,
    StepThree,
    StepFour,
    StepFive,
    StepSix,
  },
  data() {
    return {
      step: 0,
    };
  },
  methods: {
    backTo() {
      this.$emit("back-to-options");
    },
  },
};
</script>

<style scoped>
#explanations {
  font-family: "assistant";
  font-size: 8vmin;
  overflow: hidden;
  /* max-width: 60vw; */
  /* background-size: 100% 100%; */
}
#dark-blue-line {
  position: absolute;
  width: 100vw;
  background-color: #264653;
  height: 50vh;
  top: 25vh;
}
#red-line {
  position: absolute;
  top: 10%;
  height: 22vh;
  width: 100vw;
  background-color: #f4a261;
} 
p {
  position: absolute;
    top: 13vh;
    font-size: 5vmin;
}
#start-header {
  position: absolute;
  top: 10vh;
    font-size: 5vmin;
    width: 90vw;
    left: 50%;
    transform: translateX(-50%);
    font-family: 'assistant-bold';
}
#step1-img {
  width: 12vw;
    position: absolute;
    top: 3vh;
    left: 60vw;
}
#step2-img {
  width: 16vw;
    position: absolute;
    top: 20vh;
    left: 76vw;
}
#step3-img {
  width: 29vw; 
  position: absolute; 
  top: 35vh; 
  left: 52vw;
}
#step4-img {
  width: 21vw;
  position: absolute;
  top: 33vh;
    left: 20vw;
}
#step5-img {
  width: 21vw;
    position: absolute;
    top: 17vh;
    left: 6vw;
}
#step6-img {
  width: 19vw;
  position: absolute;
  top: 3vh;
  left: 27vw;
}
#center-man-img {
  width: 19vw;
  position: absolute;
  top: 21vh;
  left: 43vw;
}
#yellow-line {
  position: absolute;
  width: 100%;
  height: 10vh;
  background-color: #e9c46a;
  top: 74vh;
}
#green-line {
  position: absolute;
    width: 100%;
    height: 16vh;
    background-color: #2a9d8f;
    bottom: 0vh;
}
#step1-header {
  position: relative;
    top: 16vh;
    left: 16vw;
    font-size: 5vmin;
}
#step2-header {
   position: relative;
    left: 33vw;
    top: 27vh;
    font-size: 5vmin;
}
#step3-header {
  position: relative;
  top: 35vh;
    left: 17vw;
    font-size: 5vmin;
}
#step4-header {
   position: relative;
   right: 19vw;
    top: 33vh;
  font-size: 5vmin;
}
#step5-header {
  position: relative;
  top: 15vh;
    right: 32vw;
  font-size: 5vmin;
}
#step6-header {
  position: relative;
    left: 20vw;
    top: -3vh;
    font-size: 5vmin;
    width: 33vw;
}
#back-btn {
  position: absolute;
    top: 87vh;
    /* z-index: 33; */
    left: 50%;
    transform: translateX(-50%);
    color: #2a9d8f;
    background-color: #f4a261;
    border-radius: 0;
    font-family: 'assistant-bold';
}
</style>
