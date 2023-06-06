<template>
  <div>
    <div class="about-rows">
      <div class="about-content">
        <h3>Learn to become a <span>Professional</span> Programmer</h3>
        <p>
          If you are going to use a passage of Lorem Ipsum, you need to be sure
          there isn't anything embarrassing hidden in the middle of text.
        </p>

        <div class="rows-benefit">
          <div class="benefit" v-for="(text, index) of benefits" :key="index">
            <p><check-outlined />{{ text }}</p>
          </div>
        </div>

        <Button size="large">About Us<right-outlined /></Button>
      </div>

      <div class="slide-image">
        <img :src="imageList[currentIndex]" alt="image" ref="img" />

        <div class="radio" @click="changeImageClick">
          <span class="radio-button" id="btn1" ref="btn1"></span>
          <span class="radio-button" id="btn2" ref="btn2"></span>
          <span class="radio-button" id="btn3" ref="btn3"></span>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { CheckOutlined, RightOutlined } from "@ant-design/icons-vue";
import { Button } from "ant-design-vue";
import image1 from "../assets/image/image1.jpg";
import image2 from "../assets/image/image2.jpg";
import image3 from "../assets/image/image3.jpg";

export default {
  components: {
    CheckOutlined,
    RightOutlined,
    Button,
  },
  data() {
    return {
      benefits: [
        "Best Practice",
        "Best Quality",
        "Safe and Security",
        "Nice Environtment",
      ],
      imageList: [image1, image2, image3],
      currentIndex: 1,
      intervalId: null,
    };
  },

  methods: {
    changeImageClick(e) {
      const radio = document.querySelectorAll(".radio-button");
      for (const index of radio) {
        if (index.classList.contains("radio-active"))
          index.classList.remove("radio-active");
      }

      if (e.target.classList.contains("radio-button")) {
        if (e.target.id == "btn1") this.currentIndex = 0;
        else if (e.target.id == "btn2") this.currentIndex = 1;
        else if (e.target.id == "btn3") this.currentIndex = 2;

        e.target.classList.add("radio-active");
        this.$refs.img.classList.add("animation-slide");

        setTimeout(() => {
          this.$refs.img.classList.remove("animation-slide");
        }, 200);
      }

      clearInterval(this.intervalId);
      this.startSlide();
    },

    startSlide() {
      const radio = document.querySelectorAll(".radio-button");
      radio[this.currentIndex].classList.add("radio-active");

      this.intervalId = setInterval(() => {
        radio[this.currentIndex].classList.remove("radio-active");

        this.currentIndex = (this.currentIndex + 1) % this.imageList.length;

        this.$refs.img.classList.add("animation-slide");

        radio[this.currentIndex].classList.add("radio-active");

        setTimeout(() => {
          this.$refs.img.classList.remove("animation-slide");
        }, 400);
      }, 6000);
    },
  },

  mounted() {
    this.startSlide();
  },
};
</script>
<style>
.about-rows {
  background: #fff;
  padding: 5.5rem;
  display: flex;
  overflow: hidden;
}

.about-content {
  flex: 1;
  padding: 0 20px;
}

.about-content h3 {
  font-size: 2rem;
  color: #555;
  text-shadow: 2px 2px 2px rgba(0, 0, 0, 0.2);
}

.about-content h3 span {
  color: orange;
}

.about-content p {
  font-size: 1rem;
  color: #777;
  margin-bottom: 0;
}

.rows-benefit {
  display: flex;
  flex-wrap: wrap;
  padding: 40px 0;
  gap: 25px;
}

.benefit {
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
  padding: 10px;
  width: 250px;
  border-radius: 8px;
  border-left: 3px solid orange;
}

.benefit p {
  font-size: 1.2rem;
  font-weight: bold;
  color: #555;
}

.benefit svg {
  margin: 0 10px;
}

.about-content .ant-btn {
  background: orange !important;
  color: #fff;
  font-weight: 5000;
  border-radius: 5px;
  border: 2px solid orange !important;
}

.about-content .ant-btn:hover {
  background: inherit !important;
  color: rgb(0, 0, 199);
}

.about-content .ant-btn-lg {
  height: 50px;
  width: 120px;
}

.ant-btn .anticon,
.about-content .ant-btn:not(:hover) .anticon {
  transform: translateX(-20px);
  opacity: 0;
  transition: 0.4s all;
}

.about-content .ant-btn:hover .anticon {
  transform: translateX(0);
  transition: 0.4s all;
  opacity: 1;
}

.slide-image {
  flex: 1;
}

.animation-slide {
  animation: imgSlide 3s;
}

.about-rows .slide-image img {
  width: 100%;
}

.slide-image .radio {
  display: flex;
  gap: 10px;
  margin: 20px auto 0;
  transform: translateX(45%);
}

.radio-button {
  border: 1px solid blue;
  height: 8px;
  width: 8px;
  border-radius: 50%;
  cursor: pointer;
}

.radio-active {
  border-radius: 5px;
  height: 8px;
  background: orange;
  display: inline-block;
  border: none;
  animation: wide 0.3s forwards;
}

@keyframes wide {
  from {
    width: 0;
  }

  to {
    width: 30px;
  }
}

@keyframes imgSlide {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
</style>
