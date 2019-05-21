<template>
  <div class="test">
    <h1>{{ msg }}</h1>
    <h2>test one two one two</h2>
    <button v-on:click="goToHome">go to home</button>
  </div>
</template>

<script>
export default {
  name: 'Test',
  data () {
    return {
      msg: 'this is test page'
    }
  },
  methods: {
    goToHome: function () {
      fetch('https://koreanjson.com/users').then((res) => {
        console.log(this)
      })
      this.$router.push('/')
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
