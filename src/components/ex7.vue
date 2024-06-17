<template>
    <div id="ex7">
      <div id="orange-line">
      <p id="header">סוף התרגול</p>
      </div>
      <div id="yellow-line"></div>
      <div id="blue-line"></div>
      <div id="dark-blue-line">
          <br /><br />
        <p id="bold-header">האם ברצונך</p>
        <!-- <button @click="endLomda" class="buttons">לסיים את הלומדה</button> -->
        <button @click="backToStart" class="buttons">לחזור לתחילת הלומדה</button>
      <!-- <img src="./assets/red-book-1.png" id="red-book-1"/>
      <img src="./assets/orange-book-1.png" id="orange-book-1"/>
      <img src="./assets/yellow-book-1.png" id="yellow-book-1"/>
      <img src="./assets/blue-book-1.png" id="blue-book-1"/>
      <img src="./assets/red-book-2.png" id="red-book-2"/>
      <img src="./assets/orange-book-2.png" id="orange-book-2"/>
      <div>
        <img src="./assets/man.png" id="man"/>
      </div>
      <img src="./assets/yellow-book-2.png" id="yellow-book-2"/> -->
    </div>
    <!-- </div> -->
    
    <!-- <button  @click="showHome" id="btn">התחלה</button> -->

    </div>
<!-- <div class="row">
    <div class="col-3">
      <h3>מטרת המשימה</h3>
      <draggable
        class="list-group"
        :list="list1"
        group="people"
        @change="log"
        itemKey="name"
      >
        <template #item="{ element, index }">
          <div class="list-group-item">{{ element.name }} {{ index }}</div>
        </template>
      </draggable>
    </div>

    <div class="col-3">
      <h3>מתווה המשימה</h3>
      <draggable
        class="list-group"
        :list="list2"
        group="people"
        @change="log"
        itemKey="name"
      >
        <template #item="{ element, index }">
        </template>
      </draggable>
    </div>

    <div class="col-3">
      <h3>דגשים</h3>
      <draggable
        class="list-group"
        :list="list2"
        group="people"
        @change="log"
        itemKey="name"
      >
        <template #item="{ element, index }">
        </template>
      </draggable>
    </div>

    <div class="col-3">
      <h3>בדיקת הבנה</h3>
      <draggable
        class="list-group"
        :list="list1"
        group="people"
        @change="log"
        itemKey="name"
      >
        <template #item="{ element, index }">
        </template>
      </draggable>
    </div>

    <div class="col-3">
      <h3>אני מאמין של החונך</h3>
      <draggable
        class="list-group"
        :list="list2"
        group="people"
        @change="log"
        itemKey="name"
      >
        <template #item="{ element, index }">
        </template>
      </draggable>
    </div>

    <div class="col-3">
      <h3>מחסן שלבים</h3>
      <draggable
        class="list-group"
        :list="list1"
        group="people"
        @change="log"
        itemKey="name"
      >
        <template #item="{ element, index }">
          <div class="list-group-item">{{ element.name }} {{ index }}</div>
        </template>
      </draggable>
    </div>
  </div> -->
</template>

<script>

import { ref } from "vue";
// import draggable from 'vuedraggable';
import draggable from "vuedraggable";

export default {
    name: "ex7",
    display: "ex7",
    order: 1,
    components: {
        draggable,
    },
    data() {
        return {
            list1: [
        { name: "", id: 1 },
        { name: "מתווה המשימה", id: 2 },
        { name: "דגשים", id: 3 },
        { name: "בדיקת הכנה", id: 4 },
        { name: "אני מאמין של החונך", id: 5 },
      ],
                
        }
    },
    methods: {
        backToStart() {
            this.$emit("back-to-start-page");
        },



        add: function() {
      this.list.push({ name: "Juan" });
    },
    replace: function() {
      this.list = [{ name: "Edgard" }];
    },
    clone: function(el) {
      return {
        name: el.name + " cloned"
      };
    },
    log: function(evt) {
      window.console.log(evt);
    }

    },

};
</script>

<style scoped>
body {
  /* background-size: 100% 100%; */
  background-color: #e76f51;


}
#bold-header {
    font-family: 'assistant-bold';
    font-size: 8vmin;
}
#ex7 {
  overflow-x: hidden;
  font-family: "assistant";
}
#btn1 {
  font-size: 10vmin;
    z-index: 10;
    background-color: bisque;
    position: absolute;
    bottom: 3vh;
    border-radius: 0px;
    left: 10vw;
    padding: 20px;
}
#btn2 {
  font-size: 10vmin;
    z-index: 10;
    background-color: bisque;
    position: absolute;
    top: 85.5vh;
    border-radius: 0px;
    padding: 20px;
    right: 10vw;
}
#btn {
  font-size: 10vmin;
  z-index: 10;
  background-color: bisque;
  position: absolute;
  top: 85.5vh;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 0px;
}
#header {
  font-size: 11vmin;
  margin: -12px;
}
#orange-line {
  background-color: #f4a261;
    position: absolute;
    top: 10%;
    left: 0%;
    width: 100vw;
    height: 72vh;
    z-index:2;
}
#yellow-line {
  background-color: #e9c46a;
    position: absolute;
    top: 15%;
    left: 0%;
    width: 100vw;
    height: 60vh;
    z-index:3;
}
#blue-line {
  background-color: #2a9d8f;
  position: absolute;
  top: 19%;
  left: 0%;
  width: 100vw;
  height: 47vh;
  z-index: 3;
}
#dark-blue-line {
  background-color: #264653;
  position: absolute;
  top: 24%;
  left: 0%;
  width: 100vw;
  height: 40vh;
  z-index: 4;
}
#red-book-1 {
  position: absolute;
    top: 13%;
    width: 20%;
    left: 38%;
    z-index: 3;
}
#orange-book-1 {
  position: absolute;
  top: 17%;
  width: 32%;
  left: 42%;
  z-index: 1;
}
#yellow-book-1 {
  position: absolute;
    top: 37%;
    width: 42%;
    left: 44%;
}
#blue-book-1 {
  position: absolute; 
  top: 47%; 
  width: 38%; 
  left: 38%;
}
#red-book-2 {
  position: absolute;
    top: 50%;
    width: 21%;
    left: 32%;
}
#orange-book-2 {
  position: absolute;
    top: 49%;
    width: 34%;
    left: 14%;
}
#yellow-book-2 {
  position: absolute;
    top: 44%;
    width: 43%;
    left: 5%;
}
#man {
  position: absolute;
  width: 15%;
  z-index: 3;
  top: 7vh;
  left: 18vw;

}
.draggable-list {
  background: #3f51b5;
  color: #fff;
  border: 1px solid;
  height: 50vh;
}
.list-item {
  margin: 10px;
  padding: 40px;
  cursor: pointer;
  font-size: 18px;
  border-radius: 5px;
  background: #f44336;
  display: inline-block;
}
.buttons {
    border-radius: 0px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 1em;
    font-weight: 500;
    background-color: #f4a261;
    cursor: pointer;
    transition: border-color 0.25s;
    position: relative;
    top: 2vh;
    width: 80vw;
    margin: 3%;
    font-size: 6vmin;
    font-family: 'assistant-bold';
}
</style>