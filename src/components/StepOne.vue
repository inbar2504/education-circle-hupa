<template>
  <div id="step-one">
    <div v-if="!showQuestion">
      <!-- <br /> -->
      <p class="bold-font">השלב הראשון הינו - הכנה עצמית</p>
      <p>
        שלב ההכנה העצמית הינו כולו של החונך, מטרת השלב הזה היא הכנת החונך לתהליך
        החניכה , על מנת שישיג את כל המטרות שקבע.
      </p><br />
      <p>
        זה מתחלק לשלושה היבטים<br />
        הבנה ותכנון המשימה o<br />
        למידת מאפייני הנחנך o<br />
        למידת תכונות הנחנך o
      </p>
      <button @click="showQuestion = true">המשך</button>
    </div>
    <div v-if="showQuestion">
      <p>נניח ומודיעים לך שהינך צריך להתחיל חניכה לחייל חדש - סמן מה היית בודק כחלק משלב ההכנה העצמית</p>
  <h2 id="try-again">נסו שנית</h2>
      <br />
      <div id="field">

        <div>
          <input type="checkbox" id="horns0" name="true" />
          <label class = "answers" for="horns0" id="horns00">מה הידע שלו</label>
        </div>

        <div>
          <input type="checkbox" id="horns1" name="true" />
          <label class = "answers" for="horns1" id="horns10">איזה נסיון יש לו</label>
        </div>
        <div>
          <input type="checkbox" id="horns2" name="true" />
          <label class = "answers" for="horns2" id="horns20">מה מקומו בתהליך ההכשרה</label>
        </div>
        <div>
          <input type="checkbox" id="horns3" name="true" />
          <label class = "answers" for="horns3" id="horns30">אבחון תכונותיו</label>
        </div>
        <div>
          <input type="checkbox" id="horns4" name="true" />
          <label class = "answers" for="horns4" id="horns40">מה המשימה</label>
        </div>
        <div>
          <input type="checkbox" id="horns5" name="false" />
          <label class = "answers" for="horns5" id="horns50">איפה הוא גר</label>
        </div>
      </div>
      <button v-if="count === 0" id="check" @click="checkAnswer">בדיקה</button>
      <button v-if="count === 1" id="continue" @click="BackToHomePage">
        המשך
      </button>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "step-one",
  components: {},
  data() {
    return {
      showQuestion: false,
      count: 0,
      counter: 0,
      coun: 0,
    };
  },
 
  methods: {
    BackToHomePage() {
      for(let i=0;i<6;i++) {
        document.getElementById(`horns${i}0`).style.color="white";
        document.getElementById(`horns${i}`).checked = false;
      }
      this.$emit("finish-stop-one",1);
    },
    checkAnswer() {
      this.counter++;
      this.coun = 0;
      document.getElementById("try-again").style.display = "none";
      for(let i=0;i<6;i++) {
        if(this.counter === 1) {
            if(document.getElementById(`horns${i}`).checked && document.getElementById(`horns${i}`).name === "true") {
              document.getElementById(`horns${i}0`).style.color="green";
              this.coun++;
            }else if(document.getElementById(`horns${i}`).checked && document.getElementById(`horns${i}`).name === "false") {
              document.getElementById(`horns${i}0`).style.color="red";
            }
        }
      
        else if(this.counter === 2) {
          if(document.getElementById(`horns${i}`).name === "true") {
            document.getElementById(`horns${i}0`).style.color="green";

          }
          if(document.getElementById(`horns${i}`).name === "false") {
            document.getElementById(`horns${i}0`).style.color="red";
          }
          this.count = 1;
          document.getElementById("try-again").style.display = "none";
        }
       
      }
      if(this.coun === 5) {
          this.count = 1;
          document.getElementById("try-again").style.display = "none";
        } else if(this.coun !== 5 && this.counter !== 2) {
          document.getElementById("try-again").style.display = "block";
        }
    }
  },
};
</script>

<style scoped>
/* * {
  max-width: 90vw;

} */

#step-one {
  font-family: "assistant";
    font-size: 8vmin;
    background-color: #f4a261;
    text-align: center;
    display: flow;
    width: 100%;
    height: 100vh;
    padding: 50px;
}
.checkbox {
  width: 2%;
  height: 2%;
}
.answers {
  font-size: 6vmin;
}
button {
    border: 1px solid transparent;
    padding: 15px;
    font-size: 5vmin;
    font-weight: 500;
    background-color: #1a1a1a;
    cursor: pointer;
    transition: border-color 0.25s;
    color: #e76f51;
    background-color: #e9c46a;
    margin: 15px;
    border-radius: 0;
}
#field {
  direction: rtl;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.bold-font {
  font-family: "assistant-bold";
}

#try-again {
    display: none;
    position: absolute;
    top: 33vh;
    left: 50%;
    transform: translateX(-50%);
    min-width: 100%;
    font-family: 'assistant-bold';
    font-size: 8vmin;
    color: #f44336;

}
</style>
