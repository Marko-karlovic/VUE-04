<template>
    <div class="card">
        <img src="/images/preuzmi.png" alt="John" style="width:100%">
        <h1> {{ userEmail }} </h1>
        <p class="title">Student</p>
        <div style="margin: 24px 0;">
        </div>
        <p><button @click="passwordReset">Change password</button></p>
    </div>
</template>

<script>
    import store from '@/store.js'
    export default {
        data () {
            return store;
        },
        methods: {
            passwordReset () {
                firebase.auth().sendPasswordResetEmail(this.userEmail)
                .then(function() {
                    console.log("Email for password change sent to your email")
                })
                .catch(function(error) {
                    console.log("Error")
                });
            }
        }
    }
</script>

<style>
.card {
  box-shadow: 0 4px 8px 0 rgb(8, 2, 44);
  margin: auto;
  text-align: center;
  font-family: arial;
}
 h1{
     margin-top: 60px;
 }

button {
  border: none;
  outline: 0;
  display: inline-block;
  padding: 8px;
  color: white;
  background-color: rgb(3, 4, 37);
  text-align: center;
  cursor: pointer;
  width: 100%;
  font-size: 18px;
}

a {
  text-decoration: none;
  font-size: 22px;
  color: black;
}

button:hover, a:hover {
  opacity: 0.7;
}
</style>