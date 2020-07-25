<template>
<div>
  <section class="form-simple">
    <mdb-row>
      <mdb-col md="5">
        <mdb-card>
          <div class="header pt-3 grey lighten-2">
            <mdb-row class="d-flex justify-content-start">
              <h3 class="deep-grey-text mt-3 mb-4 pb-1 mx-5">Log in</h3>
            </mdb-row>
          </div>
          <form>
          <mdb-card-body class="mx-4 mt-4">
            <mdb-input label="Your email" type="text" v-model="toname" required/>
            <mdb-input label="Your password" type="password" containerClass="mb-0"  v-model="topass" required/>
            <div class="">
             <div v-for="todo of todos"  :key="todo.id" id="hh"> 
           <div v-if="  ((toname==(todo.name))&&(topass==(todo.pass)))">
        
           </div>
        </div>
          <mdb-btn color="danger" id="bt" v-on:click="al">Log in</mdb-btn>
            </div>
           
           
          </mdb-card-body>
           </form>
        </mdb-card>
      </mdb-col>
    </mdb-row>
  </section>
   
       
    
    </div>
</template>
<script>

import axios from 'axios';
  import { mdbRow, mdbCol, mdbCard, mdbCardBody, mdbInput,mdbBtn} from 'mdbvue';
  export default {
    name: 'FormsPage',
    name1: 'ButtonPage',
     name2: 'AlertPage',
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
            toname:'',
            topass:'',
            check:'false',
           
        } 
    },
    async created()
    {
     
      const res =await axios.get('http://localhost:3000/todos');
    this.todos=res.data;
    
    },
    methods:{
        al:function()
        {
            if(this.check==true)
            {
                window.alert("success");
            }
            else{
                window.alert("failed");
            }
        }
    }
}
   
  
</script>
<style>
  .form-simple .font-small {
    font-size: 0.8rem; }

  .form-simple .header {
    border-top-left-radius: .3rem;
    border-top-right-radius: .3rem; }

  .form-simple input[type=text]:focus:not([readonly]) {
    border-bottom: 1px solid #ff3547;
    -webkit-box-shadow: 0 1px 0 0 #ff3547;
    box-shadow: 0 1px 0 0 #ff3547; }

  .form-simple input[type=text]:focus:not([readonly]) + label {
    color: #4f4f4f; }

  .form-simple input[type=password]:focus:not([readonly]) {
    border-bottom: 1px solid #ff3547;
    -webkit-box-shadow: 0 1px 0 0 #ff3547;
    box-shadow: 0 1px 0 0 #ff3547; }

  .form-simple input[type=password]:focus:not([readonly]) + label {
    color: #4f4f4f; }
    .form-simple{
      margin-left: 13cm;
     
    }
    #bt
    {
      width: 6.5cm;
    }
</style>
