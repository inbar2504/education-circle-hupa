<template>
    <div id="ex5">
        <h2 id="you-right">🎉נכון,כל הכבוד🎉</h2>
        <h2 id="try-again">&#x274C;תשובה לא נכונה, נסו שנית &#x274C; </h2>
        <h2 id="wrong-twice">לא נורא, העיקר שתלמד/י מהטעויות</h2>
        <br /><br>
        <div id="question">
            <h2 id="header-bold">מה נרשום בדף תצפית</h2>
        <br />

        <button id= "wrong1" @click="checkAnswer('wrong')" class="ans">החניך קפץ</button>
        <button id= "wrong2" @click="checkAnswer('wrong')" class="ans">החניך גרוע בחומר</button>
        <button id= "wrong3" @click="checkAnswer('wrong')" class="ans">החניך לא מזהה קונפליקטים</button>
        <button id="right" @click="checkAnswer('right')" class="ans">החניך זחל בלילה , לאורך 100 מטר, תוך שמירה על גובה מינימאלי </button>
        </div>
        
       <button @click="nextQuestion" id="countinu">המשך</button>
    </div>
</template>

<script>

import { ref } from "vue";

export default {
    name: "ex5",
    components: {
        
    },
    data() {
        return {
            answer: '',
            countWrong: 0,
        };
    },
    methods: {
        checkAnswer(answer) {
            if(answer === 'right') {
                document.getElementById("you-right").style.display = "block";
                document.getElementById("right").style.backgroundColor = "green";
                document.getElementById("wrong1").style.backgroundColor = "red";
                document.getElementById("wrong2").style.backgroundColor = "red";
                document.getElementById("wrong3").style.backgroundColor = "red";
                document.getElementById("countinu").style.display = "block";
                document.getElementById("try-again").style.display = "none";
            } else {
                document.getElementById("try-again").style.display = "block";
                this.countWrong++;
            } if(this.countWrong == 2) {
                document.getElementById("try-again").style.display = "none";
                document.getElementById("wrong-twice").style.display = "block";
                document.getElementById("right").style.backgroundColor = "green";
                document.getElementById("wrong1").style.backgroundColor = "red";
                document.getElementById("wrong2").style.backgroundColor = "red";
                document.getElementById("wrong3").style.backgroundColor = "red";
                document.getElementById("countinu").style.display = "block";
            }
        },
        nextQuestion(){
            this.$emit('finish-question-five');
        }

    }
};
</script>

<style scoped>
#ex5 {
    background-color: #264653;
    min-height: 100vh;
    min-width: 100vw;
}
#header-bold {
    font-family: "ellinia-bold";
    font-size: 7vmin;
}
.ans {
    margin: 2%;
    width: 85%;
    border-radius: 33px;
    font-size: 5vmin;
    background-color: #e76f51;
}
#you-right {
    display: none;
    position: absolute;
    top: 10vh;
    left: 50%;
    transform: translateX(-50%);
    width: 90vw;
    font-family: 'ellinia-bold';
    font-size: 8vmin;
}
#countinu {
    display: none;
    position: absolute;
    top: 80vh;
    left: 50%;
    transform: translateX(-50%);
    border-radius: 0;
    font-size: 6vmin;
    background-color: #2a9d8f;
}
#try-again {
    display: none;
    position: absolute;
    top: 14vh;
    left: 50%;
    transform: translateX(-50%);
    min-width: 100%;
    font-family: 'ellinia-bold';
    font-size: 6vmin;

}
#wrong-twice {
    display: none;
    position: absolute;
    top: 10vh;
    left: 50%;
    transform: translateX(-50%);
    width: 90vw;
    font-family: 'ellinia-bold';
    font-size: 8vmin;
}
#question {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
    width: 90vw;
}
</style>