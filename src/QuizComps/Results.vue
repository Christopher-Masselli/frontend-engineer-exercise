<template>
<p>test</p>
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
    }
  },
  data: () => ({

  })
};
</script>
