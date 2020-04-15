<template>
  <div class="swiper-container">
    <div class="swiper-control">
      <i class="fas fa-chevron-left prev-slide"></i>

      <i class="fas fa-chevron-right next-slide"></i>
    </div>
    <div class="swiper-wrapper timeline">
      <div class="swiper-slide" v-for="(item, index) in steps" :key="index">
        <div class="timestamp">
          <span class="date">{{ item.dateLabel }}</span>
        </div>
        <div class="status">
          <span>{{ item.title }}</span>
        </div>
      </div>
    </div>
    <!-- Add Pagination -->
    <div class="swiper-pagination"></div>
  </div>
</template>

<script>
import Swiper from "swiper";
const data = [
  { dateLabel: "January 2017", title: "Gathering Information" },
  { dateLabel: "February 2017", title: "Planning" },
  { dateLabel: "March 2017", title: "Design" },
  { dateLabel: "April 2017", title: "Content Writing and Assembly" },
  { dateLabel: "May 2017", title: "Coding" },
  { dateLabel: "June 2017", title: "Testing, Review & Launch" },
  { dateLabel: "July 2017", title: "Maintenance" }
];
export default {
  name: "timeline",
  data() {
    return {
      steps: data
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
        renderBullet: function(index, className) {
          return '<span class="' + className + '">' + (index + 1) + "</span>";
        }
      },
      navigation: {
        nextEl: ".next-slide",
        prevEl: ".prev-slide"
      }
    });
  }
};
</script>

<style lang="scss" scoped>
.swiper-pagination-bullet {
  width: 20px;
  height: 20px;
  text-align: center;
  line-height: 20px;
  font-size: 12px;
  color: #000;
  opacity: 1;
  background: rgba(0, 0, 0, 0.2);
}
.swiper-pagination-bullet-active {
  color: #fff;
  background: #007aff;
}

.timeline {
  margin: 50px 0;
  list-style-type: none;
  display: flex;
  padding: 0;
  text-align: center;
  color: var(--text-primary);
}
.timeline li {
  transition: all 200ms ease-in;
}
.timestamp {
  width: 200px;
  margin-bottom: 20px;
  padding: 0px 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-weight: 100;
}
.status {
  padding: 0px 40px;
  display: flex;
  justify-content: center;
  border-top: 0.2rem solid var(--text-primary);
  position: relative;
  transition: all 200ms ease-in;
}

.status span {
  font-weight: 600;
  padding-top: 20px;
}
.status span:before {
  content: "";
  width: 25px;
  height: 25px;
  background-color: var(--bg-primary);
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
}

.swiper-container {
  width: 80%;
  height: 250px;

  overflow: hidden;
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
