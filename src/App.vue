<template>
  <header>
    <Navbar />
  </header>
  <section class="project container-lg">
    <ProjectCard class="mb-4" />
    <ProgressCard
      :dollarsBacked="dollarsBacked"
      :numBackers="numBackers"
      class="mb-4"
    />
    <AboutCard
      :rewards="rewards"
      class="mb-5"
      @select-reward="(rewardId) => (selectedReward = rewardId)"
    />
  </section>

  <PledgeModal :rewards="rewards" :selectedReward="selectedReward ? selectedReward + 1 : null" @pledge="addPledge" />
  <ThanksModal />
</template>

<script>
import Navbar from "./components/Navbar.vue";
import ProjectCard from "./components/ProjectCard.vue";
import ProgressCard from "./components/ProgressCard.vue";
import AboutCard from "./components/AboutCard.vue";
import PledgeModal from "./components/PledgeModal.vue";
import ThanksModal from "./components/ThanksModal.vue";

export default {
  name: "App",
  components: {
    Navbar,
    ProjectCard,
    ProgressCard,
    AboutCard,
    PledgeModal,
    ThanksModal,
  },
  data() {
    return {
      rewards: [
        {
          name: "Bamboo Stand",
          minPledge: 25,
          description:
            "You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campaign, and you’ll be added to a special Backer member list.",
          stock: 101,
        },
        {
          name: "Black Edition Stand",
          minPledge: 75,
          description:
            "You get a Black Special Edition computer stand and a personal thank you. You’ll be added to our Backer member list. Shipping is included.",
          stock: 64,
        },
        {
          name: "Mahogany Special Edition Pledge",
          minPledge: 200,
          description:
            "You get two Special Edition Mahogany stands, a Backer T-Shirt, and a personal thank you. You’ll be added to our Backer member list. Shipping is included.",
          stock: 0,
        },
      ],
      selectedReward: null,
      dollarsBacked: 89914,
      numBackers: 5007,
    };
  },
  methods: {
    addPledge(rewardId, ammount) {
      if (rewardId != 0) {
        this.rewards[rewardId - 1].stock--;
      }
      this.dollarsBacked += ammount;
      this.numBackers++;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Commissioner:wght@400;500;700&display=swap");
body {
  font-family: "Commissioner", sans-serif;
  font-size: 16px;
  background-color: hsl(0, 0%, 90%);
}

header {
  background-image: url("./assets/images/image-hero-mobile.jpg");
  background-size: cover;
  height: 60vh;
}

.pledge-text {
  color: hsl(176, 50%, 47%);
}

section.project {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translateX(-50%);
}

.card {
  border-radius: 10px;
}
.card.inactive:after {
  content: " ";
  z-index: 10;
  display: block;
  position: absolute;
  height: 100%;
  top: 0;
  left: 0;
  right: 0;
  background: rgba(228, 228, 228, 0.2);
  border-radius: 10px;
}

.btn.btn-primary {
  background-color: hsl(176, 50%, 47%);
  border-color: hsl(176, 50%, 47%);
  font-weight: 500;
}
.btn.btn-primary:active,
.btn.btn-primary:hover {
  background-color: hsl(176, 72%, 28%);
}
.btn.btn-light {
  color: hsl(0, 0%, 48%);
  font-weight: 700;
}

.attribution {
  font-size: 11px;
  text-align: center;
}
.attribution a {
  color: hsl(228, 45%, 44%);
}

@media screen and (min-width: 992px) {
  header {
    background-image: url("./assets/images/image-hero-desktop.jpg");
    height: 50vh;
  }

  section.project {
    top: 30%;
  }
}

@media screen and (min-width: 1200px) {
  section.project {
    width: 50%;
  }
}
</style>
