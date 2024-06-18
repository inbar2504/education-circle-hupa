<template>
  <div id="step-five">
    <div v-if="!showQuestion">
      <p class="level-header">השלב החמישי והאחד לפניי אחרון הינו שלב המשוב</p>
      <p>
        מטרת שלב המשוב היא שימור ושיפור ביצועו של הנחנך, הצגת תוצרי העיבוד בפני
        הנחנך, והפקת לקחים להמשך על ידי איתור הגורמים לתופעות הביצוע של הנחנך
      </p>
      <br />
      <p>בעת ביצוע משוב חשוב לשים לב לדגשים הבאים</p>
      <br />
      <swiper
        

        :navigation="true"
        :modules="modules"
        class="mySwiper"
      >
      <!-- :slides-per-view="1"
        :space-between="50" -->

        <swiper-slide class="card-slide" id="o1"
          ><div class="options">תמיכה באגו ועירור מוטיבציה</div></swiper-slide
        >
        <swiper-slide class="card-slide" id="o2"><div class="options">איסוף אינפורמציה</div></swiper-slide>
        <swiper-slide class="card-slide" id="o3"><div class="options">מתן לגיטימציה לטעויות</div></swiper-slide
        >
        <swiper-slide class="card-slide" id="o4"
          ><div class="options">דיבור בשפה משותפת></div></swiper-slide
        >
        <swiper-slide class="card-slide" id="o5"><div class="options">תמציתיות</div></swiper-slide>
        <swiper-slide class="card-slide" id="o6"
          ><div class="options">עיתוי ומיון מתאים לביצוע שיחת המשוב</div></swiper-slide
        >
      </swiper>
      <br /><br />
      <v-card class="mx-auto card" width="300">
        <v-list v-model:opened="open">
          <v-list-item class="header-top"><b>מבנה המשוב</b></v-list-item>

          <v-list-group value="Admin">
            <template v-slot:activator="{ props }">
              <v-list-item v-bind="props"
                ><b class="header">פתיחה</b>
              </v-list-item>
            </template>

            <v-list-item
              v-for="(title, i) in admins"
              :key="i"
              class="v-list-item-title"
              :title="title"
              :value="title"
            ></v-list-item>
          </v-list-group>

          <v-list-group value="Actions">
            <template v-slot:activator="{ props }">
              <v-list-item v-bind="props"
                ><b class="header">גוף</b></v-list-item
              >
            </template>

            <v-list-item
              v-for="(title, i) in cruds"
              :key="i"
              class="v-list-item-title"
              :title="title"
              :value="title"
            ></v-list-item>
          </v-list-group>
          <v-list-group value="Admin11">
            <template v-slot:activator="{ props }">
              <v-list-item v-bind="props"
                ><b class="header">סיכום</b></v-list-item
              >
            </template>

            <v-list-item
              v-for="(title, i) in admin11"
              :key="i"
              class="v-list-item-title"
              :title="title"
              :value="title"
            ></v-list-item>
          </v-list-group>
        </v-list>
      </v-card>
      <br /><br /><br /><br /><br /><br /><br /><br />
      <p class="level-header">מתן המשוב</p>
      <p>
        בעת מתן המשוב נבדוק קודם מה הסיבה שלושת הסיבות שנבדוק הן: מודעות , תפיסה
        ויישום. ראשי תיבות מת”י. לחצו על כל סיבה כדי לראות פירוט מעמיק עליה
      </p>
      <button class="mati" @click="showMati('ye')">יישום</button>
      <button class="mati" @click="showMati('tf')">תפיסה</button>
      <button class="mati" @click="showMati('mu')">מודעות</button>
      <div id="mu" class="mati3">
        <br />
        <b class="bold-h">-מודעות-</b><br />
        מצב בו הנחנך לא קלט את הגירוי
        <br />
        <b>התמודדות</b>
        <br />
        מתן הוכחות מהתצפית,העלאת המודעות, מתן כלים לתשומת לב
        <br />
        <button @click="closeWindow('mu')" class="ok-btn">אוקיי, הבנתי</button>
      </div>
      <div id="tf" class="mati3">
        <br /><b class="bold-h">-תפיסה-</b><br />
        האמונות, התפיסות והדעות לא תואמות את התורה המקצועית ולא תואמות את המצב הנתון
        <br />
        <b>התמודדות</b>
        <br />
        להראות את ההשלכות של הפעולה-יתרונות וחסרונות, דוגמאות מהניסיון
        <br />
        <button @click="closeWindow('tf')" class="ok-btn">אוקיי, הבנתי</button>
      </div>
      <div id="ye" class="mati3">
        <br /><b class="bold-h">-יישום-</b><br />
        ביצוע טכני לא איכותי, בחירת פתרון/תגובה שלא מתאימים למצב
        <br />
        <b>התמודדות</b>
        <br />
        תרגול,מתן כלים נוספים,הסבר על השלכות בחירת הכלים
        <br />
        <button @click="closeWindow('ye')" class="ok-btn">אוקיי, הבנתי</button>
      </div>
      <p class="level-header"><b>התנגדויות במשוב</b></p>
      <p>ביטוי התנהגותי לאי הסכמה ורצון להפסיק אתהתקשורת עם החונך</p>
      <br />
      <p class="level-header"><b>סיבות להתנגדויות</b></p>
      <p>
        התנהגות החונך -<br />
        אי הכרה בחשיבות החניכה -<br />
        איום על האגו -<br />
        גורמים סביבתיים -<br />
      </p>
      <br />
      <p class="level-header"><b>שלבי דרכי ההתמודדות</b></p>
      <br />
      <p>
        זיהוי התמודדות<br />
        &#8595;<br />
        עצירה ושיקוף<br />
        &#8595;<br />
        איתור סיבת ההתנגדות<br />
        &#8595; <br />
        טיפול בהתנגדות<br />
        &#8595; <br />
        חזרה לתקשורת<br />
      </p><br />
      <button id="continu" @click="showQuestions">המשך</button>
    </div>
    <div v-if="showQuestion">
      <p id="some_div">{{ countDown }}</p>
      <h2 id="time-over">!הזמן נגמר</h2>
      <p id="header">
        בוחן פתע<br />
        יש לך 30 שניות לענות על השאלות הבאות.<br />
        יש פה מספר מאפיינים של סוגי מתנגדים<br />
        אנא בחר איזה סוג מתנגד מתאים לכל מאפיין <br />
      </p>
      <div>
        <p>לא מסכים עם אף נקודה</p>
        <select name="question1" class="selects" id="que1">
          <option class="option" value="nothing" id="o1">-בחר אופציה-</option>
          <option class="option" value="first" id="o2">הווכחן</option>
          <option class="option" value="second" id="o3">המסכים לכאורה</option>
          <option class="option" value="third" id="o4">טראגי</option>
        </select>
      </div>
      <div>
        <p>מהנהן, פסיבי,מחכה לתשובת החונך ומיד מסכים עמו</p>
        <select name="question2" class="selects" id="que2">
          <option class="option" value="nothing" id="o5">-בחר אופציה-</option>
          <option class="option" value="first" id="o6">הווכחן</option>
          <option class="option" value="second" id="o7">המסכים לכאורה</option>
          <option class="option" value="third" id="o8">טראגי</option>
        </select>
      </div>
      <div>
        <p>חסר פרופורציה בוכה לעיתים,</p>
        <select name="question3" class="selects" id="que3">
          <option class="option" value="nothing" id="o9">-בחר אופציה-</option>
          <option class="option" value="first" id="1o">הווכחן</option>
          <option class="option" value="second" id="2o">המסכים לכאורה</option>
          <option class="option" value="third" id="3o">טראגי</option>
        </select>
      </div>
      <br />
      <button @click="checkQuestion">הגש</button>
      <div id="right-answers">
        <br />
        <br />
        <p>התשובות הנכונות הן</p>
        <br />
        <p>לא מסכים עם אף נקודה - הווכחן</p>
        <br />
        <p>מהנהן,פסיבי,מחכה לתשובת החונך ומיד מסכים עמו - המסכים לכאורה</p>
        <br />
        <p>חסר פרופורציה,בוכה לעיתים - טראגי</p>
        <br />

        <br />

        <button id= "wrong" @click="BackToHomePage">סיום</button>
      </div>
      <div id="right">
        <br />
        <br />
        <h1 id="you-right">!יפה מאוד !צדקת בכל התשובות</h1>

        <br />

        <button @click="BackToHomePage">סיום</button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css/scrollbar";
