<template>
    <div>
<button class="get-btn" @click="handelGlobalJokeEmit">Generate Joke</button>
    </div>
</template>

<script>
import axios from "axios";
 //created variables with, undefind values.
export default {
        data() {
            return {
                joke: undefined,
            }
    },
 //created method that handles a global emite with a joke_emit name and payload of a joke value
    methods: {

        handelGlobalJokeEmit(){
            this.$root.$emit(`joke_emit`, this.joke );

        }
    },
    // created a mouted lifeCycle-hook that processes an Axios requst
    // and  on a response assign a variable to the value of a response   
        mounted(){
        axios.request({
            url: `https://ron-swanson-quotes.herokuapp.com/v2/quotes`
        } ).then( ( response ) =>{
            this.joke = response[`data`][0]
            
        } ).catch((error) =>{
            error;
            this.errorData="please try again"
        } )
    }
    }
</script>

<style scoped>
.get-btn{
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
.get-btn:active{
    transform: translateY(3px);
box-shadow: none;
}
p{
    text-align: center;

}
</style>