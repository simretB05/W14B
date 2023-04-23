<template>
    <div>
      <button  @click="get_all_users" >GET THE USERS</button>
      <section ref="user_container">
        <div v-if="usersData">
          <div  v-for="(userData,i) in usersData" :key="i">
            <h3>{{ userData[`first_name`] }}</h3>
            <p>{{ userData[`last_name`] }}</p>
            <img :src="userData[`avatar`]">
          </div>
        </div>
        <div v-else>
          <h2> {{displayError}}</h2>
        </div>
      </section>
      </div>
  </template>
  
  <script>
  import axios from "axios";
  export default {
    data() {
      return {
          users: [],
          errorMessage:undefined,
          usersData: undefined,
          displayError:undefined
      };
    },
    methods: {
        get_all_users(){
          this.usersData = this.users

      },
    },
    
    mounted(){
        axios.request({
            url: `https://reqres.in/api/users`
        } ).then( ( response ) =>{
            this.users = response[`data`][`data`]
          } ).catch( ( error ) =>
        {
            error;
              this.errorMessage = "please try again"
        } )
    }
  };
  </script>