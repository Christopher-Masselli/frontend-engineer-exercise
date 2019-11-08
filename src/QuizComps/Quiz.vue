<template>
  <transition name="modal">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="progress">
          <div class="progress-bar bg-success" role="progressbar" :style="{ width: green + '%'}"></div>
          <div
            class="progress-bar bg-warning progress-bar-striped progress-bar-animated"
            role="progressbar"
            :style="{ width: yellow + '%'}"
          ></div>
          <div class="progress-bar bg-danger" role="progressbar" :style="{ width: red + '%'}"></div>
        </div>
        <div class="modal-body" >
          <p>{{question}}</p>
          <fieldset class="form-group">
            <div class="form-check" v-for="(ans, index) in answers">
              <label class="form-check-label">
                <input
                  type="radio"
                  class="form-check-input"
                  name="optionsRadios"
                  id="optionsRadios1"
                  :value="ans"
                  v-on:click="$emit('hasAnswered')"
                  v-model="picked"
                >
                {{ans}}
              </label>
            </div>
          </fieldset>
        </div>
        <div class="modal-footer" >
          <button
            :disabled="answered"
            type="button"
            class="btn btn-primary"
            v-on:click="$emit('quizNext', picked)"
          >Next question</button>
        </div>
      </div>
    </div>
  </transition>
</template>
<script>
export default {
  name: "",
  props: {
    answered: {
      type: Boolean,
      required: true
    },
    question: {
      type: String,
      required: true
    },
    answers: {
      type: Array,
      required: true
    },
    green: {
      type: Number,
      required: true
    },
    yellow: {
      type: Number,
      required: true
    },
    red: {
      type: Number,
      required: true
    },

  },
  data: () => ({
    picked: null
  })
}
</script>
