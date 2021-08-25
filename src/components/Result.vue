<template>
  <div class="result">
    <div class="title">{{ results[resultIndex].title }}</div>
    <div class="desc">{{ results[resultIndex].desc }}</div>
  </div>
</template>

<script>
  export default {
    name: "Result",
    props: ["results", "correctAnswers"],
    computed: {
      resultIndex() {
        let index = 0;
        this.results.forEach((r, i) => {
          if (r.min <= this.correctAnswers && r.max >= this.correctAnswers)
            index = i;
        });
        return index;
      },
    },
  };
</script>