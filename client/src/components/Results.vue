<template lang="">
<div class="container" v-show="submitted">
    <h2>Result</h2>

    <div class="score">
        <h3>You got {{correctQuestions}} / {{allQuestions}} correct</h3>
        <p :class="`${grade <= 50 ? 'fail' : 'pass'}`">{{`${grade === undefined ? 0 : grade}`}}%</p>
    </div>
</div>
 
</template>
<script>
export default { 
 props:{
     grade:Number,
     allQuestions:Number,
     correctQuestions: Number,
     submitted: Boolean
 }
}
</script>
<style scoped>
.container{
padding:2rem;
display: flex;
justify-content: center;
align-items: center;
flex-direction: column;
}
.score{ 
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.container h2
{
font-size: 30px;
text-decoration: underline;
margin-bottom: 12px;
}   
    .pass,.fail{
        font-size: 20px;
        font-weight:700;
    }
    .pass{
        color:green;
    }
    .fail{
        color:red;
    }
    
</style>