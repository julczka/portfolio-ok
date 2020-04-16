<template>
  <div class="swiper-container">
    <div class="swiper-control">
      <i class="fas fa-arrow-left prev-slide"></i>

      <i class="fas fa-arrow-right next-slide"></i>
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
    <div class="swiper-pagination"></div>
  </div>
</template>

<script>
import Swiper from "swiper";
import resume from "../data/resume.json";
export default {
  name: "timeline",
  data() {
    return {
      steps: resume,
    };
  },

  mounted() {
    new Swiper(".swiper-container", {
      //pagination: '.swiper-pagination',
      slidesPerView: 2,
      freeMode: true,
      grabCursor: true,
      pagination: {
        el: ".swiper-pagination",
        clickable: true,
      },
      navigation: {
        nextEl: ".next-slide",
        prevEl: ".prev-slide",
      },
    });
  },
};
</script>

<style lang="scss" scoped>
@import url("../styles/_swiper.scss");

.swiper-pagination-bullet {
  width: 10px;
  height: 10px;
  text-align: center;
  line-height: 60px;
  font-size: 0.8rem;
  font-family: futura-pt, sans-serif;
  font-weight: 200;
  color: var(--text-primary);
  opacity: 1;
  background: var(--bg-secondary);
}
.swiper-pagination-bullet-active {
  color: var(--text-primary);
  background: var(--text-primary);
  border: 1px solid var(--text-primary);
}

.swiper-container-horizontal
  > .swiper-pagination-bullets
  .swiper-pagination-bullet {
  margin: 0 0.4em;
}

.swiper-pagination {
  position: relative;
  margin-top: 2rem;
}

.timeline {
  margin: 50px 0;
  list-style-type: none;
  display: flex;
  padding: 0;
  text-align: center;
}
.timeline li {
  transition: all 200ms ease-in;
}
.timestamp {
  // width: 200px;
  margin-bottom: 2em;
  padding: 0 6em;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  font-weight: 100;
  color: var(--text-secondary);
}
.status {
  padding: 0 4em;
  display: flex;
  flex-direction: column;
  justify-content: center;
  border-top: 0.2rem solid var(--text-secondary);
  position: relative;
  transition: all 200ms ease-in;
  text-align: left;
  font-family: futura-pt, sans-serif;
  font-weight: 400;
}

.status h5 {
  padding-top: 1.2em;
  font-weight: 600;
  color: var(--text-primary);
}

.status p {
  color: var(--text-secondary);
}

.timeline-link {
  color: var(--text-primary);
  text-decoration: underline;
  font-size: 2rem;
}
.status h5:before {
  content: "";
  width: 25px;
  height: 25px;
  background-color: var(--bg-secondary);
  border-radius: 25px;
  border: 0.2rem solid var(--text-primary);
  position: absolute;
  top: -15px;
  left: 42%;
  transition: all 200ms ease-in;
}
.swiper-control {
  text-align: right;
  font-size: 3rem;
  display: flex;
  justify-content: space-between;
  margin: 0.5em 0;

  i {
    color: var(--text-secondary);
  }

  .disabled {
    opacity: 0.3;
  }
}

.swiper-container {
  width: 80%;
}
.swiper-slide {
  width: 3rem;
  text-align: center;
  font-size: 1rem;
}
.swiper-slide:nth-child(2n) {
  width: 40%;
}
.swiper-slide:nth-child(3n) {
  width: 20%;
}
</style>
