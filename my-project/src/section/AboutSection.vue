<template>
  <section id="about">
    <div class="about-container">
      <header>
        <div :class="addedClass">
          <h3>Welcome To <span>Bootcamp</span></h3>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit.
            Perspiciatis corporis provident labore, voluptate id quibusdam
            suscipit quo ratione ut a.
          </p>
        </div>
      </header>
    </div>

    <div class="row-cards">
      <card-component v-for="(card, index) in dataCards" :key="index">
        <a-card hoverable style="width: 240px" :key="index" class="hide-card">
          <img :src="card.img" alt="Deskripsi Gambar" />

          <a-card-meta :title="card.title">
            <template #description>
              Lorem ipsum dolor sit amet elit consectetur adipiscing sed eiusmod
              tempor.
            </template>
          </a-card-meta>
          <button>Read More</button>
        </a-card>
      </card-component>
    </div>
  </section>
</template>
<script>
import CardComponent from "../components/CardComponent.vue";
import Teacher from "../assets/cards-icon/001-teacher.png";
import Certificate from "../assets/cards-icon/certificate.png";
import Computer from "../assets/cards-icon/computer.png";
import CustomerService from "../assets/cards-icon/customer-support.png";

export default {
  name: "AboutSection",
  components: {
    "card-component": CardComponent,
  },
  props: {
    isScaledAbout: {
      type: Boolean,
    },
  },

  computed: {
    addedClass() {
      if (this.isScaledAbout) return "about-scale-active";
      else return "about-before-scale";
    },
  },

  data() {
    return {
      dataCards: [
        {
          img: Teacher,
          title: "Best Teacher",
          isShowCard: false,
        },
        { img: Certificate, title: "Certificate", isShowCard: false },
        { img: Computer, title: "Good Program", isShow: false },
        {
          img: CustomerService,
          title: "Customer Service",
          isShow: false,
        },
      ],
    };
  },

  mounted() {},
};
</script>
<style>
#about {
  padding: 100px 0;
}

.about-before-scale {
  transform: scale(0);
}

.about-scale-active {
  animation: scale 1.5s;
}

.about-container header {
  text-align: center;
  margin-bottom: 100px;
}

.about-container header h3 {
  font-size: 2rem;
}

.about-container header h3 span {
  color: orange;
}

.about-container header p {
  width: 40%;
  margin: auto;
  font-size: 1rem;
  color: #666;
}

.row-cards {
  display: flex;
  justify-content: center;
  gap: 20px;
}

.row-cards .ant-card {
  padding: 20px 0;
  width: 280px !important;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.hide-card {
  opacity: 0;
}

.show-card-active {
  animation: showCard 0.2s;
}

.row-cards .ant-card-meta-title {
  font-size: 1.5rem;
  margin: 20px 0;
  font-weight: bold;
  color: #333;
}

.row-cards .ant-card-meta-description {
  font-size: 1.1rem;
  color: rgba(0, 0, 0, 0.7);
  margin-bottom: 40px;
}

.row-cards .ant-card img {
  width: 80px;
}

.row-cards .ant-card button {
  background: none;
  border: none;
  outline: none;
  color: rgb(0, 0, 255);
  cursor: pointer;
  font-size: 1rem;
}

.row-cards .ant-card button:hover {
  color: orange;
}

.row-cards .ant-card button::after {
  content: "";
  display: block;
  background: orange;
  width: 30%;
  height: 2px;
  border-radius: 2px;
  margin-top: 5px;
  transition: 0.4s;
}

.row-cards .ant-card button:hover::after {
  width: 100%;
}

@keyframes showCard {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}

@keyframes scale {
  0% {
    scale: 0;
    opacity: 0;
  }

  100% {
    scale: 1;
    opacity: 1;
  }
}
</style>
