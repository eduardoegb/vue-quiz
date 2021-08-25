<template>
  <div class="ctr">
    <questions
      v-if="questionsAnswered < questions.length"
      :questions="questions"
      :questionsAnswered="questionsAnswered"
      @question-answered="onQuestionAnswered"
    />
    <result v-else />
    <button type="button" class="reset-btn">Reset</button>
  </div>
</template>

<script>
  import Questions from "./components/Questions.vue";
  import Result from "./components/Result.vue";

  export default {
    name: "App",
    components: { Questions, Result },
    data() {
      return {
        questionsAnswered: 0,
        correctAnswers: 0,
        questions: [
          {
            q: "What is 2 + 2?",
            id: "1",
            answers: [
              {
                text: "4",
                id: "1a",
                is_correct: true,
              },
              {
                text: "3",
                id: "1b",
                is_correct: false,
              },
              {
                text: "Fish",
                id: "1c",
                is_correct: false,
              },
              {
                text: "5",
                id: "1d",
                is_correct: false,
              },
            ],
          },
          {
            q: 'How many letters are in the word "Banana"?',
            id: "2",
            answers: [
              {
                text: "5",
                id: "2a",
                is_correct: false,
              },
              {
                text: "7",
                id: "2b",
                is_correct: false,
              },
              {
                text: "6",
                id: "2c",
                is_correct: true,
              },
              {
                text: "12",
                id: "2d",
                is_correct: false,
              },
            ],
          },
          {
            q: "Find the missing letter: C_ke",
            id: "3",
            answers: [
              {
                text: "e",
                id: "3a",
                is_correct: false,
              },
              {
                text: "a",
                id: "3b",
                is_correct: true,
              },
              {
                text: "i",
                id: "3c",
                is_correct: false,
              },
            ],
          },
        ],
        results: [
          {
            min: 0,
            max: 2,
            title: "Try again!",
            desc: "Do a little more studying and you may succeed!",
          },
          {
            min: 3,
            max: 3,
            title: "Wow, you're a genius!",
            desc: "Studying has definitely paid off for you!",
          },
        ],
      };
    },
    methods: {
      onQuestionAnswered(is_correct) {
        if (is_correct) this.correctAnswers++;
        this.questionsAnswered++;
      },
    },
  };
</script>