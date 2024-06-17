<template>
    <div id="ex2">
        <h2 id="you-right">🎉נכון,כל הכבוד🎉</h2>
        <h2 id="try-again">&#x274C;תשובה לא נכונה, נסו שנית &#x274C; </h2>
        <h2 id="wrong-twice">לא נורא, העיקר שתלמד/י מהטעויות</h2>
        <br /><br>
        <div id="question">
            <h2 id="bold-header">?מה הפירוש של מת"י</h2>
            <br />
            <button id="right" @click="checkAnswer('right')" class="ans">מודעות ,תפיסה ויישום</button>
            <button id= "wrong1" @click="checkAnswer('wrong')" class="ans">משמעת,תפיסה ויישום</button>
            <button id= "wrong2" @click="checkAnswer('wrong')" class="ans">משמעות, תפקיד ויחס</button>
            <button id= "wrong3" @click="checkAnswer('wrong')" class="ans">משמעות, תפקיד ויישום</button>
             <button @click="nextQuestion" id="countinu">המשך</button>
        </div>
        
    </div>
</template>


<script>

import { ref } from "vue";

export default {
    name: "ex2",
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
            this.$emit('finish-question-two');
        }

    }
};
</script>

<style scoped>
#ex2 {
    background-color: #f4a261;
    min-height: 100vh;
    min-width: 100vw;
    /* padding: 50%; */

}
.ans {
    margin: 2%;
    width: 85%;
    border-radius: 33px;
    font-size: 5vmin;
    background-color: #2a9d8f;
}
#question {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
    min-width: 90%;
}
#you-right {
    display: none;
    /* display: none; */
    position: absolute;
    top: 14vh;
    left: 50%;
    transform: translateX(-50%);
    min-width: 100%;
    font-family: 'ellinia-bold';
    font-size: 7vmin;
}
#countinu {
    display: none;
    border-radius: 0;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 6vmin;
    font-weight: 500;
    background-color: #264653;
    cursor: pointer;
    transition: border-color 0.25s;
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 50vh;
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
    top: 14vh;
    left: 50%;
    transform: translateX(-50%);
    min-width: 100%;
    font-family: 'ellinia-bold';
    font-size: 7vmin;
}
#bold-header {
    font-family: 'ellinia-bold';
    font-size: 8vmin;
}
</style>
