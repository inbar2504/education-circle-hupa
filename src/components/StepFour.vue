<template>
  <div id="step-four">
    <div v-if="!showQuestion">
      <p id="level-header">השלב הרביעי הינו -עיבוד</p>
    <p>בשלב העיבוד נתמקד במציאת דפוס התנהגות נפוץ הניתן לשינוי במשוב ומתבטא בסיפטומים שונים</p>
    <p>יש לדפדף כדי לראות את שלבי תהליך העיבוד</p>
    <br />
    <swiper
          
          :navigation="true"
          :modules="modules"
          class="mySwiper"
          >
          <swiper-slide class="card-slide"><div class="text-card"><b>1 שלב</b><br />איתור דוגמאות <br />משלב התצפית</div></swiper-slide>
          <swiper-slide class="card-slide"><div class="text-card"><b>שלב 2</b><br />איתור מכנה משותף לסימפטומים שונים</div></swiper-slide>
          <swiper-slide class="card-slide"><div class="text-card"><b>שלב 3</b><br />בחירת תופעות-2 לשיפור <br />ו2 לשימור</div></swiper-slide>
          <swiper-slide class="card-slide"><div class="text-card"><b>שלב 4</b><br />ניסוח תופעות</div></swiper-slide>
          <swiper-slide class="card-slide"><div class="text-card"><b>שלב 5</b><br />כתיבת הערות במידה ויש</div></swiper-slide>
    </swiper>
    <div id="heart">
      <br />
     
      &#x2764; שימו לב	 <br/>תופעה מורכבת משלושה סימפטומים לפחות, במידה וראינו סימפטום שחשוב לנו להתייחס אליו-נכתוב אותו כהערה בסיום המשוב
    </div>
    <div>
      <br />
      <p id="bold-header">כללים לניסוח תופעה</p>
      <span class="circle" id="circle1">מדויקת</span>
      <span class="circle" id="circle2">מפורטת</span>
      <span class="circle" id="circle3">כתיבה על דרך החיוב</span>
    </div><br /><br />
    <button id="continu" @click="showQuestions">המשך</button>
    <br /><br />
    </div>
    
    <div v-if="showQuestion" id="questions">

      <p>בדיקה קצרה שהבנת את החומר</p><br />
      <p>מעבר לשלושה סימפטומים נקראים תופעה</p><br />
      <button class = "buttons" id="right1" v-if ="count=1" @click='checkAnswer("right1","green","wrong1")'>נכון</button> / <button id="wrong1" @click='checkAnswer("wrong1","red","right1")'>לא נכון</button>
      <br />
      <br />
      <p>תופעות יכולות להיות חיוביות</p>
      <button id="right2" @click='checkAnswer("right2","green","wrong2")'>נכון</button> / <button id="wrong2" @click='checkAnswer("wrong2","red","right2")'>לא נכון</button>

    </div>
    <br />
    <button id="continue" @click="BackToHomePage">המשך</button>
  </div>
</template>

<script>

import { ref } from 'vue';
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css/scrollbar";
// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import { Navigation } from "swiper/modules";

export default {
  name: "step-four",
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
        showQuestion: false,
        answer: '',
        count: 0,
       
    };
  },
  methods: {
    checkAnswer(answerId,colorAnswer,notSelected) {
      document.getElementById(answerId).style.color = colorAnswer;
      document.getElementById(notSelected).disabled=true;
      if(this.count === 2) {
        document.getElementById("continue").style.display="block";
      }
      this.count++;
    },
    showQuestions() {
        this.showQuestion=true;
        // this.countDownTimer();
    },
    BackToHomePage() {
      this.$emit("finish-stop-four");
    },
  },
  setup() {
    return { modules: [Navigation] };
  },
};
</script>


<style scoped>
* {
  max-width: 70vw;
}
#step-four {
  background-color: #2a9d8f;
  background-color: #2a9d8f;
  min-width: 100vw;
  min-height: 100vh;
  display: flow;
  text-align: center;
  padding: 60px;
  font-size: 7vmin;
}
/* .swiper {
  margin-left: auto;
    margin-right: auto;
    position: relative;
    overflow: hidden;
    list-style: none;
    padding: 0;
    z-index: 1;
    display: block;
    width: 75vw;
} */
.text-card {
  /* width: 50vw;
  font-size: 6.5vmin; */
  width: 62vw;
  font-size: 5vmin;
 }
.swiper-button-prev, .swiper-rtl .swiper-button-next {
    left: var(--swiper-navigation-sides-offset, 10px);
    right: auto;
    color: #e9c46a;

}
.swiper-button-next, .swiper-rtl .swiper-button-prev {
    right: var(--swiper-navigation-sides-offset, 10px);
    left: auto;
    color: #e9c46a;
}
.card-slide {
  /* border: 2px solid;
  border-radius: 15px; */
  width: 50vw; 
  height: 16vh;
  justify-content: center;
  display: flex;
  align-items: center;

}
#level-header {
  font-family: 'ellinia-bold';
  font-size: 8vmin;
}
.circle {
  display: flex;
    border-radius: 50%;
    background-color: blue;
    height: 28vw;
    width: 28vw;
    justify-content: center;
    flex-direction: column;
    margin-top: 10%;
    margin-left: 30%;
    font-size: 5vmin;
    font-family: 'ellinia-bold';
    padding: 3px;
}
#circle1 {
  background-color: #e9c46a;
}
#circle2 {
  background-color: #f4a261;
}
#circle3 {
  background-color: #e76f51;
}
#bold-header {
  font-family: "ellinia-bold";
}
#some_div {
    position: absolute;
    top: 5%;
    left: 5%;
}
:deep(.swiper-button-next:after, .swiper-rtl .swiper-button-prev:after) {
    content: 'next';
    color: #e9c46a;
}
:deep(.swiper-button-prev:after, .swiper-rtl .swiper-button-next:after) {
    content: 'prev';
    color: #e9c46a;
}
#continue {
  display: none;
  text-align: center;
  position: relative;
  left: 50%;
  transform: translateX(-50%);
  /* position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 75vh; */
}
#questions {
  font-size: 7vmin;
}
button {
    border-radius: 8px;
    border: 1px solid transparent;
    font-size: 1em;
    font-weight: 500;
    background-color: #1a1a1a;
    cursor: pointer;
    transition: border-color 0.25s;
    border-radius: 0;
    color: #2a9d8f;
    background-color: #264653;
    font-family: 'ellinia-bold';
    padding: 5px;
    width: 30vw;
}
</style>