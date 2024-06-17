<template>
  <div id="step-six">
    <p class="bold-header">השלב האחרון במעגל החניכה הינו סיכום והפקת לקחים</p><br />
    <p>מטרתו להביא לייעול עצמי של החונך לקראת החניכה הבאה<br /><br />החונך מבצע מעין סיכום עם עצמו<br /> איך תיפקד כחונך ומבצע הפקת לקחים לקראת החניכה הבאה</p>
  <button id="continu" @click="BackToHomePage">המשך</button>
  </div>
</template>

<script>
import { ref } from 'vue';
export default {
  name: "step-six",
  components: {

  },
  data() {
    return {
        
    };
  },
  methods: {
    BackToHomePage() {
      this.$emit("finish-stop-six");

    },
  }
};
</script>


<style scoped>
.bold-header {
  font-family: "ellinia-bold";
}
button {
    border-radius: 8px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 1em;
    font-weight: 500;
    background-color: #2a9d8f;
    cursor: pointer;
    transition: border-color 0.25s;
    border-radius: 0;
    margin: 5%;
}
</style>