// Import Swiper
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import { Navigation } from "swiper/modules";

export default {
  name: "step-five",
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      showQuestion: false,
      count: 0,
      countDown: 30,
      timeOver: false,
      open: ["Users"],
      admins: [
        ["מיקום"],
        ["זמן"],
        ["יצירת אווירה"],
        ['נטרול "חוזה" ונטרול חששות'],
      ],
      cruds: [
        ["תופעות מפורטות וסימפטומים"],
        ["איתור וטיפול"],
        ["התייחסות הנחנך"],
      ],
      admin11: [
        ["הגעה להסכמה משותפת בדבר הלקחים"],
        ["הסכמה על הצעדים הבאים"],
        ["סיכום שיחת המשוב והפקת לקחים"],
      ],
      mati: "",
      rightAnswers: 0,
    };
  },
  methods: {
    showMati(mati) {
      document.getElementById(`${mati}`).style.display = "block";
    },
    countDownTimer() {
      
      if (this.countDown > 0) {
        setTimeout(() => {
          this.countDown -= 1;
          this.countDownTimer();
        }, 1000);
      } else if (this.countDown === 0) {
        document.getElementById("time-over").style.display = "block";
        if (this.rightAnswers < 3) {
          document.getElementById("right-answers").style.display = "block";
        }
      } else {
        this.timeOver = true;
        this.checkQuestion();
        document.getElementById("time-over").stytle.display = "block";
        
        if (this.rightAnswers < 3) {
          document.getElementById("right-answers").style.display = "block";
        }
      }
    },
    showQuestions() {
      this.showQuestion = true;
      this.countDownTimer();
    },
    
    closeWindow(mati) {
      document.getElementById(`${mati}`).style.display = "none";
    },
    checkQuestion() {
      this.rightAnswers = 0;
      if (document.getElementById("o2").selected) {
        document.getElementById("que1").style.color = "green";
        this.rightAnswers++;
      } else {
        document.getElementById("que1").style.color = "red";
      }
      if (document.getElementById("o7").selected) {
        document.getElementById("que2").style.color = "green";
        this.rightAnswers++;
      } else {
        document.getElementById("que2").style.color = "red";
      }
      if (document.getElementById("3o").selected) {
        document.getElementById("que3").style.color = "green";
        this.rightAnswers++;
      } else {
        document.getElementById("que3").style.color = "red";
      }
      if (this.rightAnswers === 3) {
        document.getElementById("right").style.display = "block";
        document.getElementById("some_div").style.display = "none";
      }
    },
    BackToHomePage() {
      document.getElementById("time-over").style.display = "none";
      this.$emit("finish-stop-five");
    },
  },
  setup() {
    return { modules: [Navigation] };
  },
};
</script>

