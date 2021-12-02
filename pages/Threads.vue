<template>
  <div>{{getToken}}</div>
</template>

<script>
export default {
  methods: {
    checkToken(){
      console.log(getToken());
    }
  },
  computed: {
    getToken() {
      return this.$store.state.token;
    },
  }
}
</script>

<style>

</style>