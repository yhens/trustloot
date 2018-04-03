<template>
    <div>
        <div class="alert alert-danger" v-if="error && !success">
            <p>Error, al registar.</p>
        </div>
        <div class="alert alert-success" v-if="success">
            <p>Registro Exitoso<router-link :to="{name:'login'}">sign in.</router-link></p>
        </div>
        <form id="form" autocomplete="off" @submit.prevent="formSubmit " v-if="!success" method="post">

            <div class="form-group" v-bind:class="{ 'has-error': error && errors.name }">
                <label for="name">Name</label>
                <input type="text" id="name" class="form-control" v-model="name" required>
                <span class="help-block" v-if="error && errors.name">{{ errors.name }}</span>
            </div>

            <div class="form-group" v-bind:class="{ 'has-error': error && errors.email }">
                <label for="email">E-mail</label>
                <input type="email" id="email" class="form-control" placeholder="user@example.com" v-model="email" required>
                <span class="help-block" v-if="error && errors.email">{{ errors.email }}</span>
            </div>
            
            <div class="form-group" v-bind:class="{ 'has-error': error && errors.password }">
                <label for="password">Password</label>
                <input type="password" id="password" class="form-control" v-model="password" required>
                <span class="help-block" v-if="error && errors.password">{{ errors.password }}</span>
            </div>
           
            <button type="reset" class="btn btn-default formSubmit ">Cancel</button>
             <button type="submit" class="btn btn-default">Acept</button>
        </form>
    </div>
</template>

<script>
    const app=new Vue({
        el:'#form',
        date:{
            name:'',
            email:'',
            password:'',
            
            submitted:{
                name:'',
                email:'',
                password:''
            }
        },
        methods:{
            formSubmit:function(event){
                this.submitted.name=this.name;
                this.submitted.email=this.email;
                this.submitted.password=this.password;

                this.name='';
                this.email='';
                this.password='';

                event.target.reset();
            }
        }
    });
</script>
