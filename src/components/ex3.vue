<template>
    <div id="ex3">
        <h2 id="bold-header">לפניכם רשימת ציטוטים מדף תצפית- סמנו עבור כל ציטוט האם הוא עובדתי או שיפוטי</h2><br /><br />
        <div><br />
            <h2>עומדת בקרבת מקום, מוציא פנקס ומתחיל לרשום</h2><br />
        <div class="select" id="ques1">
        <select name="format" id="format1">
            <option selected disabled>לחץ לבחירה</option>
            <option id="que1" value="true">עובדתי</option>
            <option value="false">שיפוטי</option>
        </select>
        </div>
        </div>
        <div><br />
            <h2>מבקשת משמרית עזרה כי יודע שהיא תמיד יכולה מוכנה לוותר לו</h2><br />
        <div class="select" id="ques2">
        <select name="format" id="format2">
            <option selected disabled>לחץ לבחירה</option>
            <option value="false">עובדתי</option>
            <option  id="que2" value="true">שיפוטי</option>
        </select>
        </div>
        </div>
        <div><br />
            <h2>מסביר בצורה מדוקדקת ולפרטים כיצד יש להעמיד את המסדר</h2><br />
        <div class="select" id="ques3">
        <select name="format" id="format3">
            <option selected disabled>לחץ לבחירה</option>
            <option value="false">עובדתי</option>
            <option  id="que3" value="true">שיפוטי</option>
        </select>
        </div>
        </div>
        <div><br />
            <h2>מבקש משמרית עזרה כי יודע שהיא תמיד יכולה מוכנה לוותר לו</h2><br />
        <div class="select" id="ques4">
        <select name="format" id="format4">
            <option selected disabled>לחץ לבחירה</option>
            <option value="false">עובדתי</option>
            <option  id="que4" value="true">שיפוטי</option>
        </select>
        </div>
        </div>
        <div><br />
            <h2>מסביר כי לכל המסדר יהיו 20 דקות</h2><br />
        <div class="select" id="ques5">
        <select name="format" id="format5">
            <option selected disabled>לחץ לבחירה</option>
            <option  id="que5" value="true">עובדתי</option>
            <option value="false">שיפוטי</option>
        </select>
        </div>
        </div>
        <div><br />
            <h2>אומר כי הוא מצפה לעבודת צוות , תקתוק ויסודיות במסדר</h2><br />
        <div class="select" id="ques6">
        <select name="format" id="format6">
            <option selected disabled>לחץ לבחירה</option>
            <option  id="que6" value="true">עובדתי</option>
            <option value="false">שיפוטי</option>
        </select>
        </div>
        </div>
        <div><br />
            <h2>סוף זמן אוכל, טירונים נותנים הקשב , מ”כ משחרר ושואל אם כולם אכלו</h2><br />
        <div class="select" id="ques7">
        <select name="format" id="format7">
            <option selected disabled>לחץ לבחירה</option>
            <option  id="que7" value="true">עובדתי</option>
            <option value="false">שיפוטי</option>
        </select>
        </div>
        </div>
        <div><br />
            <h2>אף אחד לא מודה, הוא מתעצבן</h2><br />
        <div class="select" id="ques8">
        <select name="format" id="format8">
            <option selected disabled>לחץ לבחירה</option>
            <option value="false">עובדתי</option>
            <option  id="que8" value="true">שיפוטי</option>
        </select>
        </div>
        </div>
        <div><br />
            <h2>אומר ליריב בכעס ובהתנשאות שישאיר לו את תפקיד המפקד על הכיתה</h2><br />
        <div class="select" id="ques9">
        <select name="format" id="format9">
            <option selected disabled>לחץ לבחירה</option>
            <option value="false">עובדתי</option>
            <option  id="que9" value="true">שיפוטי</option>
        </select>
        </div>
        </div><br />
        <button id = "check" @click="checkAnswers">בדיקה</button>
        <button id = "countinue" @click="nextQuestion">המשך</button>
    </div>
</template>

<script>

import { ref } from "vue";

export default {
    name: "ex3",
    components: {
        
    },
    data() {
        return {

        };
    },
    mounted() {
        for(let i=1;i<10;i++) {        
            document.getElementById(`format${i}`).style.color="black";
        }
    },
    methods: {
        checkAnswers() {
            for(let i=1;i<10;i++) {
                if(document.getElementById(`que${i}`).selected) {
                    document.getElementById(`format${i}`).style.color="green";
                } else {
                    document.getElementById(`format${i}`).style.color="red";
                }
            }
           document.getElementById("check").style.display = "none";
           document.getElementById("countinue").style.display = "block";
        },
        nextQuestion() {
            this.$emit("finish-question-three");
        }

    }
};
</script>

<style scoped>
#ex3 {
   display: flex;
   flex-direction: column;
   justify-content: center;
   align-items: center;
   min-height: 100vh;
   min-width: 100vw;
   background-color: #2a9d8f;
   color: #120000;
   padding: 50px;
   /* max-width: 90vw; */
}
#bold-header {
    font-family: "assistant-bold";
}
select {

   -webkit-appearance:none;
   -moz-appearance:none;
   -ms-appearance:none;
   appearance:none;
   outline:0;
   box-shadow:none;
   border:0!important;
   background: rgb(255, 255, 255);
   background-image: none;
   flex: 1;
   padding: 0 .5em;
   color:#000000;
   cursor:pointer;
   font-size: 7vmin;
    text-align: center;
}
select::-ms-expand {
   display: none;
}
.select {
    position: relative;
    display: flex;
    width: 35vw;
    height: 3em;
    line-height: 3;
    background: #5c6664;
    overflow: hidden;
    border-radius: .25em;
    align-content: center;
    justify-content: center;
    align-items: center;
    flex-wrap: nowrap;
    flex-direction: column;
    left: 50%;
    transform: translateX(-50%);
    text-align: center;
}
.select::after {
   /* content: '\25BC'; */
   position: absolute;
   top: 0;
   right: 0;
   /* padding: 0 1em; */
   background: #2b2e2e;
   cursor:pointer;
   pointer-events:none;
   transition:.25s all ease;
}
#countinue {
    display: none;
}
/* .select:hover::after {
   color: #23b499;
} */
option {
    margin-left: -10vw;
    font-size: 3vmin;
    text-align: center;
    direction: rtl;
}
button {
    border-radius: 0px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 6vmin;
    font-weight: 500;
    background-color: #f4a261;
    cursor: pointer;
    transition: border-color 0.25s;
}


</style>