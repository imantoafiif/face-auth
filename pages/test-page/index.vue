<template>
  <section class="section">
    <form method='post' @submit.prevent='login()'>
      <input type='text' v-model='username' placeholder='username'></input>
      <input type='password' v-model='password' placeholder='username'></input>
      <button type='submit'>Submit</button>
    </form>
  </section>
</template>

<script>
  export default {
    data() {
      return {
        username: '',
        password: ''
      }
    },
    methods: {
      login() {
        this.$axios.post('/login', {
          username: this.username
        })
        .then(response => {
          console.log(response)
        })
      },
      // login() {
      //   this.$axios.get('/message/afiif')
      //   .then(response => {
      //     console.log(response)
      //   })
      // }
      // login() {
      //   this.$auth.loginWith('local', {
      //     data: {
      //       username: 'imantoafiif@gmail.com'
      //     }
      //   });
      // }
    }
  }
</script>
