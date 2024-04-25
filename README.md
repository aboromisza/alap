# alap
Nav: 
import { RouterLink} from "vue-router";
<router-link to="/"

app
import { RouterView } from 'vue-router'
import NavBar from "@/components/layouts/NavBar.vue";
<nav-bar/>
<RouterView />

http.js
import axios from "axios";
const http = axios.create({
    baseURL:"http://localhost:3000"
})
export {http}

import {http} from "@/utils/http.js"
  export default {
  
    data (){
        return{
          post: []
      }
    },
    
    methods: {
        goBack() {
      this.$router.go(-1); 
       
    },
	async getPosts(){
      const  response = await http.get('posts')
      this.posts=await response.data.blogPosts;
    },
    async getData(){
      const response = await http.get(`/posts/${this.$route.params.id}`);
      this.post=response.data.blogPosts;
      console.log(response)
    },

   
    },
    mounted() {

    this.getData();  
  }
  
  <div class="col-md-3" v-for="item in questions" :key="item.id">
  <p class="card-text">ID: {{ item.id }}</p>
  
  async deleteUser(id) {
    try {
      await http.delete(`/user/${id}`);
      await this.getUsers(); // Felhasználók újratöltése a törlés után
    } catch (error) {
      console.error('Hiba történt a felhasználó törlése közben:', error);
    }

import { Field, Form, ErrorMessage } from 'vee-validate'; // a mezők/adatok validálásához
import * as yup from 'yup';
import ErrorModal from "@/components/layouts/ErrorModal.vue"; // A felugró ablak komponens

const schema = yup.object ({
  email: yup.string().required().email(),
  password: yup.string().required(),
  
});

@submit="loginUser" :validation-schema="schema"

  <div class="w-50 mt-5 m-auto p-5 bg-info bg-opacity-25">

const errorModal = ref(null);
const loginUser = async () => {
  try {
    const response = await http.post('login', user.value);

  } catch (error) {
    loginStatus.value = 'error';
    errorModal.value.displayError(error.response.data.error); //ha a catch ág fut le, meghívjuk ezt a Modalt, és kiíratjuk a hibát

    console.error('Error during registration:', error.response.data);
  }
};

  <Form class="card-body cardbody-color p-lg-5" @submit="loginUser" :validation-schema="schema">
            <div class="text-center">
              <h3>Bejelentkezés</h3>
              <img src="../img/questionm.jpg" class="img-fluid profile-image-pic img-thumbnail rounded-circle my-3"
                width="200px" alt="profile">
            </div>
            <div class="mb-3">
              <Field name="email" type="text" class="form-control" id="email" v-model="user.email" 
                placeholder="Email"/>
              <ErrorMessage name="email" as="div" class="alert alert-danger m-1"/>
			    <ErrorModal ref="errorModal" />
				</div>
               <div class="text-center"><button type="submit" class="btn btn-color px-5 mb-5 w-100">Bejelentkezés</button>
            
			   </Form>

const newUser = ref({
  name: '',
  email: ''})

const registerUser = async () => {
  try {
    const response = await http.post('registration', newUser.value);
    const responseData = response.data; // A válasz adatai
	
	
	
	modal
	<template>
    <div :class="{ 'alert alert-danger m-1': showModal }">
      <b-modal v-model="showModal" title="Hibaüzenet">
        
        <p >{{ errorMessage }}</p>
      </b-modal>
    </div>
  </template>
  
<script>

export default {

  data() {
    return {
      showModal: false,
      errorMessage: ""
    };
  },
  methods: {
    displayError(message) {
      this.errorMessage = message;
      this.showModal = true;
      setTimeout(() => {
        this.showModal= false;
        this.errorMessage= "";
      },  1000);
    }
  },

};
</script>

main.jsimport {defineRule} from "vee-validate"
defineRule('required', () => {
          if(!value || value ===""){
            return "A mező kitöltése kötelező"
        }
        return true
    }
 )
