<template>
  <div id="step-three">
    <div>
      <p id="header">השלב השלישי הינו -תצפית</p>
      <p>
        ביצוע תצפית של החונך על התנסות הנחנך. בשלב זה נצפה בביצוע כדי לאסוף
        מקסימום אינפורמציה וביצוע בקרה על ביצועי החניך
      </p>
      <p>
        החונך אוסף את כל המידע שהוא יכול לגבי הנחנך.הוא ממלא “דף תצפית” גרדו את
        הריבוע על מנת לראות דוגמא לדף תצפית
      </p>
      <div id="scratching">
        <vue-scratchable
          v-slot="{ init }"
          :brushOptions="brush"
          :hideOptions="hide"
        >
          <div class="wrapper">
            <img
              id="scratch-img"
              src="../assets/scratchPage.jpg"
              @load="init()"
            />
          </div>
        </vue-scratchable>
      </div>
      <div>
        <br />
        <p>
          מיקום התצפית מורכב משלושה היבטים<br />
          החליקו שמאלה כדי לראותם
        </p>

        <swiper
          :slides-per-view="1"
          :space-between="50"
          @swiper="onSwiper"
          @slideChange="onSlideChange"
          :navigation="true"
          :modules="modules"
          class="mySwiper"
        >
          <swiper-slide class="card-slide">מינימום הפרעה לנחנך</swiper-slide>
          <swiper-slide class="card-slide">מינימום הפרעה לחניכים</swiper-slide>
          <swiper-slide class="card-slide">מקסימום איסוף מידע</swiper-slide>
        </swiper>
      </div>
      <div>
        <br />
        <h2>עקרונות התצפית</h2>
        <p>אובייקטיביות ומהימנות</p>
        <p>פירוט ברישום</p>
        <p>רלוונטיות ופרקטיות</p>
      </div>
      <div>
        <br />
        <h2 id="header-3">התערבות בתצפית</h2>
        <p>לפעמים נתערב במהלך התצפית, יש 2 סוגי התערבויות</p>
        <br />
        <div id="intervention">
          <div id="indirect">התערבות עקיפה</div>
          <br />
          <div id="direct">התערבות ישירה</div>
        </div>
      </div>
    </div>
<br />
    <button @click="showExtraMsg = true">המשך</button>
    <div v-show="showExtraMsg" id="extra-msg">
      <h2 id="close-btn" @click="BackToHomePage">X</h2>
      <p id="information">
        !שימו לב
        <br />
        לרוב נתערב בתצפית כאשר
        <br />
        הנחנך חורג מהכללים*
        <br />
        הנחנך מטעה אחרים*
        <br />
        ישנה חריגה מהוראות הבטיחות*
      </p>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";
import VueScratchable from "./vue-scratchable.vue";
import paperPattern from "../assets/natural-paper-texture.jpg";

// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

import "swiper/css/scrollbar";

// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import { Navigation } from "swiper/modules";

export default {
  name: "step-three",
  components: {
    VueScratchable,
    Swiper,
    SwiperSlide,
  },

  data() {
    return {
      showExtraMsg: false,
      hide: {
        type: "pattern",
        src: paperPattern,
        repeat: "repeat",
      },
      brush: {
        size: 60,
        shape: "round",
      },
    };
  },

  methods: {
    BackToHomePage() {
      this.$emit("finish-stop-three");
    },
  },
  setup() {
    const onSwiper = (swiper) => {
      console.log(swiper);
    };
    const onSlideChange = () => {
      console.log("slide change");
    };
    return {
      onSwiper,
      onSlideChange,
      modules: [Navigation],
    };
  },
};
</script>

<style scoped>
* {
  max-width: 70vw;
}
#header {
  font-family: "assistant-bold";
}
#step-three {
  margin: 57px;
}

.swiper-button-prev, .swiper-rtl .swiper-button-next {
    left: var(--swiper-navigation-sides-offset, 10px);
    right: auto;
    width: 0%;
    color: #f5deb3;
}
:deep(.swiper-button-next:after, .swiper-rtl .swiper-button-prev:after) {
    content: 'next';
    color: wheat;
}
:deep(.swiper-button-prev:after, .swiper-button-next:after) {
    font-family: swiper-icons;
    font-size: var(--swiper-navigation-size);
    text-transform: none !important;
    letter-spacing: 0;
    font-variant: initial;
    line-height: 1;
    color: wheat !important;
}
/* .swiper-button-prev:after, .swiper-button-next:after {
    font-family: swiper-icons;
    font-size: var(--swiper-navigation-size);
    text-transform: none !important;
    letter-spacing: 0;
    font-variant: initial;
    line-height: 1;
    color: wheat;
} */
.vue-scratchable-wrapper > *[data-v-4c500325] {
  user-select: none;
  height: 35vh;
  width: 40vw;
}
#scratch-img {
  height: 35vh;
  width: 65vw;
}
#intervention {
  left: 50%;
  top: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
#indirect {
  display: flex;
  align-content: stretch;
  justify-content: center;
  align-content: center;
  flex-wrap: wrap;
  border: 1px solid;
  border-radius: 5px;
  width: 70%;
  height: 5%;
  font-size: 6vmin;
}
#direct {
  display: flex;
  align-content: center;
  align-content: stretch;
  justify-content: center;
  flex-wrap: wrap;
  border: 1px solid;
  border-radius: 5px;
  width: 70%;
  height: 5%;
  font-size: 6vmin;
}
#extra-msg {
  border: 3px solid white;
  border-radius: 5px;
  width: 80vw;
  height: 30vh;
  background-color: #e9c46a;
  z-index: 3;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

#close-btn {
  position: relative;
  top: 1vh;
    right: -27vw;
  z-index: 4;
}
button {
    border-radius: 8px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 1em;
    font-weight: 500;
    background-color: #1a1a1a;
    cursor: pointer;
    transition: border-color 0.25s;
    color: #e76f51;
    background-color: #e9c46a;
    border-radius: 0;
}
#information {
  position: relative;
  top: -3vh;
  font-size: 6vmin;
  text-align: center;
}
.card-slide {
  width: 69vw !important;
  height: 5vh;
  font-size: 6vmin;
  margin-right: 55px;
}
/* #header-3{
  font-family: 'assistant-bold';
} */
</style>
