<template>
  
  <section id="content">
      <h2 class="subheader">{{ titulo }}</h2>
      <h1>{{ texto }}</h1>
      <h2>{{ texto }}</h2>
  </section>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      titulo: 'HelloWorld',
      texto: "Componente corriendo!"
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
