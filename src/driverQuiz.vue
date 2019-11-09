<template>
    <preQuiz v-if="this.curr == -1" v-on:preNext="curr++;"/>
    <Quiz v-else-if="this.curr >= 0 && this.curr < this.total"
      :question="questions[this.curr].text" :answers="questions[this.curr].answers"
      :answered="answered" :green="green" :yellow="yellow" :red="red"
      @hasAnswered="hasAnswered()"
      @quizNext="next"
      />
    <postQuiz v-else-if="this.curr >= this.total"/>

</template>

<script>
import preQuiz from './QuizComps/preQuiz.vue'
import Quiz from './QuizComps/Quiz'
import postQuiz from './QuizComps/postQuiz.vue'

export default {
  props: {
    questions: {
      type: Array,
      required: true
    }
  },
  components: {
      preQuiz,
      Quiz,
      postQuiz
  },
  data() {
    return {
      curr: -1,
      total: this.questions.length,
      answered: false,
      green: Number,
      yellow: Number,
      red: Number,
      answers: [],
      picked: null
    };
  },
  created() {
    this.green = (this.curr / this.total) * 100;
    this.yellow = 0;
    this.red = ((this.total - this.curr - 1) / this.total) * 100;
  },
  methods: {
    hasAnswered() {
      this.answered = false;
      this.yellow = (1 / this.total) * 100;
      this.red = ((this.total - this.curr - 1) / this.total) * 100;
    },
    next(ans) {
      this.answers.push(ans);
      this.answered = true;
      if (this.curr < this.total) {
        this.curr++;
      }
      this.yellow = 0;
      this.green = (this.curr / this.total) * 100;
      this.red = ((this.total - this.curr) / this.total) * 100;

    }
  }
};
</script>
