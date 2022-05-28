
<template>

    <!-- Display card color if correct or incorrect  -->
    <div :class="`container ${submitted ? `${gradeChoices(question.answer)}-card`:''}`" v-for="(question, i) in questions"  :key="question.id">
        <div class="card">
        <h2>.{{i + 1}}) {{question.questionTitle}}</h2>
            <Answers :answers="question.options" 
            :name="question.questionTitle" 
            :answer="question.answer" 
            :handleSelection="handleSelection" 
            :gradeChoices="gradeChoices"
            :submitted="submitted"/>
              <div class="results">    
        <p v-show="submitted" :class="`${submitted ? `${gradeChoices(question.answer)}-text`:''}`">{{gradeChoices(question.answer) === "pass" ? 'Correct' :"Incorrect"}}</p>
        </div>
        </div>
    </div>   
</template>
<script>    
import Answers from "./Answers.vue"

export default {
   
    props: {
        questions: Array,
        submitted: Boolean, 
        handleSelection: Function,
        correctQuestions: Array
    },
    components: { Answers },
    methods:{
      gradeChoices(answer){
        
    const filteredQuestions = this.correctQuestions.filter((correct) => correct === answer)[0]

            if(filteredQuestions !== undefined){
                return 'pass'
            }else{
                return 'error'
            }
      }
    }
}
</script>
<style scoped>
input{
padding: 10px 20px;
color: white;
background-color: green;
transition: 300ms ease-in-out;
  border-radius: 5px;
    border: 3px solid rgba(26, 77, 26, 0.856)   
}
input:hover{
transition: 300ms ease-in-out;
background-color: rgb(152, 202, 76);   
border: 3px solid green;

}
.btn-group{
    display: flex;
    justify-content: center;
    margin-bottom: 0.75rem;
}
.container{
    border-radius: 8px;
    margin-bottom: 1.125rem;
    background-color: white;
    max-height: 400px;
    padding:15px 10px;
    box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
}
li{
    list-style: none;
}
.card{
   display: flex;
   flex-direction: column;
}
.card h2{   
    font-size: 18px;
    margin-bottom: 1.125rem;
}
.pass-text{
    color: green;
}
p{
    color:red;
    text-align: center;
    margin-bottom: 1.125rem
}
.warning-text{
    color:orange
}
.error-text{
    color:red
}

.pass-card{
    border: 2px solid green;
}
.warning-card{
    border: 2px solid orange;
}
.error-card{
 border: 2px solid red;

}
.results{
   display: flex;
   justify-content: flex-end; 
   font-weight: 900;

}
.question-group{
    margin-bottom: 0.75rem;
}
.question-group input{
    margin-right: 10px;
}

</style>