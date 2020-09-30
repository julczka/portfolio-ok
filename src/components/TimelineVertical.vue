<template>
  <div class="swiper-container">
    <div class="swiper-control">
      <button class="swiper-button">
        <i class="fas fa-arrow-up prev-slide"></i>
      </button>

      <button class="swiper-button">
        <i class="fas fa-arrow-down next-slide"></i>
      </button>
    </div>
    <div class="swiper-wrapper timeline">
      <div class="swiper-slide" v-for="(item, index) in steps" :key="index">
        <div class="timestamp">
          <span class="date">{{ item.dateLabel }}</span>
        </div>
        <div class="status">
          <h5 v-html="item.title">{{ item.title }}</h5>
          <p v-html="item.description">
            {{ item.description }}
          </p>
        </div>
      </div>
    </div>
    <!-- Add Pagination -->
    <!-- <div class="swiper-pagination"></div> -->
  </div>
</template>

<script>
import Swiper from "swiper";
import resume from "../data/resume.json";
export default {
  name: "timeline-vertical",
  data() {
    return {
      steps: resume
    };
  },

  mounted() {
    new Swiper(".swiper-container", {
      //pagination: '.swiper-pagination',
      slidesPerView: 1,
      // freeMode: true,
      grabCursor: true,
      direction: "vertical",
      // pagination: {
      //   el: ".swiper-pagination",
      //   clickable: true,
      //   renderBullet: function(index, className) {
      //     return '<span class="' + className + '">' + (index + 1) + "</span>";
      //   }
      // },
      navigation: {
        nextEl: ".next-slide",
        prevEl: ".prev-slide"
      }
    });
  }
};
</script>

<style lang="scss" scoped>
@import url("../styles/_swiper.scss");

.swiper-button {
  background-color: var(--bg-primary);
  font-size: 2rem;
  padding: 0.8em;
  border: 1px solig var(--bg-secondary);
  border-radius: 50px;
}

// .timeline {
//   margin: 50px 0;
//   list-style-type: none;
//   display: flex;
//   padding: 0;
//   text-align: center;
// }

.timestamp {
  // width: 200px;
  // margin-bottom: 2em;
  padding: 0 2em;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  font-weight: 100;
  color: var(--text-secondary);
  font-family: futura-pt, sans-serif;
}
.status {
  padding: 0 0.5em 0 3.5em;
  display: flex;
  flex-direction: column;
  justify-content: center;
  border-left: 0.2rem solid var(--text-secondary);
  position: relative;
  transition: all 200ms ease-in;
  text-align: left;
  font-family: futura-pt, sans-serif;
  font-weight: 400;
  height: 100%;
  width: 70%;
}

.status h5 {
  // padding-top: 1.2em;
  font-weight: 600;
  color: var(--text-primary);
}

.status p {
  color: var(--text-secondary);
  text-align: justify;
  text-justify: inter-word;
}
.status h5:before {
  content: "";
  width: 2rem;
  height: 2rem;
  background-color: var(--bg-secondary);
  border-radius: 25px;
  border: 0.2rem solid var(--text-primary);
  position: absolute;
  top: 47.9%;
  left: -0.9em;
  transition: all 200ms ease-in;
}
.swiper-control {
  text-align: left;
  font-size: 3rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin: 0.5em 0;
  height: 90%;
  position: absolute;
  z-index: 10;

  i {
    color: var(--text-secondary);
  }
}

.swiper-container {
  width: 80%;
  height: 70vh;
}
.swiper-slide {
  text-align: center;
  font-size: 1.5rem;
  // height: 50%;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}
.swiper-slide:nth-child(2n) {
  height: 40%;
}
.swiper-slide:nth-child(3n) {
  height: 20%;
}
</style>
