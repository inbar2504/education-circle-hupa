<template>
    <div id="ex1">
      <h3 id="right">🎉 נכון,כל הכבוד 🎉</h3>
        <h3 id="wrong">נסה שוב... תשובה לא נכונה</h3>
        <h4>סדרו את שלבי מעגל החניכה לפי הסדר מלמעלה ללמטה על ידי גרירה שלהם</h4>
        <div class="row">
        <div class="col-2">
          <div class="form-group">
            <div
              class="btn-group-vertical buttons"
              role="group"
              aria-label="Basic example">
            </div>

            
          </div>
        </div>

        <div>

      <draggable
        :list="list"
        :disabled="!enabled"
        item-key="name"
        class="list-group"
        ghost-class="ghost"
        :move="checkMove"
        @start="dragging = true"
        @end="dragging = false"
      >
        <template #item="{ element }">
          <div class="list-group-item" :class="{ 'not-draggable': !enabled }">
            {{ element.name }}
          </div>
        </template>
      </draggable>
    </div>

    <!-- <rawDisplayer class="col-3" :value="list" title="List" /> -->

  </div>
  <br /><br />
  <button v-if="checking" @click="checkAnswer">בדיקה</button> 
  <button v-if="continue" @click="nextQuestion" >המשך</button>
  <div id="showAnswer">
    <h4>ראינו שקצת התקשית אז להלן התשובות</h4>
    <p>הכנה עצמית</p>
    <p>תדריך</p>
    <p>תצפית</p>
    <p>עיבוד</p>
    <p>משוב</p>
    <p>סיכום והפקת לקחים</p>

    <button @click="nextQuestion" >המשך</button>
  </div>
    </div>
</template>

<script>
import draggable from 'vuedraggable';
import { ref } from "vue";

let id = 1;

export default {
  name: "ex1",
  display: "Simple",
  order: 0,
  components: {
    draggable,
  },
  data() {
    return {
      counts:0,
      enabled: true,
      count: 0,
      checking: true,
      continue: false,
      list: [
        { name: "הכנה עצמית", id: 0 },
        { name: "תדריך", id: 1 },
        { name: "תצפית", id: 2 },
        { name: "עיבוד", id: 3 },
        { name: "משוב", id: 4 },
        { name: "סיכום והפקת לקחים", id: 5 },
      ],
      list_update: [
        { name: "הכנה עצמית", id: 0 },
        { name: "תדריך", id: 1 },
        { name: "תצפית", id: 2 },
        { name: "עיבוד", id: 3 },
        { name: "משוב", id: 4 },
        { name: "סיכום והפקת לקחים", id: 5 },
      ],
      dragging: false,
    }
  },
  methods: {
    checkMove: function(e) {
      window.console.log("Future index: " + e.draggedContext.futureIndex);
    },
    checkAnswer() {
          this.count=0;
          while(this.count < 6 && this.count!==10){
              if(this.list[this.count].name === this.list_update[this.count].name) {
                  this.count++;
              } else {
                  this.count=10;
              }
          }
          if(this.count === 6) {
              document.getElementById("right").style.display="block";
              document.getElementById("wrong").style.display="none";
              this.continue = true;
              this.checking = false;
          } if(this.count === 10) {
              this.counts++;
              document.getElementById("wrong").style.display="block";
              document.getElementById("right").style.display="none";
          }
          if(this.counts === 2) {
            document.getElementById("showAnswer").style.display = "block";
          }
          
        },    
    nextQuestion() {
      this.$emit('finish-question-one');
    },

    
  }
};
</script>
<style scoped>
#ex1 {
  font-size: 7vmin;
    min-width: 72vw;
    position: absolute;
    top: 16vh;
    left: 50%;
    transform: translateX(-50%);
}
button {
    border-radius: 0;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 1em;
    font-weight: 500;
    background-color: #264653;
    cursor: pointer;
    transition: border-color 0.25s;
}
.buttons {
  margin-top: 35px;

}
.list-group-item {
  border: 2px solid;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-content: center;
  font-family: 'assistant-bold';
}
.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}

.not-draggable {
  cursor: no-drop;
}
#right {
  display: none;
  position: absolute;
  top: -9vh;
  left: 50%;
  transform: translateX(-50%);
  width: 80vw;
  font-family: 'assistant-bold';

}
#wrong {
  position: absolute;
  top: -9vh;
  left: 50%;
  transform: translateX(-50%);
  width: 80vw;
  font-family: 'assistant-bold';
  display: none;
}
#showAnswer {
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%,-50%);
  width: 75%;
  height: 80%;
  background-color: pink;
  display: none;
  
}
</style>