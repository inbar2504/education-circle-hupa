<template>
    <div id="ex6">
        <h2 id="you-right">🎉נכון,כל הכבוד🎉</h2>
        <h2 id="try-again">&#x274C;תשובה לא נכונה, נסו שנית &#x274C; </h2>
        <br /><br>
        <h2 id="header-bold">לחץ על השלבים בתהליך העיבוד לפי הסדר שלהם</h2>
        <br />
        <div class="same-div">
            <h1 id="num-10"></h1>
            <button class = "optional" id= "num-1" value="not-press" @click = "ratedAnswer('num-1')">איתור דוגמאות</button>
        </div>
        
        <div>
            <h1 id= "num-20"></h1>
            <button class = "optional" id= "num-2" value="not-press" @click = "ratedAnswer('num-2')">איתור מכנה משותף לסימפטומים שונים</button>
        </div>
        
        <div>
            <h1 id= "num-30"></h1>
            <button class = "optional" id= "num-3" value="not-press" @click = "ratedAnswer('num-3')">בחירת 2 תופעות לשימור ו2 תופעות לשימור</button>
        </div>
       
        <div>
            <h1 id= "num-40"></h1>
            <button class = "optional" id= "num-4" value="not-press" @click = "ratedAnswer('num-4')">ניסוח תופעות</button>
        </div>
       
        <div>
            <h1 id="num-50"></h1>
            <button class = "optional" id="num-5" value="not-press" @click = "ratedAnswer('num-5')">כתיבת הערות במידה ויש</button>
        </div>
       <div id="show-answer">
        <br /><br />
            ראינו שמעט התקשית- להלן התשובות<br/>
            שלב 1-איתור דוגמאות<br />
            שלב 2-איתור מכנה משותף לסימפטומים שונים<br />
            שלב 3-בחירת 2 תופעות לשימור ו2 תופעות לשימור<br/>
            שלב 4-ניסוח תופעות<br />
            שלב 5-כתיבת הערות במידה ויש<br />
            <br /><br/>
            <button @click="nextQuestion">המשך</button>
       </div>
       <br />
        <button @click="checkAnswer" id="check">בדיקה</button>
        <button @click="nextQuestion" id="countinu">המשך</button>
        <br />
    </div>
</template>

<script>

import { ref } from "vue";

export default {
    name: "ex6",
    components: {
        
    },
    data() {
        return {
            idNumber: 0,
            countAnswer: 0,
            IsWrong: false,
            countWrong: 0,
        };
    },
    methods: {
        ratedAnswer(idNumber) {
            if(document.getElementById(idNumber).value == "not-press") {
                this.countAnswer++;
                document.getElementById(idNumber).value = "press";
                document.getElementById(idNumber).name = this.countAnswer;
                document.getElementById(`${idNumber}0`).innerText=this.countAnswer;
            } else if(document.getElementById(idNumber).value == "press" && document.getElementById(idNumber).name == this.countAnswer) { 
                document.getElementById(idNumber).value = "not-press";
                document.getElementById(`${idNumber}0`).innerText="";
                document.getElementById(idNumber).name = 0;
                this.countAnswer--;
                    

            }
            if(this.countAnswer == 5) {
                document.getElementById("check").style.display = "block";
            }   
        },
        nextQuestion(){
            this.$emit('finish-question-six');
        },
        checkAnswer() {
            this.IsWrong = false;
            for(let i=1;i<=5;i++) {
                if(document.getElementById(`num-${i}`).name !== String(i)) {
                    this.IsWrong = true;
                    document.getElementById(`num-${i}`).style.color = "red";
                } else {
                    document.getElementById(`num-${i}`).style.color = "green";
                }
            }
            if(this.IsWrong == true) {
                this.countWrong++;
                document.getElementById("try-again").style.display = "block";

            } else {
                document.getElementById("you-right").style.display = "block";
                document.getElementById("check").style.display = "none";
                document.getElementById("countinu").style.display = "block";
                document.getElementById("try-again").style.display = "none";

            } if(this.countWrong == 2) {
                document.getElementById("show-answer").style.display = "block";
            }
        },

    }
};
</script>

<style scoped>
#ex6 {
    /* padding: 10px; */
    background-color: #e76f51;
    min-width: 100vw;
    min-height: 100vh;

}

#header-bold {
    font-family: "assistant-bold";
    font-size: 7vmin;
}
h1 {
    position: relative;
    left: 76vw;
    top: 8vh;
    width: 10vw;
    height: 5vh;
    font-size: 7vmin;
}
.ans {
    margin: 2%;
    width: 85%;
    border-radius: 33px;
    font-size: 5vmin;
}
#you-right {
    display: none;
    position: absolute;
    top: 15vh;
    left: 50%;
    transform: translateX(-50%);
    width: 90vw;
    font-family: 'assistant-bold';
    font-size: 8vmin;
}
#countinu {
    display: none;
}
#try-again {
    display: none;
    position: absolute;
    top: 14vh;
    left: 50%;
    transform: translateX(-50%);
    min-width: 100%;
    font-family: 'assistant-bold';
    font-size: 7vmin;
}
.optional {
    width: 53vw;
    height: 11vh;
    font-size: 5vmin;
    padding: 4px;
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    justify-content: center;
    align-content: center;
    position: relative;
    transform: translateX(-50%);
    left: 50%;
    margin: -10px;
}
#check {
    display: none;
}
#show-answer {
    display: none;
    width: 70vw;
    height: 80vh;
    background-color: rgb(255, 216, 243);
    font-size: 7vmin;
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
    padding: 5px;
}
button {
    border-radius: 0px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 6vmin;
    font-weight: 500;
    background-color: #e9c46a;
    cursor: pointer;
    transition: border-color 0.25s;
    position: relative;
    left: 50%;
    bottom: -20%;
    transform: translateX(-50%);
}
</style>