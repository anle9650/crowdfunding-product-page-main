<template>
  <div>
    <img class="logo" src="../assets/images/logo-mastercraft.svg" alt="" />
    <div class="card">
      <div class="card-body text-center mt-5 mb-3">
        <h5 class="card-title mb-4">Mastercraft Bamboo Monitor Riser</h5>
        <h6 class="card-subtitle mb-4 text-muted">
          A beautiful & handcrafted monitor stand to reduce neck and eye strain.
        </h6>
        <div class="d-lg-flex justify-content-between mx-4">
          <button
            type="button"
            class="btn btn-primary badge-pill px-5 py-3 mr-2"
            data-toggle="modal"
            data-target="#pledgeModal"
          >
            Back this project
          </button>
          <button
            type="button"
            :class="['btn btn-light badge-pill d-lg-flex align-items-center p-0 pr-lg-4', bookmarked ? 'bookmarked' : '']"
            @click="bookmarked = !bookmarked"
          >
            <i :class="['bookmark', bookmarked ? 'bookmarked' : '']"></i>
            <span class="ml-3 d-none d-lg-inline">{{ bookmarked ? 'Bookmarked' : 'Bookmark' }}</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProjectCard",
  data() {
    return {
      bookmarked: false
    }
  }
};
</script>

<style scoped>
img.logo {
  position: relative;
  left: 50%;
  transform: translateX(-50%) translateY(50%);
  z-index: 1;
}
.card .card-title {
  font-weight: 700;
  font-size: 1.5em;
}
button.bookmarked {
  color: hsl(176, 72%, 28%);
}
i.bookmark {
  display: inline-block;
  background: url("../assets/images/icon-bookmark.svg");
  background-size: 56px 56px;
  height: 56px;
  width: 56px;
}
i.bookmark:hover{
  background: url("../assets/images/icon-bookmark-active.svg");
}
i.bookmark.bookmarked {
  background: url("../assets/images/icon-bookmarked.svg");
}
</style>