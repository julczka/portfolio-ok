<template>
  <div id="bcg-wrapper">
    <svg
      id="b183346d-cd5a-41cf-b9ba-e6138f97b72a"
      data-name="Layer 1"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      width="1920"
      height="1080"
      viewBox="0 0 1920 1080"
    >
      <defs>
        <linearGradient
          id="bd943ecc-f758-4848-867d-32a1e6021a31"
          x1="959.5"
          y1="122.41"
          x2="959.5"
          y2="1298.46"
          gradientUnits="userSpaceOnUse"
        >
          <stop offset="0" stop-color="#d9d7d8" />
          <stop offset="1" stop-color="#595859" />
        </linearGradient>
        <linearGradient
          id="a76479e8-94e3-41fe-b879-8f8db571de14"
          x1="1803.24"
          y1="972.42"
          x2="564.23"
          y2="-266.59"
          gradientUnits="userSpaceOnUse"
        >
          <stop offset="0.09" stop-color="#d9d7d8" />
          <stop offset="1" stop-color="#595859" />
        </linearGradient>
        <linearGradient
          id="b4a10aea-9592-4906-9979-e7c5e7d99ba8"
          x1="972.5"
          y1="677.6"
          x2="972.5"
          y2="-1571.5"
          gradientUnits="userSpaceOnUse"
        >
          <stop offset="0" stop-color="#d9d7d8" />
          <stop offset="0.91" stop-color="#595859" />
        </linearGradient>
        <linearGradient
          id="b762dba1-8438-4a2d-94de-925cc917c992"
          x1="334.5"
          y1="1000.42"
          x2="334.5"
          y2="-135.58"
          gradientUnits="userSpaceOnUse"
        >
          <stop offset="0.08" stop-color="#d9d7d8" />
          <stop offset="1" stop-color="#595859" />
        </linearGradient>
      </defs>
      <g>
        <path
          d="M1,1V285.69c144.55,26.94,322.38,47.83,521.24,60.4,137.41,8.69,284.83,13.41,438.26,13.41,162,0,317.31-5.26,461.19-14.9C1610.39,332,1779.4,311.79,1918,286.06V1Z"
          transform="translate(-1 -1)"
          fill="url(#bd943ecc-f758-4848-867d-32a1e6021a31)"
        />
        <path
          d="M1773.75,584.42c-72.21-72.21-177.16-91.73-267.08-58.59a252.51,252.51,0,0,0-91.42,58.59c-99,99-99,259.51,0,358.51a256.55,256.55,0,0,0,22.41,19.91c99.49,78.55,244.25,71.92,336.09-19.91C1872.75,843.93,1872.75,683.42,1773.75,584.42Z"
          transform="translate(-1 -1)"
          fill="url(#a76479e8-94e3-41fe-b879-8f8db571de14)"
        />
        <path
          d="M1506.67,525.83a549.68,549.68,0,0,0-85-181.23c-100.14-139.91-264-231.1-449.19-231.1-185.84,0-350.22,91.83-450.26,232.59A549.49,549.49,0,0,0,420.5,665.5q0,9,.3,17.92c83.13,34,141.7,115.7,141.7,211.08a227.07,227.07,0,0,1-27.18,108A554.92,554.92,0,0,0,605.69,1078h733.62a552.88,552.88,0,0,0,167.36-552.17Z"
          transform="translate(-1 -1)"
          fill="url(#b4a10aea-9592-4906-9979-e7c5e7d99ba8)"
        />
        <path
          d="M420.8,683.42a227.24,227.24,0,0,0-86.3-16.92c-125.92,0-228,102.08-228,228A227.66,227.66,0,0,0,199.17,1078H469.83A227.71,227.71,0,0,0,562.5,894.5C562.5,799.12,503.93,717.44,420.8,683.42Z"
          transform="translate(-1 -1)"
          fill="url(#b762dba1-8438-4a2d-94de-925cc917c992)"
        />
      </g>
    </svg>
  </div>
</template>

<script>
export default {
  name: "bckgr",
};
</script>

<style scoped lang="scss">
// #bcg-wrapper {
//   width: 100%;
//   position: fixed;
//   z-index: 0;
// }

#b183346d-cd5a-41cf-b9ba-e6138f97b72a {
  position: absolute;
  bottom: 0;
  right: 0;
  top: 100;
  z-index: 0;
  width: 100%;
}
</style>
