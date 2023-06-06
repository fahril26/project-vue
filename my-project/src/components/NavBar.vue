<template>
  <nav :class="{ 'nav-onscroll': isScrolled }">
    <img src="../assets/favicon.png" alt="logo" />

    <ul>
      <li v-for="(list, index) of listNav" :key="index">
        <a :href="list.url" :class="{ 'color-change': isScrolled }">{{
          list.name
        }}</a>
      </li>

      <div @click="changeIcon = !changeIcon" class="icon">
        <search-outlined style="font-size: 1.7rem" v-if="changeIcon" />
        <close-outlined style="font-size: 1.7rem" v-else />
      </div>
      <button>Admission Now</button>
    </ul>
    <Transition>
      <div class="drop-down" v-show="!changeIcon">
        <div class="wrapper-input">
          <input type="text" placeholder="Search Here..." />
          <button><search-outlined /></button>
        </div>
      </div>
    </Transition>
  </nav>
</template>

<script lang="ts">
import { SearchOutlined, CloseOutlined } from "@ant-design/icons-vue";

export default {
  components: {
    SearchOutlined,
    CloseOutlined,
  },

  props: {
    isScrolled: {
      type: Boolean,
      default: false,
    },
  },

  data() {
    return {
      listNav: [
        { name: "Home", url: "#home" },
        { name: "About", url: "#about" },
        { name: "Course", url: "#course" },
        { name: "Gallery", url: "#gallery" },
        { name: "Teacher", url: "#teacher" },
        { name: "Blog", url: "#blog" },
        { name: "Contact", url: "#contact" },
      ],
      changeIcon: true,
      inpVisible: false,
    };
  },
};
</script>

<style scoped>
nav {
  display: flex;
  padding: 0 5rem;
  align-items: center;
  justify-content: space-between;
  position: fixed;
  left: 0;
  right: 0;
  transition: 0.5s all;
  z-index: 99;
}

.nav-onscroll {
  background: #fff;
  animation: navScroll 1s;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
}

nav ul {
  width: 60%;
  padding: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0 !important;
}

nav ul > div,
nav button {
  cursor: pointer;
}

nav ul a {
  color: #fff;
}

nav ul a:hover {
  color: orange;
}

.color-change {
  color: #000;
}

nav .icon {
  padding: 10px;
  background: rgb(255, 179, 37);
  border-radius: 50%;
  color: #fff;
}

nav .icon:hover {
  background: orange;
}

nav ul button {
  background: rgb(255, 179, 37);
  border-radius: 5px;
  color: #fff;
  border: none;
  outline: none;
  padding: 10px 20px;
}

nav button:hover {
  background: orange;
}

.drop-down {
  position: absolute;
  right: 20%;
  top: 100.5%;
  padding: 20px;
  background: #fff;
  width: 240px;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
}

.drop-down input {
  outline: none;
  border: 1px solid orange;
  padding: 5px;
}

.drop-down button {
  background: rgb(255, 179, 36);
  outline: none;
  border: none;
  padding: 6px;
  color: #fff;
  cursor: pointer;
}
.drop-down button:hover {
  background: orange;
}

.v-enter-active {
  animation: added 0.3s;
}
.v-leave-active {
  animation: added 0.3s reverse;
}

@keyframes added {
  from {
    opacity: 0;
    transform: translateX(100%);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes navScroll {
  from {
    opacity: 0;
    transform: translateY(-100%);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
