
<template>
    <div>
        <button class="normal-btn" @click="makeLowerCase"  :lowerCaseJoke="lowerCaseJoke" >Normal joke</button> 
    </div>
</template>

<script>
export default {
    components: {
    },
    data() {
        return {
            normalJoke: undefined,
            lowerCaseJoke: undefined,
            dataFromBtnLowercased:undefined

            }
    },
 //created methods that take  emited value and details value as an argument.
    methods: {
        makeLowerCase( details ){
            // assigned a new variable to the value of an attribute 
            let dataFromBtn = details[`target`].getAttribute( `lowerCaseJoke` )
            //assigned variables to the value of dataFromBtn which is, a data that is 
            // attached to the detalis target attributs, the data we get when we click a btn, 
            // we then make the result, lowercase by using built-in fucntion.
            this.dataFromBtnLowercased = dataFromBtn.toLowerCase()
            // used global emit method to emit a data payload with the name upperCaseJoke_emite
            this.$root.$emit( `lowerCaseJoke_emite`, this.dataFromBtnLowercased  )

            
        },
         //created methods that take  emited values as an argument,  and assigned a variable to the emit value

        getMainJoke( joke ){
            this.normalJoke = joke
            this.lowerCaseJoke = this.normalJoke
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
.normal-btn{
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
.normal-btn:active{
    transform: translateY(3px);
box-shadow: none;
}
</style>