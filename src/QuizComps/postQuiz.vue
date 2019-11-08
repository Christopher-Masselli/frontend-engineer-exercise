<template>
  <transition name="modal">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="progress">
          <div class="progress-bar bg-success" role="progressbar" style="width: 100%"></div>
        </div>
        <div class="modal-body">
          <p class="h3 text-success text-center">Your answers have been submited for grading.</p>
          <br>
          <img
            class="mx-auto d-block"
            style="width: 40%; margin: auto;"
            center
            src="https://cdn.pixabay.com/photo/2016/10/10/01/49/hook-1727484_960_720.png"
            alt="Check mark"
          >
          <br>
          <p class="h2 text-success text-center">Test completed!</p>
        </div>
      </div>
    </div>
  </transition>
</template>
<script>
export default {
  name: "postQuiz",
  data: () => ({

  })
}
</script>
<style lang="scss" scoped>
</style>
