<template>
  <div>
    <form @submit.prevent>
      <input class="border-2 block" type="text" v-model="user.name">
      <input class="border-2 block" type="text" v-model="user.email"> 
      <input class="border-2 block" type="text" v-model="user.password"> 
      <input class="border-2 block" type="text" v-model="user.description"> 
      <button class="border-2 block" type="submit" @click="postuser">
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
        name: '',
        email:'',
        password:'',
        description:'',		
      }
    }
  },
  methods: {
    async postuser(){
      try {
        const response = await axios.post('/api/v1/auth/signup',this.user);
        console.log(response);
      } catch (error) {
        console.error(error);
        console.error("SignUpでエラーが発生しました。");
        return;
      }
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
