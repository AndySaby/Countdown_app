<template>
  <div>
    <p class="header">We’re launching soon</p>

    <div class="timeWrapper">
      <!-- days wrap -->
      <div class="card">
        <div class="top">
          <div class="upper"></div>
        </div>

        <div class="lower">
          <div class="value">
            <span class="timeIndicator">{{ days }}</span>
          </div>
        </div>
        <p class="timeElement">DAYS</p>
      </div>

      <!-- hours -->
      <div class="card">
        <div class="top">
          <div class="upper"></div>
        </div>

        <div class="lower">
          <div class="value">
            <span class="timeIndicator">{{ hours }}</span>
          </div>
        </div>
        <p class="timeElement">HOURS</p>
      </div>

      <!-- minutes -->
      <div class="card">
        <div class="top">
          <div class="upper"></div>
        </div>

        <div class="lower">
          <div class="value">
            <span class="timeIndicator">{{ minutes }}</span>
          </div>
        </div>
        <p class="timeElement">MINUTES</p>
      </div>

      <!-- seconds -->
      <div class="card">
        <div class="top">
          <div class="upper"></div>
        </div>

        <div class="lower">
          <div class="value">
            <span class="timeIndicator">{{ seconds }}</span>
          </div>
        </div>
        <p class="timeElement">SECONDS</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Timer",
  data() {
    return {
      days: "",
      minutes: "",
      hours: "",
      seconds: "",
    };
  },
  mounted() {
    this.countdown();
  },
  methods: {
    // formatNum(num) {
    //   num < 10 ? "0" + num : num;
    // },
    countdown() {
      const timer = setInterval(() => {
        let lanuchDate = new Date("July 30, 2022 00: 00 : 00 ").getTime();
        let now = new Date().getTime();
        const difference = lanuchDate - now;

        let seconds = 1000;
        let minutes = seconds * 60;
        let hours = minutes * 60;
        let days = hours * 24;

        let daysLeft = Math.floor(difference / days);
        let hoursLeft = Math.floor((difference % days) / hours);
        let minutesLeft = Math.floor((difference % hours) / minutes);
        let secondsLeft = Math.floor((difference % minutes) / seconds);

        this.days = daysLeft < 10 ? "0" + daysLeft : daysLeft;
        this.hours = hoursLeft < 10 ? "0" + hoursLeft : hoursLeft;
        this.minutes = minutesLeft < 10 ? "0" + minutesLeft : minutesLeft;
        this.seconds = secondsLeft < 10 ? "0" + secondsLeft : secondsLeft;
      }, 1000);
      console.log(timer);
      return timer;
    },
  },
};
</script>

<style scoped>
.header {
  font-family: "Red Hat Text";
  font-style: normal;
  font-weight: 700;
  font-size: 22px;
  line-height: 29px;
  text-align: center;
  letter-spacing: 7.5px;
  text-transform: uppercase;
  color: #ffffff;
  margin: 132px 0 104px 0;
}
.timeWrapper {
  display: flex;
  justify-content: center;
  gap: 0 32px;
  flex-wrap: wrap;
}
.top {
  background: #343650;
  border-radius: 8px;
}
.upper {
  background: #000000;
  mix-blend-mode: normal;
  opacity: 0.15;
  border-radius: 0px 0px 8px 8px;
  transform: matrix(1, 0, 0, -1, 0, 0);
  width: 148px;
  height: 70px;
}
.lower {
  background: #343650;
  border-radius: 8px;
  width: 148px;
  height: 70px;
  position: relative;
}
.timeIndicator {
  font-style: normal;
  font-weight: 700;
  font-size: 80px;
  line-height: 71px;
  text-align: center;
  letter-spacing: -2.4px;
  color: #fb5e84;
  text-align: center;
  position: absolute;
  top: -50%;
  left: 20%;
}
.timeElement {
  font-style: normal;
  font-weight: 700;
  font-size: 14px;
  line-height: 19px;
  text-align: center;
  letter-spacing: 5.91875px;
  color: #8385a9;
  margin-top: 16px;
}
@media only screen and (max-width: 700px) {
  .header {
    margin: 50px 0;
  }
}
</style>
