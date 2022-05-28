<script setup>
import Navbar from './components/navbar.vue';
import Results from './components/Results.vue';
import Quizzes from './components/Quizzes.vue';
import data from "../questions.json"
</script>

<script>
// initialState
let allQuestions = data[0].questions.length
let grade
let correctQuestions = []

export default{
data(){
  return {
    data,
    grade,
    allQuestions,
    correctQuestions,
    submitted : false
  }
}, 
// Component Methods
methods:{
  onSubmit(e){  
   this.handleSubmitted()
    e.preventDefault();
  },
  handleSubmitted(){
   this.submitted = !this.submitted
    window.scrollTo(0,0);
  },

  // handle selection of and adjust score  
  handleSelection(answer, option){
      answer === option ? this.calculateScore(option) : null
  },

    //calcluate the selected question based on how many is right vs total questions
    // using an array of correctQuestions
  calculateScore(option){
    if(correctQuestions.includes(option)){
      return null
    }else{  
      correctQuestions.push(option)
    }
    this.grade = Math.floor( correctQuestions.length / allQuestions * 100)

  }

}

}
//Component Templates 
</script>
<template>
    <Navbar/>
  <main>
    <Results :grade="grade" :allQuestions="allQuestions" :correctQuestions="correctQuestions.length"  :submitted="submitted"/>
    <Quizzes :data="data"  :handleSelection="handleSelection" :onSubmit="onSubmit" :submitted="submitted" :correctQuestions="correctQuestions"/>
  </main>
</template>


<!-- Component Styles   -->
<style>
@import url(./assets/base.css);
main{
height: 85vh;
display: flex;
flex-direction: column;
width:100%;
}
</style>
