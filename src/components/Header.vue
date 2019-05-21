<template>
  <div class="hello">
    <button @click="goToHome">home</button>
    <button @click="goToTest">test</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: () => ({
    msg: 'Welcome to Your Vue.js App'
  }),
  methods: {
    moveRoute: function (path) {
      this.$router.push(`/${path}`)
    },
    goToHome: this.moveRoute(''),
    goToTest: this.moveRoute('test')
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
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
