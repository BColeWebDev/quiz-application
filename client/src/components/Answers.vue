<template>
    <p>Choose one:</p>
    <div class="answer-group" v-for="({option}, i) in answers" :key="i">
    <div  :class="`${option === answer && submitted ? 'right-answer':''}`">
    <input  type="radio" :id="i + 1" :value="option" :name="name" @click="handleSelection(answer, option )" required>
    <label :for="option">{{option}}</label>   
    </div>    
    </div>

  
</template>
<script>

export default {    
      data() {
      return {
      }
    },
    props:{
        answers:Array,
        answer: String,
        name:String,
        handleSelection:Function,
        gradeChoices:Function,
        submitted: Boolean
    },

}
</script>
<style scoped>

.answer-group{
    padding:10px;
    margin-bottom: 0.75rem;
}
.right-answer{
background-color: green;
width: 70%;
padding: 10px;
color: white;
border-radius: 10px;
border:2px solid darkgreen

}
p{
 margin-bottom: 1.125rem;
}

input{
    margin-left: 20px;
    cursor: pointer;
}
input:required{
    color:red;
}

label{
    margin-left: 20px;
}
</style>