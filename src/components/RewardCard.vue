<template>
  <div :class="['card p-2', reward.stock === 0 ? 'inactive' : '']">
    <div class="card-body">
      <h6 class="d-flex flex-column mb-4 flex-lg-row justify-content-between">
        <span class="font-weight-bold mb-1">{{ reward.name }}</span>
        <span class="pledge-text" v-if="reward.minPledge !== undefined"
          >Pledge ${{ reward.minPledge }} or more</span
        >
      </h6>
      <div class="text-muted mb-4">
        {{ reward.description }}
      </div>
      <div class="d-lg-flex justify-content-between">
        <div class="mb-4 mb-lg-0">
            <span class="stock-text font-weight-bold mr-2 align-middle">{{
              reward.stock
            }}</span
            ><span class="text-muted align-middle">left</span>
        </div>
        <button
          class="btn btn-primary badge-pill py-2 px-4"
          @click="$emit('select-reward', id)"
          data-toggle="modal"
          data-target="#pledgeModal"
        >
          <small>{{ reward.stock != 0 ? 'Select Reward' : 'Out of Stock' }}</small>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
let id = 0;

export default {
  name: "RewardCard",
  props: {
    reward: {
      type: Object,
      required: true,
    },
  },
  emits: ["select-reward"],
  data() {
    return {
      id: null,
    };
  },
  created() {
    this.id = id;
    id += 1;
  },
};
</script>

<style scoped>
.stock-text {
  font-size: 2em;
}
</style>