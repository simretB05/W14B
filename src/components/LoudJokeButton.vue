
<template>
    <div>
        <button class="loud-btn" @click="makeUpperCase"  :upperCaseJoke="upperCaseJoke" >Loud joke</button> 
    </div>
</template>

<script>
export default {
    components: {
    },
    //created variables with, undefind values.
    data() {
        return {
            normalJoke: undefined,
            upperCaseJoke: undefined,
            dataFromBtnUpprcased:undefined

            }
    },
    //created methods that take  emited value and details value as an argument.
   
    methods: {
        makeUpperCase( details ){
        // assigned a new variable to the value of an attribute 
            let dataFromBtn = details[`target`].getAttribute( `upperCaseJoke` )
        //assigned variable to the value of dataFromBtn which is, a data that is 
        // attached to the detalis target attributs, the data we get when we click a btn, 
        // we then make the result, uppercase by using built-in fucntion.
            this.dataFromBtnUpperCased = dataFromBtn.toUpperCase()
        // used global emit method to emit a data payload with the name upperCaseJoke_emite
            this.$root.$emit( `upperCaseJoke_emite`, this.dataFromBtnUpperCased  )

            
        },
      //created methods that take  emited values as an argument,  and assigned a variable to the emit value
       getMainJoke( joke ){
            this.normalJoke = joke
            this.upperCaseJoke = this.normalJoke
        }
    },
    // created a mouted lifeCycle-hook and registered an on Listeners  with a name of joke_emit  
    // and  corressponding functions call.
    mounted(){  
        this.$root.$on( `joke_emit`, this.getMainJoke)
        },
}

</script>

<style scoped>
.loud-btn{
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
.loud-btn:active{
    transform: translateY(3px);
box-shadow: none;
}
</style>