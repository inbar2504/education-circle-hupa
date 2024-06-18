<template>
    <div id="ex4">
        <h2 id="you-right">🎉נכון,כל הכבוד🎉</h2>
        <h2 id="try-again">&#x274C;תשובה לא נכונה, נסו שנית &#x274C; </h2>
        <h2 id="wrong-twice">לא נורא, העיקר שתלמד/י מהטעויות</h2>
        <br /><br>
        <div id="question">
            <h2 id="header-bold">מה הם השיקולים של התערבות ישירה</h2>
            <br />

            <button id= "wrong1" @click="checkAnswer('wrong')" class="ans">מיקום התרגיל בהכשרה,גיל הנחנך וחריגה מהוראות הבטיחות</button>
            <button id= "wrong2" @click="checkAnswer('wrong')" class="ans">פגיעה במטרות התרגיל וגיל הנחנך</button>
            <button id= "wrong3" @click="checkAnswer('wrong')" class="ans">פגיעה במטרות התרגיל,ומיקום התרגיל בהכשרה</button>
            <button id="right" @click="checkAnswer('right')" class="ans">מיקום התרגיל בהכשרה,פגיעה במטרות התרגיל, וגיל הנחנך</button>
        </div>
        
       <button @click="nextQuestion" id="countinu">המשך</button>
    </div>
</template>

<script>

import { ref } from "vue";

export default {
    name: "ex4",
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
            this.$emit('finish-question-four');
        }

    }
};
</script>

<style scoped>
#ex4 {
    background-color: #e9c46a;
    min-height: 100vh;
    min-width: 100vw;
}
#header-bold {
    font-family: "ellinia-bold";
    font-size: 7vmin;
    position: relative;
    top: 0vh;
}
.ans {
    margin: 2%;
    width: 70vw;
    border-radius: 33px;
    font-size: 5vmin;
    background-color: #2a9d8f;
}
#you-right {
    display: none;
    position: absolute;
    top: 8vh;
    left: 50%;
    transform: translateX(-50%);
    width: 90vw;
    font-family: 'ellinia-bold';
    font-size: 8vmin;
}
#countinu {
    display: none;
    position: relative;
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
    top: 8vh;
    left: 50%;
    transform: translateX(-50%);
    width: 90vw;
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
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
</style>