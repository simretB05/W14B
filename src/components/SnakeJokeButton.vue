
<template>
    <div>
        <button class="SnakeJoke-btn" @click="makeSnakeLike"  :snakeLikeJoke="snakeLikeJoke" >Snak-like joke</button> 
    </div>
</template>

<script>
export default {
     //created variables with, undefind values.
    data() {
        return {
            normalJoke: undefined,
            snakeLikeJoke: undefined,
            modifiedSnakeWords: undefined,
            snake_joke:undefined

            }
    },
    //created methods that take  emited value and details value as an argument.
    methods: {
        makeSnakeLike( details ){
            // assigned a new variable to the value of an attribute 
            let dataFromSnakeLikeBtn = details[`target`].getAttribute( `snakeLikeJoke` )
            //assigned variables to the value of dataFromSnakeLikeBtn which is, a data that is 
            // attached to the detalis target attributs, the data we get when we click a btn, 
            // we then make the result, snake-like by using built-in fucntion. .split('') to
            // splite and make make all words a string and then assign the result to another 
            // variable which uses the map method to map through each string and  and add the __  characters
            //  after that ist joined  back to make it one word using .join() built in function
            let dataFromBtnSnakeJoke = dataFromSnakeLikeBtn.split( ' ' );
            this.modifiedSnakeWords = dataFromBtnSnakeJoke.map( word => word + `__` )
            this.snake_joke = this.modifiedSnakeWords.join( '' )
            // used global emit method to emit a data payload with the name upperCaseJoke_emite
            this.$root.$emit( `snakeLikeJoke_emite`, this.snake_joke )

            
        },
    //created methods that take  emited values as an argument,  and assigned a variable to the emit value
        getMainJoke( joke ){
            this.normalJoke = joke
            this.snakeLikeJoke = this.normalJoke
        }
    },
    // created a mouted lifeCycle-hook and registered an on Listeners  with a name of joke_emit  and
    //  corressponding functions call.
    mounted(){
            
        this.$root.$on( `joke_emit`, this.getMainJoke)
        },
}

</script>

<style scoped>
.SnakeJoke-btn{
width: 192px;
background-color: #79adde;
border: none;
border-radius: 25px;
color: white;
font-weight: 700;
padding: 7px;
transition: background-color 0.5s ease;
box-shadow: 0 3px 0 #afcce7;
margin:16px ;


}
.SnakeJoke-btn:active{
    transform: translateY(3px);
box-shadow: none;
}
p{
    text-align: center;
}
</style>