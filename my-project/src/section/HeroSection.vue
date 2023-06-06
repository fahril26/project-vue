<template>
  <section id="home">
    <div class="hero-container">
      <div class="hero-row">
        <div class="hero-content">
          <h5 class="text-white text-capitalize mb-4">
            We will teach you How to Learn
          </h5>
          <h1>BEST BOOTCAMP & ANYTHING TO <span>LEARN</span> SMART WAY</h1>
          <p>Learning & Course etc.</p>

          <div class="hero-btn">
            <a-button size="large">Default Button<right-outlined /></a-button>
            <a-button size="large">Default Button<right-outlined /></a-button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import Navbar from "../components/NavBar.vue";
import { Button } from "ant-design-vue";
import { RightOutlined } from "@ant-design/icons-vue";

export default {
  name: "HeroSection",
  components: {
    "nav-bar": Navbar,
    Button,
    RightOutlined,
  },

  mounted() {},
};
</script>

<style>
.hero-container {
  background-image: url(../assets/hero.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  height: 100vh;
}

.hero-row {
  display: flex;
  align-items: center;
  height: 100%;
}

.hero-content {
  color: #fff;
  padding: 0 100px;
  width: 60%;
}

.hero-content img {
  width: 40px;
}

.hero-content h5 {
  color: inherit;
  font-size: 1.5rem;
  text-shadow: 3px 3px 5px rgba(0, 0, 0, 0.5);
}

.hero-content h1 {
  color: inherit;
  font-size: 2.3rem;
  margin-top: 20px;
  text-shadow: 3px 3px 5px rgba(0, 0, 0, 0.5);
  animation: slide1 1s;
  transition: 1s;
}

.hero-content p {
  font-size: 1rem;
  margin: 20px 0;
  color: inherit;
  text-shadow: 3px 3px 5px rgba(0, 0, 0, 0.5);
}

.hero-content h1 span {
  color: orange;
}

.hero-content .hero-btn {
  display: flex;
  gap: 20px;
}

.hero-btn .ant-btn {
  font-weight: 500;
  transition: 0.7s all;
  border-radius: 5px;
}

.hero-btn .ant-btn-lg {
  height: 50px;
  padding: 6.4px 8px 6.4px 25px;
}

.hero-btn .ant-btn:nth-child(1) {
  color: rgb(2, 2, 173);
}

.hero-btn .ant-btn:nth-child(2) {
  background: inherit;
  color: #fff;
}

.hero-btn .ant-btn:nth-child(1):hover {
  background: inherit !important;
  border-color: #fff;
  color: #fff;
}

.hero-btn .ant-btn:nth-child(2):hover {
  border-color: #fff;
}

.hero-btn .anticon {
  transform: translateX(-25px);
  opacity: 0;
}

.hero-btn .ant-btn:nth-child(1):hover .anticon,
.hero-btn .ant-btn:nth-child(2):hover .anticon {
  transform: translateX(0);
  transition: 0.4s all;
  opacity: 1;
}

.hero-btn .ant-btn:nth-child(1):not(:hover) .anticon,
.hero-btn .ant-btn:nth-child(2):not(:hover) .anticon {
  transform: translateX(-25px);

  transition: 0.4s all;
}

@keyframes slide1 {
  from {
    transform: translateX(-10%);
    opacity: 0;
  }

  to {
    transform: translateX(0);
    opacity: 1;
  }
}
</style>
