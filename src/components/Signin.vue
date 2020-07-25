<template>
<div>
  <section class="form-elegant  needs-validation">
    <mdb-row>
      <mdb-col md="5">
        <mdb-card>
          <mdb-card-body class="mx-4">
            <div class="text-center">
              <h3 class="dark-grey-text mb-5"><strong>Sign in</strong></h3>
            </div>
            <mdb-input label="Your email" type="text"  v-model="todoName" aria-required="true"/>
            <div v-for="todo of todos"  :key="todo.id" id="hh"> 
           <div v-if=" (todoName==(todo.name))">
             <p> ***Already exist***</p>
           </div>
            </div>
            <mdb-input label="Your password" type="password" containerClass="mb-0" v-model="topass" aria-required="true"/>
            
            <div class="text-center mb-3">
             <mdb-btn type="button" gradient="blue" id ="ss" rounded class="btn-block z-depth-1a" v-on:click="addtodo ">Sign in</mdb-btn>
            </div>
             <p class="font-small grey-text d-flex justify-content-center"> Have an account? <router-link class="dark-grey-text font-weight-bold ml-1" to="login"> Login</router-link></p>
          </mdb-card-body>
        </mdb-card>
      </mdb-col>
    </mdb-row>
  </section>
  
</div>
</template>

<script>

import axios from 'axios';
  import { mdbRow, mdbCol, mdbCard, mdbCardBody, mdbInput, mdbBtn,  } from 'mdbvue';
  export default {
    name: 'FormsPage',
    components: {
      mdbRow,
      mdbCol,
      mdbCard,
      mdbCardBody,
      mdbInput,
      mdbBtn,
     
    },
    data(){
        return{
            todos:[],
            todoName:'',
            topass:''
        } 

    },
   methods:{
  async  addtodo(){
      const res=await axios.post('http://localhost:3000/todos',{name:this.todoName,pass:this.topass});
      this.todos=[...this.todos,res.data]; 
      this.todoName='';
      this.topass='';
    }
  },
   async created()
    {
     
      const res =await axios.get('http://localhost:3000/todos');
    this.todos=res.data;
    
    }

  }

</script>
<style>
 .form-elegant
 {
   margin-left: 13cm;
  
 }
 #ss
 {
   
   margin-top: 2cm;
 }
</style>