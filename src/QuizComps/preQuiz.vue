<template >
  <transition name="modal" width="100px">
    <div class="modal-dialog">
      <div class="modal-content">
        <img
          style="width: 100%; margin: auto;"
          src="https://storage.needpix.com/rsynced_images/quiz-2058883_1280.png"
        >
        <div class="modal-footer">
          <button type="button" class="btn btn-primary" v-on:click="$emit('preNext')">Begin</button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
};
</script>