<style scoped>
#step-five {
  font-size: 6vmin;
  max-width: 78vw;
  background-color: #264653;
  position: absolute;
  min-height: 100vh;
  min-width: 100vw;
  top: 0vh;
  padding: 40px;
}
:deep(.swiper-button-next:after, .swiper-rtl .swiper-button-prev:after) {
    content: 'next';
    color: #e9c46a;
    font-size: 22vmin;
}
:deep(.swiper-button-prev:after, .swiper-rtl .swiper-button-next:after) {
    content: 'prev';
    color: #e9c46a;
    font-size: 22vmin;
}
.level-header {
  font-family: 'ellinia-bold';
}
.card-slide {
  height: 10vh;
  width: 50vw;
  position: relative;
  left: 50%;
  transform: translateX(-50%);
  font-size: 6vmin;
  justify-content: center;
  display: flex;
  align-items: center;


}
.options {
  width: 55vw;
}
button {
    border-radius: 0px;
    border: 1px solid transparent;
    padding: 10px;
    font-size: 1em;
    font-weight: 500;
    background-color: #1a1a1a;
    cursor: pointer;
    transition: border-color 0.25s;
    color: #264653;
    background-color: #2a9d8f;
    font-family: "ellinia-bold";
}
:deep(.v-list-group__items .v-list-item) {
  --indent-padding: 0px !important;
  padding-inline-start: 0px !important;
}
:deep(.card) {
  padding: 1px;
    background-color: #2a9d8f;
    font-family: 'ellinia-bold';
    background-color: #2a9d8f;
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    z-index:2;

    
}
:deep(.v-list-item--density-default:not(.v-list-item--nav).v-list-item--one-line) {
    padding-inline: 68px;
    background-color: #2a9d8f;
}
:deep(.v-list) {
    --indent-padding: 0px;
    background-color: #2a9d8f;
    font-family: 'ellinia';
}

