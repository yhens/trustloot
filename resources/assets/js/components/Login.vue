<template>
    <div>
        <div class="alert alert-danger" v-if="error">
            <p>Error!!!</p>
        </div>
        <form id="form"  @submit.prevent="formSubmit" method="post">
            <div class="form-group">
                <label for="email">E-mail</label>
                <input type="email" id="email" class="form-control" placeholder="user@example.com" v-model="email" required>
            </div>
            <div class="form-group">
                <label for="password">Password</label>
                <input type="password" id="password" class="form-control" v-model="password" required>
            </div>
            <button type="reset" class="btn btn-default formSubmit " >Cancel</button>
            <button type="submit" class="btn btn-default">Acept</button>   
        </form>
    </div>
</template>

<script>
const app= new Vue({
    el:'#form',
    data:{
        email:'',
        password:'',

        submitted:{
            password:'',
            email:''
        }
    }, 
    methods:{
         formSubmit: function(event) {
           this.submitted.password = this.password;
            this.submitted.email = this.email;
      
             this.password = this.email = '';
             
      
        event.target.reset();
    }
  }   
    
});
   
</script>

