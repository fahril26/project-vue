<template>
  <nav>
    <img src="../assets/favicon.png" alt="logo" />

    <ul>
      <li v-for="(list, index) of data.listNav" :key="index">
        <a href="#">{{ list }}</a>
      </li>

      <div @click="data.changeIcon = !data.changeIcon">
        <search-outlined style="font-size: 1.7rem" v-if="data.changeIcon" />
        <close-outlined style="font-size: 1.7rem" v-else />
      </div>
      <button>Button</button>
    </ul>
  </nav>
</template>

<script lang="ts" setup>
import { reactive } from "vue";
import { SearchOutlined, CloseOutlined } from "@ant-design/icons-vue";
const data = reactive({
  listNav: ["Home", "about", "Course", "Gallery", "Teacher", "Blog", "Contact"],
  changeIcon: true,
});
</script>

<style scoped>
nav {
  display: flex;
  padding: 0 5rem;
  align-items: center;
  justify-content: space-between;
}

nav ul {
  width: 60%;
  padding: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

nav ul > div,
nav button {
  cursor: pointer;
}
</style>
