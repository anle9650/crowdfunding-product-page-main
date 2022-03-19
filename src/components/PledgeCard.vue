<template>
  <div
    :class="[
      'card',
      reward.stock === 0 ? 'inactive' : '',
      selectedId === id ? 'selected' : '',
    ]"
  >
    <div class="card-body">
      <div
        class="
          custom-control custom-radio custom-control-inline
          mt-2
          mb-5 mb-lg-3
          d-lg-flex
        "
      >
        <input
          class="custom-control-input"
          type="radio"
          name="rewardRadios"
          :id="'rewardRadios' + id"
          :value="'option' + id"
          @change="$emit('select-reward', id)"
          :checked="selectedId === id"
        />
        <label
          class="
            custom-control-label
            font-weight-bold
            d-flex
            flex-column flex-lg-row
            ml-3 ml-lg-4
          "
          :for="'rewardRadios' + id"
        >
          <span class="reward-text mb-1 mr-3">{{ reward.name }}</span>
          <span class="pledge-text" v-if="reward.minPledge !== undefined"
            >Pledge ${{ reward.minPledge }} or more</span
          >
        </label>
        <div
          class="d-none d-lg-inline-block ml-auto"
          v-if="reward.stock !== undefined"
        >
          <span class="font-weight-bold mr-2">{{ reward.stock }}</span
          ><span class="text-muted small">left</span>
        </div>
      </div>
      <div class="text-muted mb-4 ml-lg-5 mb-lg-2">
        {{ reward.description }}
      </div>
      <div class="d-lg-none" v-if="reward.stock !== undefined">
        <span class="font-weight-bold mr-2">{{ reward.stock }}</span
        ><span class="text-muted small">left</span>
      </div>
    </div>
    <hr v-if="selectedId === id" />
    <div
      v-if="selectedId === id"
      class="card-body d-lg-flex justify-content-between px-lg-4"
    >
      <div class="text-muted text-center mb-4 mb-lg-3 align-self-center">
        Enter your pledge
      </div>
      <form action="" class="form-inline">
        <div class="input-addon mr-3">
          <span class="text-muted">$</span>
          <input
            type="number"
            class="form-control"
            placeholder="$"
            v-model="pledge"
          />
        </div>
        <button
          class="btn btn-primary badge-pill py-2 px-4 ml-auto"
          @click="$emit('pledge', pledge)"
          data-dismiss="modal"
          data-toggle="modal"
          data-target="#thanksModal"
        >
          <small>Continue</small>
        </button>
      </form>
    </div>
  </div>
</template>

<script>
let id = 0;

export default {
  name: "PledgeCard",
  props: {
    reward: {
      type: Object,
      default() {
        return {
          name: "Pledge with no reward",
          description:
            "Choose to support us without a reward if you simply believe in our project. As a backer, you will be signed up to receive product updates via email.",
        };
      },
    },
    selectedId: Number,
  },
  emits: ["select-reward", "pledge"],
  data() {
    return {
      id: null,
      pledge: this.reward.minPledge ?? 0,
    };
  },
  created() {
    this.id = id;
    id += 1;
  },
};
</script>

<style scoped>
.card {
  position: relative;
}
.card.selected {
  border: 2px solid hsl(176, 50%, 47%);
}

.reward-text:hover {
  cursor: pointer;
  color: hsl(176, 50%, 47%);
}

.custom-control {
  position: relative;
}
.custom-control-label::before,
.custom-control-label::after {
  position: absolute;
  top: 50%;
  left: -2rem;
  transform: translateY(-50%) scale(1.5);
}
.custom-control-input:checked ~ .custom-control-label::before {
  background-color: hsl(176, 50%, 47%);
  border-color: #adb5bd;
}

.form-control {
  width: 6rem;
  border-radius: 16px;
  text-align: center;
  font-weight: bold;
  padding: 1.25em;
}
.form-control:hover {
  cursor: pointer;
  border-color: hsl(176, 50%, 47%);
}
.input-addon {
  position: relative;
}
.input-addon span {
  position: absolute;
  padding: 8px 20px;
  pointer-events: none;
  font-weight: 500;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
/* Firefox */
input[type="number"] {
  -moz-appearance: textfield;
}
</style>