<template>
  <div>
    <form @submit.prevent>
      <input class="border-2 block" type="text" v-model="user.email"> 
      <input class="border-2 block" type="text" v-model="user.password"> 
      <button class="border-2 block" type="submit" @click="signIn">
        送信
      </button>
    </form>
  </div>
</template>

<script>
import axios from "~/plugin/axios.js";


export default {
  setup() {
  },
  data(){
    return {
      user: {
        email:'',
        password:'',
      }
    }
  },
  methods: {
    async signIn(){
      try {
        const response_signin = await axios.post('/api/v1/auth/signin',{
          email:this.user.email,
          password:this.user.password
          });
        console.log(response_signin);
        this.$store.commit("setIsLogin", true);
        this.$store.commit("setToken", response_signin.data.jwt);
        this.$router.push('/Threads');
      } catch (error) {
        console.error(error);
        console.error("SignInでエラーが発生しました。");
        return;
      }
    },
  }
}
</script>