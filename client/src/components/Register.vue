<template>
  <div class="hello">
    <h1>Register</h1>
    <input
          type='email'
          text='email'
          v-model='email'
          placeholder='email' />
    <br>
    <input
          type='password'
          text='password'
          v-model='password'
          placeholder='password' />
    <br>
    <div class='error' v-html='error' />
    <br>
    <button
      @click='register'>
      Register
    </button>

  </div>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register () {
      try {
        var response = await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
        console.log(response.data)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  color:red;
}
</style>
