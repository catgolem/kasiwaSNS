<template>
  <div>
    <div class="title">
      <h2>
        KashiwaSNS!!!
      </h2>
    </div>
    <div>
      
    </div>
    <div>
    </div>

  </div>
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