<template>
    <div>
        <div class="normal-joke"> 
                <h3>normal-joke</h3>
                <p>{{lowerCaseJokeDisplay }}</p>
            </div>
            <div class="snake-joke"> 
                <h3>Snake-Like Joke</h3>
                <p>{{ snakeLikeJokeDisplay }}</p>
            </div>
            <div class="loud-joke"> 
                <h3>Loud Joke</h3>
                <p>{{ upperCaseJokeDisplay }} </p>
            </div>
    </div>
</template>

<script>
    export default {
            //created variables with, undefind values.
        data() {
            return {
            lowerCaseJokeDisplay: undefined,
            snakeLikeJokeDisplay: undefined,
            upperCaseJokeDisplay:undefined
        }
    },
        //created methods that take values as an argument,this values are emited from the 
        //NormalJokeButton, SnakeJokeButton, LoudJokeButton components, and mounted with the mount-lifecycle-hook 
    methods: {
        reactToLowerCase( lowerCaseJoke ) {
            //assigned variables to the value of emited data-payload
            this.lowerCaseJokeDisplay = lowerCaseJoke
        },
        reactToSnakeJoke( snakeJoke ){
          //assigned variables to the value of emited data-payload

            this.snakeLikeJokeDisplay = snakeJoke
        },
        reactToUppercaseJoke( upperCaseJoke ) {
           //assigned variables to the value of emited data-payload
            this.upperCaseJokeDisplay = upperCaseJoke
        }
    },
    // created a mouted lifeCycle-hook and registered an on Listeners  with a name of lowerCaseJoke_emite, 
    // snakeLikeJoke_emite, and upperCaseJoke_emite with corressponding functions calls.
    mounted(){
        this.$root.$on( `lowerCaseJoke_emite`, this.reactToLowerCase );
        this.$root.$on( `snakeLikeJoke_emite`, this.reactToSnakeJoke );
        this.$root.$on(`upperCaseJoke_emite`, this.reactToUppercaseJoke);
    },
    }
    
</script>

<style scoped>
.main{
    display: grid;
    place-items: center;
    width: 80%;
    margin: 0 auto;
}
.normal-joke{
    background-color:lightsteelblue;
    display:grid;
    place-items:center;
    margin: 16px;
    width: 100%;
    height:12vh;


}
.snake-joke{
    background-color:rgb(204, 235, 235);
    display:grid;
    place-items:center;
    margin: 16px;
    width: 100%;
    height:12vh;

}
.loud-joke{
    background-color: lightgrey;
    display:grid;
    place-items:center;
    margin: 16px;
    width: 100%;
    height:12vh;

}
h3{
    justify-self: center;
}
p{
    text-align: center;
}
</style>