<template>
  <div
    class="modal fade"
    id="thanksModal"
    tabindex="-1"
    role="dialog"
    aria-labelledby="thanksModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog" role="document">
      <div class="modal-content text-center">
        <img class="my-4" src="../assets/images/icon-check.svg" alt="check" />
        <h5 class="modal-title font-weight-bold mb-3" id="thanksModalLabel">
          Thanks for your support!
        </h5>
        <div class="modal-body px-4">
          <div class="modal-text text-muted mb-5">
            Your pledge brings us one step closer to sharing Mastercraft Bamboo
            Monitor Riser worldwide. You will get an email once our campaign is
            completed.
          </div>
          <button
            type="button"
            class="btn btn-primary badge-pill py-3 px-5 mb-4"
            data-dismiss="modal"
          >
            Got it!
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ThanksModal",
};
</script>