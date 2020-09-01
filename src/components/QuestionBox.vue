<template>
  <div class="question-box-container">
  <b-jumbotron>
    <template v-slot:lead>
      {{ currentQuestion.question }}
    </template>

    <hr class="my-4">

    <b-list-group>
        <b-list-group-item 
        v-for="(answer, index) in shuffledAnswers" :key="index"
        @click.prevent="selectAnswere(index)"
        :class="answerClass(index)"    
        >   
         {{ answer }}  
        
        </b-list-group-item>
       
    </b-list-group>

    <b-button @click="prev" variant="success" href="#">Prev</b-button>
    <b-button variant="primary"
    @click="submitAnswere"
    :disabled="selectedIndex === null || answered"
    >
    Submit
    </b-button>
    <b-button @click="next" variant="success" href="#">Next</b-button>
  </b-jumbotron>
</div>
</template>


<script>
import _ from 'lodash'
export default {
    props:{
        // currentQuestion : Object adalah json dari api v-slot:lead
        currentQuestion : Object,
        //next & prev adalah unutk metriger b-button @click
        next: Function,
        prev:Function,
        increment: Function
    },
    data(){
        return{
            selectedIndex: null,
            correctIndex: null,
            shuffledAnswers: [],
            answered: false

        }
    },
    computed: {
        answers(){
            let answers=[...this.currentQuestion.incorrect_answers]
            answers.push(this.currentQuestion.correct_answer)
            return answers
        }
    },
    watch: {
        currentQuestion: {
            immediate: true,
            handler() {
                this.selectedIndex = null
                this.answered = false
                this.shuffleAnswers()
            }
        }
    },
    methods: {
        selectAnswere(index){
            this.selectedIndex = index
        },
        submitAnswere() {
          let isCorrect =false
          if(this.selectedIndex === this.correctIndex) {
            isCorrect =true
          }
          this.answered =true
          this.increment(isCorrect)
        } ,
        shuffleAnswers() {
        let answers = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer]
        this.shuffledAnswers = _.shuffle(answers)
        this.correctIndex = this.shuffledAnswers.indexOf(this.currentQuestion.correct_answer)
        },
        answerClass(index){
            let answerClass =''
            if (!this.answered &&  this.selectedIndex === index)
            {
                answerClass ='selected'
            } else if (this.answered && this.correctIndex === index ){
                answerClass ='correct'
            } else  if (this.answered &&
              this.selectedIndex === index &&
              this.correctIndex !== index
              ){
                answerClass ='incorrect'
            }

            return answerClass
        } 
       
    },
    mounted(){
        this.shuffleAnswers()
    }
    
    //mounted(){
    //    console.log(this.currentQuestion)
    //}
}
</script>

<style scoped>
.list-group {
margin-bottom: 15px;
}
.list-group-item:hover {
    background: #fedb7a75;
    border: 1px solid #fedb7a75;
    cursor: pointer;
}
.btn {
margin: 0 5px;
}
.selected {
    background-color: lightblue;
    color: #fff;
}
.correct {
    background-color: lightgreen;
}
.incorrect {
    background-color: red;
}
</style>