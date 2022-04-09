<template>
  <form @submit.prevent="submitFun()" class="accent-pink-500 space-y-4 flex flex-col">
    <div class="justify-evenly text-left px-10 py-3 mx-10 shadow-md shadow-green-200/50 rounded-md" v-for="(quiz, im) in allQuiz" :key="quiz.qno">
      <h2 class="text-lg text-blue-700 font-bold">{{ quiz.qno }} . {{ quiz.statement }}</h2>
      <div v-for="(option, index) in quiz.options" :key="index">
        <input 
          v-if="!isSubmited"
          type="radio"
          :name="quiz.qno"
          :value="option.is_correct + ' ' + option.value"
          :id="option.value + quiz.qno"
          v-model="formValues[im]"
        />
        <label :for="option.value + quiz.qno">{{ option.value }}</label>
      </div>
      <div v-show="isSubmited">
        <div class="bg-yellow-200/50 rounded-sm shadow-sm pl-5 py-3 m-1">
          <h2
            class="text-green-400"
            v-if="formValues[im].split(' ')[0] === 'true' ? true : false"
          >You are correct</h2>
          <div v-else>
            <h2 class="text-red-500">You are wrong.</h2>
            <div v-for="(option, index) in quiz.options" :key="index">
              <h2 class="text-green-400" v-if="option.is_correct">{{ option.value }}</h2>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div>
      <button class="transition-all duration-200 ease-in-out rounded-lg px-10 py-2 my-5 bg-lime-500 text-white hover:bg-lime-300 hover:text-slate-600" v-if="!isSubmited">Submit</button>
    </div>
  </form>
</template>

<script>
export default {
  props: ['id'],
  name: "Week",
  data() {
    return {
      allQuiz: [],
      isSubmited: false,
      formValues: {
        0: "",
        1: "",
        2: "",
        3: "",
        4: "",
        5: "",
        6: "",
        7: "",
        8: "",
        9: "",
      },

    };
  },
  computed: {},
  mounted() {
    fetch("http://localhost:3000/data")
      .then((res) => res.json())
      .then((data) => (this.allQuiz = data[this.id - 1].qustions))
      .catch((err) => onsole.log(err.message));
  },
  methods: {

    submitFun() {
      this.isSubmited = true;
    },
  },
  computed: {
    shuffleArray(inputArray) {
      if (!this.isSubmited) return inputArray.sort(() => Math.random() - 0.5);
      else return inputArray;
    },
  }
}
</script>

<style scoped>
</style>