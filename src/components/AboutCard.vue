<template>
  <div class="card px-2 pt-4">
    <div class="card-body">
      <h5 class="card-title font-weight-bold mb-4">About this project</h5>
      <div class="card-text text-muted mb-5">
        <p class="mb-4">
          The Mastercraft Bamboo Monitor Riser is a sturdy and stylish platform
          that elevates your screen to a more comfortable viewing height.
          Placing your monitor at eye level has the potential to improve your
          posture and make you more comfortable while at work, helping you stay
          focused on the task at hand.
        </p>
        <p>
          Featuring artisan craftsmanship, the simplicity of design creates
          extra desk space below your computer to allow notepads, pens, and USB
          sticks to be stored under the stand.
        </p>
      </div>
      <RewardCard
        class="mb-4"
        v-for="(reward, index) in rewards"
        :key="index"
        :reward="reward"
        @select-reward="rewardId => $emit('select-reward', rewardId)"
      />
    </div>
  </div>
</template>

<script>
import RewardCard from "./RewardCard.vue";

export default {
  name: "AboutCard",
  components: {
    RewardCard,
  },
  props: {
    rewards: {
      type: Array,
      default: () => [],
    },
  },
  emits: ["select-reward"]
};
</script>