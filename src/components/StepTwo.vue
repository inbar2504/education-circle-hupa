<template>
  <div id="step-two">
    <div v-if="!showQuestions">
      <br />
        <p class="starting" id="header">השלב השני הינו - תדריך</p>
    <p class="starting">שלב התדריך הינו המפגש הרשמי הראשוני בין החונך לנחנך. מטרתו לספק לנחנך מקסימום כלים שישמשו אותו להתמודדות מוצלחת ולהפקת לקחים מקסימאלית</p>
    <p>:עקרונות התדריך</p>
    <div class="scene scene--card">
    <div class="card">
        <div class="card__face card__face--front">סדר הגיוני</div>
        <div class="card__face card__face--back">קצר, תכליתי וממוקד, בנוי לפי סדר מסוים</div>
    </div>
    </div>
    <div class="scene scene--card">
    <div class="card">
        <div class="card__face card__face--front">עירור מוטיבציה</div>
        <div class="card__face card__face--back">על מנת להעלות את רמת המסוגלות של הנחנך</div>
    </div>
</div>
    <div class="scene scene--card">
    <div class="card">
        <div class="card__face card__face--front">גורמי סביבה ומסגרת</div>
        <div class="card__face card__face--back">הסביבה בה נערך התדריך והסביבה ומסגרת המשימה</div>
    </div>
  </div><br /><br />
  <h2>מבנה התדריך</h2><br />
  <div class="frame">
    <h2>הגדרת מטרות המשימה</h2>
  </div>
  <div class="frame">
    <h2>הצגת מתווה המשימה</h2>
    <p>אירוע פותח, השתלשלות העניינים, אמצעים, כוחות וחלוקת תפקידים, ממשימות.</p>
  </div>
  <div class="frame">
    <h2>מתן דגשים לביצוע</h2>
    <p>מקצועיים,בטיחותיים,מנהלתיים, ערכיים,מנהיגותיים...</p>
  </div>
  <div class="frame">
    <h2>בדיקת הבנה</h2>
    <p>על הנחנך לחזור על הנקודות העיקריות בתדריך</p>
  </div>
  <button @click="showQuestion">המשך</button><br /><br />
</div>
    <div id="step-two-questions" v-if="showQuestions">
        
        <p id="some_div">{{ countDown }}</p>
        <p id="header">בוחן פתע! יש לך 30 שניות  לענות נכון על השאלות</p>
            <fieldset id="que1">
            <legend>מה אינו חלק ממבנה התדריך?</legend>

            <div>
                <input type="radio" id="answer1" name="question1" value="false1"/>
                <label for="answer1" id="answer10">הגדרת מתן הגדרות</label>
            </div>

            <div>
                <input type="radio" id="answer2" name="question1" value="false2"/>
                <label for="answer2" id="answer20">מתן דגשים לביצוע</label>
            </div>
            <div>
                <input type="radio" id="answer3" name="question1" value="false3"/>
                <label for="answer3" id="answer30">בדיקת הבנה</label>
            </div>
            <div>
                <input type="radio" id="answer4" name="question1" value="true4"/>
                <label for="answer4" id="answer40">שיחה אישית</label>
            </div>
            </fieldset>
            <br />
            <fieldset id="que2">
            <legend>מהו העיקרון שלא קיים בשלב התדריך?</legend>

            <div>
                <input type="radio" id="answer5" name="question2" value="true5"/>
                <label for="ans1" id="answer50">פירוט ברישום</label>
            </div>

            <div>
                <input type="radio" id="answer6" name="question2" value="false6"/>
                <label for="ans2" id="answer60">סדר הגיוני</label>
            </div>
            <div>
                <input type="radio" id="answer7" name="question2" value="false7"/>
                <label for="ans3" id="answer70">עירור מוטיבציה</label>
            </div>
            <div>
                <input type="radio" id="answer8" name="question2" value="false8"/>
                <label for="answer8" id="answer80">גורמי סביבה ומסגרת</label>
            </div>
            </fieldset>
           <br>
            <button v-if="count === 0" id="check" @click="checkAnswer">בדיקה</button>
            <button v-if="count === 1" id="continue" @click="BackToHomePage">המשך</button>
            
        </div>
    </div>
 
</template>

<script>

import { ref } from 'vue';


