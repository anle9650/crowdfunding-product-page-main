<template>
  <div
    class="modal fade"
    id="pledgeModal"
    tabindex="-1"
    role="dialog"
    aria-labelledby="pledgeModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-lg" role="document">
      <div class="modal-content">
        <div class="d-flex justify-content-between mx-4 mt-4 mb-1">
          <h5 class="modal-title" id="pledgeModalLabel">Back this project</h5>
          <button
            type="button"
            class="close"
            data-dismiss="modal"
            aria-label="Close"
          >
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body px-4">
          <div class="text-muted mb-4">
            Want to support us in bringing Mastercraft Bamboo Monitor Riser out
            in the world?
          </div>
          <PledgeCard
            class="mb-4"
            :selectedId="selectedId"
            @select-reward="selectReward"
            @pledge="addPledge"
          />
          <PledgeCard
            class="mb-4"
            v-for="reward in rewards"
            :key="reward.id"
            :reward="reward"
            :selectedId="selectedId"
            @select-reward="selectReward"
            @pledge="addPledge"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PledgeCard from "./PledgeCard.vue";

export default {
  name: "PledgeModal",
  components: {
    PledgeCard,
  },
  props: {
    rewards: {
        type: Array,
        default: () => []
    },
    selectedReward: Number
  },
  emits: ["pledge"],
  data() {
    return {
      selectedId: this.selectedReward,
    };
  },
  methods: {
    selectReward(rewardId) {
      this.selectedId = rewardId;
    },
    addPledge(ammount) {
      this.$emit("pledge", this.selectedId, ammount);
    },
  },
  watch: {
      selectedReward(newId) {
          this.selectedId = newId;
      }
  }
};
</script>

<style scoped>
.modal-title {
  font-weight: 700;
}
</style>