:deep(.v-list-item__title) {
  white-space: normal;
}
:deep(.v-list-item-title) {
  hyphens: auto;
  overflow-wrap: normal;
  /* overflow: hidden; */
  padding: 0;
  white-space: normal !important;
  text-overflow: ellipsis;
  word-break: normal;
  word-wrap: break-word;
  font-size: 5vmin;
  font-weight: 400;
  letter-spacing: 0.009375em;
  line-height: 1.5;
  text-transform: none;
  direction: ltr;
  text-align: right;
}
/* :deep(.swiper-slide) {
    flex-shrink: 0;
    width: 100%;
    height: 100%;
    position: relative;
    transition-property: transform;
    display: block;
    width: 50vw;
} */
.header-top {
  font-weight: bold;
}
.mati {
  position: relative;
  width: 30%;
  border: 2px solid;
  border-radius: 100px;
  margin: 1%;
  padding: inherit;
  margin-top: 10%;
  margin-bottom: 10%;
  background-color: #f4a261;
}
#mati3 {
  width: 76%;
  height: 89%;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #c3a4a4;
  z-index: 1;
  display: none;
}
#some_div {
  position: absolute;
  top: 2%;
  left: 5%;
}
#mu {
  width: 76%;
  height: 60%;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #e76f51;
  z-index: 2;
  /* display: none; */
  display: none;
}
#tf {
  width: 76%;
  height: 60%;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #2a9b8f;
  z-index: 2;
  display: none;
}
#ye {
  width: 76%;
  height: 60%;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #e9c46a;
  z-index: 2;
  display: none;
}
.bold-h {
  font-size: 8vmin;
}
.ok-btn {
  position: absolute;
  bottom: 1%;
  left: 50%;
  transform: translateX(-50%);
  height: 6vh;
  width: 50vw;
  font-size: 6vmin;
  background-color: #264653;
  border-radius: 0;
  color: white;
  font-family: 'ellinia-bold';
  padding: 1px;
}
.selects {
  color:#e76f51 ;
  border: 2px solid #e9c46a;
  padding: 2%;
}
.option {
  font-size: 3vmin;
  text-align: center;
}
#right-answers {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 70%;
  height: 70%;
  background-color: #e9c463;
  display: none;
}
#right {
  position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 79%;
    height: 58%;
    background-color: #e76f51;
    margin: 2%;
  display: none;
}
#time-over {
  display: none;
  font-size: 10vmin;
  color: #e76f51;
  font-family: 'ellinia-bold';
}
#you-right {
  font-size: 13vmin;
}
#header {
  color: #e9c46a;
}
#wrong {
  position: relative;
  bottom: 12%;
  font-size: 5vmin;
}
</style>
