<template>
  <Transition>
    <div class="to-top" v-show="isScrolled">
      <button><up-circle-outlined /></button>
    </div>
  </Transition>
</template>
<script>
import { UpCircleOutlined } from "@ant-design/icons-vue";
export default {
  name: "TopUpButton",
  components: {
    UpCircleOutlined,
  },

  props: {
    isScrolled: {
      type: Boolean,
      default: false,
    },
  },
};
</script>
<style scoped>
.to-top {
  position: fixed;
  bottom: 5%;
  right: 40px;
  font-size: 2rem;
  transition: opacity 0.5s;
}

.to-top button {
  padding: 5px 15px;
  color: #fff;
  border: none;
  outline: none;
  border-radius: 50%;
  color: #fff;
  background: orange;
  cursor: pointer;
}

.to-top button:hover {
  background: #000;
  color: orange;
}

.v-leave-from,
.v-enter-to {
  opacity: 1;
}
.v-leave-to,
.v-enter-from {
  opacity: 0;
}
</style>
