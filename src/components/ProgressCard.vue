<template>
  <div class="card p-4">
    <div class="card-body text-center mx-auto d-lg-flex text-lg-left mx-lg-0">
      <div class="card-section pr-lg-5">
        <h4 class="card-title font-weight-bold mb-1">
          ${{ dollarsBacked.toLocaleString() }}
        </h4>
        <div class="card-text text-muted">of $100,000 backed</div>
      </div>
      <hr class="d-lg-none"/>
      <div class="card-section px-lg-5">
        <h4 class="card-title font-weight-bold mb-1">
          {{ numBackers.toLocaleString() }}
        </h4>
        <div class="card-text text-muted">total backers</div>
      </div>
      <hr class="d-lg-none"/>
      <div class="pl-lg-5">
        <h4 class="card-title font-weight-bold mb-1">56</h4>
        <div class="card-text text-muted">days left</div>
      </div>
    </div>
    <div class="progress mx-3 my-4">
      <div
        class="progress-bar"
        role="progressbar"
        :style="{ width: `${progress}%` }"
        :aria-valuenow="progress"
        aria-valuemin="0"
        aria-valuemax="100"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProgressCard",
  props: {
    dollarsBacked: {
      type: Number,
      default: 0,
    },
    numBackers: {
      type: Number,
      default: 0,
    },
  },
  computed: {
      progress() {
          return this.dollarsBacked / 100000 * 100;
      }
  }
};
</script>

<style scoped>
.progress {
    border-radius: 10px;
}
.progress .progress-bar {
    background-color: hsl(176, 50%, 47%);
    border-radius: 10px;
}

@media screen and (min-width: 992px) {
  .card-section {
    border-right: 1px solid lightgrey;
  }
}
</style>