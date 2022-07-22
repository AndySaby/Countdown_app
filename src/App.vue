<template>
  <div class="main">
    <div><img src="@/assets/bg-stars.svg" alt="" class="stars" /></div>
    <div class="bodyContainer">
      <Timer />
    </div>

    <div class="base">
      <div><img src="@/assets/pattern-hills.svg" alt="" class="footerImage" /></div>
      <div class="footer">
        <div class="tabs">
          <img
            :src="tab.image"
            alt=""
            class="icon"
            v-for="tab in footerTabs"
            :key="tab.id"
            :class="{ active: tab === activeTab }"
            @click="() => (activeTab = tab)"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Timer from "@/components/AppTimer.vue";

export default {
  name: "App",
  components: { Timer },
  data() {
    return {
      activeTab: "",
      footerTabs: [
        { id: "1", image: require("@/assets/facebook.svg") },
        { id: "2", image: require("@/assets/Path.svg") },
        { id: "3", image: require("../src/assets/Shape.svg") },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: "Red Hat Display";
}
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background: #1d1e28;
}
.stars {
  position: absolute;
  top: 0;
  max-width: 100%;
}
.footer {
  display: flex;
  justify-content: center;
}
.tabs {
  position: absolute;
  bottom: 100px;
}
.icon {
  margin-right: 32px;
}
.icon.active {
  background: #fb5e84;
}
.main {
  background: #1d1e28;
}
.bodyContainer {
  background: #1d1e28;
  height: fit-content;
  padding-bottom: 252px;
}
.footerImage {
  position: absolute;
  bottom: 0;
  width: 100%;
}
@media only screen and (max-width: 700px) {
  .footerImage {
    height: 168px;
    top: 80%;
    z-index: -1;
  }
  .bodyContainer {
    padding-bottom: 100px;
  }
  .tabs {
    position: absolute;
    bottom: 48px;
  }
}
</style>
