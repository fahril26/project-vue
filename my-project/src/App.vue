<script>
import HeroSection from "./section/HeroSection.vue";
import ToTopButton from "./components/ToTopButton.vue";
import NavBar from "./components/NavBar.vue";
import AboutSection from "./section/AboutSection.vue";
import AboutSection2 from "./section/AboutSection2.vue";

export default {
  components: {
    HeroSection,
    ToTopButton,
    NavBar,
    AboutSection,
    AboutSection2,
  },

  data() {
    return {
      isScrolled: false,
      isScaledAbout: false,
    };
  },

  methods: {
    showCard() {
      const cards = document.querySelectorAll(".row-cards .ant-card");

      cards.forEach((card, index) => {
        setTimeout(() => {
          card.classList.add("show-card-active");
          card.classList.remove("hide-card");
        }, index * 300);
      });
    },

    windowOnScroll() {
      // Navbar and ButtonTop onscroll
      if (window.scrollY > 50) this.isScrolled = true;
      else if (window.scrollY < 50) this.isScrolled = false;

      // About section onscroll
      // scale header
      if (window.scrollY > 200) this.isScaledAbout = true;
      // show cards
      if (window.scrollY > 440) {
        this.showCard();
      }
  
    },
  },

  mounted() {
    // window onscroll
    window.addEventListener("scroll", this.windowOnScroll);
  },

  beforeUnmount() {
    // clear event onscroll
    window.removeEventListener("scroll", this.windowOnScroll);
  },
};
</script>

<template>
  <NavBar :is-scrolled="isScrolled" />
  <HeroSection />
  <AboutSection :is-scaled-about="isScaledAbout" />
  <AboutSection2 />
  <ToTopButton :is-scrolled="isScrolled" />
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style: none;
  text-decoration: none;
}

#app {
  height: 2000px;
  background-color: #efefef;
}

.show-card-active {
  animation: showCard 4s;
}

@keyframes showCard {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
</style>
