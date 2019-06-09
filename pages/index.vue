<template>
  <section class="section">
    <div v-if="!isActiveRegister" class="my-content">
      <div class="field">
        <label class="label has-text-white login-label">LOGIN</label>
        <div class="control has-text-centered">
          <input type="text" placeholder="Username" class="custom-input" v-model="usernameLogin"/>
        </div>
        <div class="control has-text-centered">
          <input type="password" placeholder="Password" v-model="passwordLogin" class="custom-input"/>
        </div>
      </div>
      <a class="button is-rounded button-auth" style="border-top-right-radius: 0px; border-bottom-right-radius: 0px;" @click='register()'>Register</a>
      <!-- <nuxt-link to="live-auth"> -->
        <a class="button is-rounded button-auth" style="border-top-left-radius: 0px; border-bottom-left-radius: 0px;" @click="login()">Authenticate</a>
      <!-- </nuxt-link> -->
    </div>
    <div v-else class="my-content">
      <div class="field">
        <label class="label has-text-white login-label">REGISTER</label>
        <div class="control has-text-centered">
          <input type="text" placeholder="Username" class="custom-input" v-model="usernameRegister"/>
        </div>
        <div class="control has-text-centered">
          <input type="password" placeholder="Password" v-model="passwordRegister" class="custom-input"/>
        </div>
      </div>
      <a class="button is-rounded button-auth" style="border-top-right-radius: 0px; border-bottom-right-radius: 0px;">Register</a>
      <a class="button is-rounded button-auth" style="border-top-left-radius: 0px; border-bottom-left-radius: 0px;" >Cancel</a>
    </div>
  </section>
</template>

<script>
  export default {
    layout: 'login',
    data() {
      return {
        isActiveRegister: false,
        usernameLogin: '',
        passwordLogin: '',
        usernameRegister: '',
        passwordRegister: ''
      }
    },
    methods: {
      register() {
        this.isActiveRegister = true;
        this.usernameRegister = '';
        this.passwordRegister = '';
      },
      login() {
        this.isActiveRegister = false;
        // this.$axios.post('/login', {
        //   'username': 'imantoafiif@gmail.com',
        //   'password': 'aderika123'
        // })
        // .then(response => {
        //   console.log(response)
        // })
        this.$axios.post('/login', {
          'username': this.usernameLogin,
          'password': this.passwordLogin
        })
        .then(response => {
          console.log(response)
          if(response.data.data.length == 0) {
            
          }
        })
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');
  .my-content {
    font-family: Roboto, sans-serif;
    border: 2px solid rgba(255, 255, 255, .2);
    border-radius: 50px;
    padding: 50px;
    position: absolute;
    top: 50%;
    left: 50%;
    width: 620px;
    height: 460px;
    margin-left: -310px;
    margin-top: -230px;
    text-align: center;
  }
  .login-label {
    letter-spacing: 5px;
    text-align: center;
    width: 500px;
    padding-bottom: 30px;
    font-size: 40px;
    margin-left: 8px;
  }
  .custom-input {
    -webkit-transition: width .15s ease-in-out;
    transition: width .15s ease-in-out;
    background-color: rgba(0, 0, 0, .2);
    /* border: 1.5px solid #3273DC; */
    border: 1.5px solid #fff;
    border-radius: 50px;
    padding: 20px;
    width: 200px;
    color: #fff;
    text-align: center;
    margin-bottom: 25px;
  }
  .button-auth {
    -webkit-transition: border .15s ease-in-out;
    transition: border .15s ease-in-out;
    margin-top: 10px;
    padding: 25px;
    width: 150px;
    background: rgba(0, 0, 0, .2);
    border: 1.5px solid #686868;
    font-size: 12px;
    color: #fff;
  }
  .button-auth:hover {
    /* border: 1.5px solid #fff; */
    color: #fff;
    background: rgba(0, 0, 0, .4);
  }
  input:hover {
    border: 1.5px solid #3273DC;
    width: 400px;
  }
  input:focus {
    border: 1.5px solid #3273DC;
    width: 400px;
    outline: none;
  }
</style>
