<template>
  <form @submit.prevent="submitFun()">
    <div v-for="(quiz, im) in allQuiz" :key="quiz.qno">
      <h2>{{ quiz.qno }} . {{ quiz.statement }}</h2>
      <div v-for="(option, index) in quiz.options" :key="index">
        <input
          type="radio"
          :name="quiz.qno"
          :value="option.is_correct+' '+option.value"
          :id="option.value+quiz.qno"
          v-model="formValues[im]"
        />
        <label :for="option.value+quiz.qno">{{ option.value }}</label>
      </div>
      <div v-show="isSubmited">
        <div>
          <h2 class="correct" v-if="formValues[im].split(' ')[0] === 'true' ? true : false">You are correct</h2>
          <div v-else>
            <h2 class="wrong">You are wrong.</h2>
            <div v-for="(option, index) in quiz.options" :key="index">
              <h2 class="correct" v-if="option.is_correct">
                {{ option.value }}
              </h2>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div>
      <button v-if="!isSubmited">Submit</button>
    </div>
  </form>
</template>

<script>
export default {
  props:['id'],
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
computed:{},
mounted() {
    fetch("http://localhost:3000/data")
      .then((res) => res.json())
      .then((data) => (this.allQuiz = data[this.id-1].qustions))
      .catch((err) => onsole.log(err.message));
    },
methods: {

    submitFun() {
      this.isSubmited = true;
    },
  },
computed:{
    shuffleArray(inputArray) {
      if (!this.isSubmited) return inputArray.sort(() => Math.random() - 0.5);
      else return inputArray;
    },
}
}
</script>

<style scoped>
form{
max-width: 900px;
margin: 30px auto;
background:white;
text-align: left;
padding: 40px;
border-radius: 10px;
}
label{
color: black;
display: inline-block; 
margin: 25px 0 15px; 
font-size: 1em; 
text-transform: uppercase; 
font-weight: bold;
letter-spacing: 1px;
font-weight: bold;
}
input{
  padding: 10px;
}
button{
  padding: 10px 20px;
  color: white;
  font-weight: bold;
  background:blue;
  border-radius: 10px;
  text-align: middle;
}
.correct {
  color: green;
  font-weight: bold;
}
.wrong{
  color: red;
  font-weight: bold;
}
</style>