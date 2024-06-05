<template>
  <div id="exercises">
    <ex1 v-if = "question === 1" @finish-question-one = "question = 2"></ex1>
    <ex2 v-if = "question === 2" @finish-question-two = "question = 3"></ex2>
    <ex3 v-if = "question === 3" @finish-question-three = "question = 4"></ex3>
    <ex4 v-if= "question === 4" @finish-question-four = "question = 5"></ex4>
    <ex5 v-if= "question === 5" @finish-question-five = "question = 6"></ex5>
    <ex6 v-if = "question === 6" @finish-question-six = "question = 7"></ex6>
    <ex7 v-if = "question === 7" @back-to-start-page= "toApp"></ex7>
    <app v-if ="question === 0"></app>
    <!-- <ex7 v-if = "question === 7" @finish-question-seven = "question = 8"></ex7> -->
  </div>
</template>

<script>
import { ref } from 'vue';

import ex1 from './ex1.vue';
import ex2 from './ex2.vue';
import ex3 from './ex3.vue';
import ex4 from './ex4.vue';
import ex5 from './ex5.vue';
import ex6 from './ex6.vue';
import ex7 from './ex7.vue';


export default {
  name: "exercises",
  
  components: {
    ex1,
    ex2,
    ex3,
    ex4,
    ex5,
    ex6,
    ex7,
    
  },
  data() {
    return {
      question: 1,
   
    }
      
  },
 
  methods: {
    toApp() {
      this.question = 1;
      this.$emit("showStart");
    }
  }
  };


</script>


<style scoped>

</style>
