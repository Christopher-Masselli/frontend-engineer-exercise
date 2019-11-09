<template>
  <div>
    <p class="h1 text-center" :class="pickScoreColor(correct)">{{correct}}%</p>
    <table class="table table-hover">
      <thead>
        <tr>
          <th scope="col">Correct answers</th>
          <th scope="col">Your submitted answers</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="x in ans" :class="pickClass(x[0], x[1] )">
            <th scope="row">{{x[0]}}</th>
            <td>{{x[1]}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  name: "Results",
  props: {
    userAns: {
      type: Array,
      required: true
    },
    correctAns: {
      type: Array,
      required: true
    },
  },
  data: () => ({
      ans: null,
      correct: 0
  }),
  created() {
    this.ans = this.correctAns.map( (x, i) => {
      if (x === this.userAns[i]) {
        this.correct++;
      }
      return [x, this.userAns[i]]
    })
    this.correct = this.correct / this.userAns.length * 100
  },
  methods: {
    pickClass(x, y) {
      if (x == y)
      {
        return 'table-success'
      }
      return 'table-danger'
    },
    pickScoreColor(x) {
      if ( x >= 80)
      {
        return 'text-success'
      }
      else if ( x >= 70)
      {
        return 'text-warning'
      }
      else
      {
        return 'text-danger'
      }
    }
  }
};
</script>