export default {
  name: "step-two",
  components: {

  },
  mounted() {
    this.stopTimer = true;
    var cards = document.querySelectorAll('.card');

    [...cards].forEach((card)=>{
    card.addEventListener( 'click', function() {
        card.classList.toggle('is-flipped');
    });
    });
  },
  data() {
    return {
        showQuestions:false,
        count: 0,
        counter: 0,
        countDown: 30,
        timeOver: false,
        counterr: 0,
        coun: 0,
        stopTimer: true,
    };
  },
  methods: {
    BackToHomePage() {
      for(let i=1;i<=8;i++) {
        document.getElementById(`answer${i}`).checked=false;
        document.getElementById(`answer${i}0`).style.color = "white";
      }
      document.getElementById("header").innerText = "בוחן פתע! יש לך 30 שניות  לענות נכון על השאלות";
      this.$emit("finish-stop-two");
    },
    showQuestion() {
        this.showQuestions=true;
        this.countDownTimer();
    },
    countDownTimer() {
                if(this.countDown > 0 && this.stopTimer) {
                    setTimeout(() => {
                        this.countDown -= 1;
                        this.countDownTimer();
                    }, 1000)
                } else {
                    this.timeOver=true;
                    if(this.count !== 1 ) {
                        document.getElementById("header").innerText = "הזמן אזל! התשובות הנכונות מסומנות בירוק";
                        document.getElementById("answer40").style.color = "green";
                        document.getElementById("answer50").style.color = "green";
                        this.count=1;
                    }
                    
                }
                
            },
    checkAnswer(){
      this.counter=0;
      this.counterr=0;
      this.coun++;
      for(let i=1;i<9;i++) {
        if(document.getElementById(`answer${i}`).checked && (document.getElementById(`answer${i}`).value === "true4" || document.getElementById(`answer${i}`).value === "true5")) {
          document.getElementById(`answer${i}0`).style.color = "green";
          this.counter++;
        } else if(document.getElementById(`answer${i}`).checked) {
          console.log(`answer${i}0`);
          document.getElementById(`answer${i}0`).style.color = "red";
          this.counterr=1;
        }

        
      }
      if(this.counter === 2) {
        this.count = 1;
        document.getElementById("header").innerText = "נכון מאוד, תשובה נכונה";
        // this.countDown = 0;                                                                                                                                                   
        this.stopTimer = false;
      }else if(this.counter < 2) {
        document.getElementById("header").innerText = "תשובה לא נכונה , נסו שנית";
        
      } 
      else if(this.coun === 2) {
  
        this.count = 1;
        document.getElementById("header").innerText= "לא נורא, העיקר שתלמד/י מהטעויות";
        document.getElementById("answer40").style.color = "green";
        document.getElementById("answer50").style.color = "green";
      }
    },
    
  }
};
</script>


<style scoped>
#step-two {
  text-align: center;
  display: flow;
  background-color: #e9c46a;
  min-height: 100vh;
  direction: rtl;
  /* padding: 42px; */
}
.starting {
  margin: 20px;
}
#header {
  font-family: "ellinia-bold";
  color: #e76f51;
  font-size: 6.5vmin;
}
.scene {
    width: 90vw;
    height: 30vh;
    margin: -50px 22px;
    perspective: 100vw;
    display: flex;
    flex-wrap: wrap;
}
#que1 {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 10px;
  font-size: 6vmin;
}
#que2 {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 10px;
  font-size: 6vmin;
}
.card {
  position: relative;
  width: 100%;
  height: 100%;
  cursor: pointer;
  transform-style: preserve-3d;
  transform-origin: center right;
  transition: transform 1s;
}

.card.is-flipped {
  transform: translateX(-70%) rotateY(-180deg);
}

.card__face {
  position: absolute;
  width: 59%;
  left: 50%;
  transform: translateX(-50%);
  height: 65%;
  display: flex;
  line-height: 6vh;
  color: white;
  text-align: center;
  font-weight: bold;
  font-size: 6vmin;
  backface-visibility: hidden;
  align-items: center;
}

.card__face--front {
  background: #f4a261;
  display: flex;
  justify-content: center;
}

.card__face--back {
  background: #e76f51;
  transform: rotateY(180deg);
}
.frame {
    width: 84vw;
    height: 10%;
    border: 2px solid white;
    border-radius: 30px;
    margin: 8%;
    font-size: 6vmin;
}
#some_div {
  position: absolute;
    top: 0%;
    left: 5%;
    font-size: 9vmin;
}
button {
    border-radius: 8px;
    border: 1px solid transparent;
    padding: 10px;
    font-size: 5vmin;
    font-weight: bold;
    background-color: #1a1a1a;
    cursor: pointer;
    transition: border-color 0.25s;
    color: #e9c46a;
    background-color: #e76f51;
    border-radius: 0;
    margin: -20px;
}
legend {
  font-family: "ellinia-bold";
    font-size: 7vmin;
    border: 0;
    color: inherit;
    display: table;
    max-width: 100%;
    white-space: normal;
    max-width: 70%;
    height: 54%;
    padding: 0%;
}
#step-two-questions {
  padding: 30px;
}
</style>