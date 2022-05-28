<template>
    <div class="container">         
        <form class="quizzes" v-for="(quiz, i) in data" :key="i" @submit="onSubmit">
            <h1>{{quiz.title}}</h1>
            <Questions :questions="quiz.questions" :submitted="submitted" :handleSelection="handleSelection"  :correctQuestions="correctQuestions"/>
    <div class="btn-group">
        <input class="pass" type="submit" value="Submit"/>
    </div>  
        </form>
    </div>
</template>
<script>
import Questions from "../components/Questions.vue"

export default {
    components:{
        Questions
    },
    props:{
        data: Array,
        onSubmit: Function,
        handleSelection: Function,
        submitted:Boolean,
        correctQuestions:Array
    },
  
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
width: 100%;
margin-bottom: 1.125rem;
}
.container h1{
    margin-left: 20px;
    text-align: left;
    font-size: 25px;
    margin-bottom: 2rem;
}@media (min-width:768px) {
    .container h1{
        width: 80%;
        margin-left: auto;
        margin-right: auto;
    }
}

.quizzes{
    display: flex;
    flex-direction: column;
    margin-left: 20px;
    margin-right: 20px;
}
.quizzes h1{
    margin: 2rem;
}
@media (min-width:768px) {
    .quizzes{
        width: 80%;
        margin-left: auto;
        margin-right: auto;
    }
}

p{
    color:red;
    text-align: center;
    margin-bottom: 1.125rem
}
</style>