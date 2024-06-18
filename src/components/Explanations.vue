<template>
  <div id="explanations">
    <div v-if="step === 0">
      <div id="red-line">
      <p id="start-header">
        הינך צריך לחנוך חייל חדש. טרם, עלייך ללמוד את מעגל החניכה, על מנת להיות
        החונך הטוב ביותר! לחץ על כל שלב במעגל בכדי ללמוד על הנושא
      </p>
    </div>
      <div id="dark-blue-line">
        <div id="step1" @click="step = 1">
          <p id="step1-header">הכנה עצמית</p>
          <img src="@/assets/step1.png" id="step1-img" :class="{'disabled-img': isStep1Finished}"/>
        </div>
        <div id="step2" @click="step = 2">
          <p id="step2-header">תדריך</p>
          <img src="@/assets/step2.png" id="step2-img" :class="{'disabled-img': isStep2Finished}"/>
        </div>
        <div id="step3" @click="step = 3">
          <p id="step3-header">תצפית</p>
          <img src="@/assets/step3.png" id="step3-img" :class="{'disabled-img': isStep3Finished}"/>
        </div>
        <div id="step4" @click="step = 4">
          <p id="step4-header">עיבוד</p>
          <img src="@/assets/step4.png" id="step4-img" :class="{'disabled-img': isStep4Finished}"/>
        </div>
       <div id="step5" @click="step = 5">
        <p id="step5-header">משוב</p>
        <img src="@/assets/step5.png" id="step5-img" :class="{'disabled-img': isStep5Finished}"/>
       </div>
        <div id="step6" @click="step = 6">
          <p id="step6-header">סיכום והפקת לקחים</p>
          <img src="@/assets/step6.png" id="step6-img" :class="{'disabled-img': isStep6Finished}"/>
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

    <step-one v-if="step === 1" @finish-stop-one="steps"></step-one>
    <step-two v-if="step === 2" @finish-stop-two="steps"></step-two>
    <step-three v-if="step === 3" @finish-stop-three="steps"></step-three>
    <step-four v-if="step === 4" @finish-stop-four="steps"></step-four>
    <step-five v-if="step === 5" @finish-stop-five="steps"></step-five>
    <step-six v-if="step === 6" @finish-stop-six="steps"></step-six>
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
      num:0,
      isStep1Finished: false,
      isStep2Finished: false,
      isStep3Finished: false,
      isStep4Finished: false,
      isStep5Finished: false,
      isStep6Finished: false,
    };
  },

  methods: {
    steps() {
      // console.log(`${window.this.step}`);
      // `this.isStep${this.window.step}Finished` = true;
      if(this.step === 1) {
        this.isStep1Finished = true;
      }
      if(this.step === 2) {
        this.isStep2Finished = true;
      }
      if(this.step === 3) {
        this.isStep3Finished = true;
      }
      if(this.step === 4) {
        this.isStep4Finished = true;
      }
      if(this.step === 5) {
        this.isStep5Finished = true;
      }
      if(this.step === 6) {
        this.isStep6Finished = true;
      }
      this.step = 0;
      // this.step = num;
      // this.step = 1;
      // document.getElementById(`step1-img`).style.cssText = "opacity: 0.4;";
      // document.getElementById(`step${num}-img`).classList.add("opac");
      // console.log(`step${num}-img`);
    },
    backTo() {
      this.$emit("back-to-options");
    },
  },
};
</script>

<style scoped>
#explanations {
  font-family: "ellinia";
  font-size: 8vmin;
  overflow: hidden;
  /* max-width: 60vw; */
  /* background-size: 100% 100%; */
}
.disabled-img {
  opacity: 0.5;
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
  position: relative;
  top: 1vh;
    font-size: 5vmin;
    width: 90vw;
    left: 50%;
    transform: translateX(-50%);
    font-family: 'ellinia-bold';
}
#step1 {
  position: absolute;
  top: 2vh;
  left: 61vw
}
#step1-img {
  width: 11vw;

}
#step2 {
  position: absolute;
    top: 20vh;
    left: 75vw;
}
#step2-img {
  width: 16vw;

}
#step3 {
  position: absolute;
  top: 36vh;
  left: 55vw;
}
#step3-img {
  width: 29vw; 

}
#step4 {
  position: absolute;
  top: 33vh;
  left: 20vw;
}
#step4-img {
  width: 21vw;

}
#step5 {
  position: absolute;
  top: 16vh;
  left: 8vw;

}
#step5-img {
  width: 19vw;

}
#step6 {
  position: absolute;
    top: 3vh;
    left: 28vw;
}
#step6-img {
  width: 17vw;

}
#center-man-img {
  width: 19vw;
  position: absolute;
  top: 21vh;
  left: 50%;
  transform: translateX(-50%);
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
    position: absolute;
    top: 86%;
    left: -70%;
    font-size: 5vmin;
    width: 30vw;
    color: white;
}
#step2-header {
    position: absolute;
    top: 88%;
    left: 26%;
    font-size: 5vmin;
    color: white;
}
#step3-header {
  position: absolute;
  top: 75%;
  left: 0%;
  font-size: 5vmin;
  width: 30vw;
  color: white;
}
#step4-header {
  position: absolute;
  left: 22%;
  top: 84%;
  font-size: 5vmin;
  color: white;
}
#step5-header {
  position: absolute;
    top: 88%;
    left: 26%;
    font-size: 5vmin;
    color: white;
}
#step6-header {
  position: absolute;
  left: -40%;
  top: 87%;
    font-size: 5vmin;
    width: 33vw;
    color: white;
}
#back-btn {
  position: absolute;
    top: 75vh;
    /* z-index: 33; */
    left: 50%;
    transform: translateX(-50%);
    color: #2a9d8f;
    background-color: #f4a261;
    border-radius: 0;
    font-family: 'ellinia-bold';
}
</style>
