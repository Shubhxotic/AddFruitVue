<template>
  <div class="hello">
      <p>{{msg}}</p>
      <h1 v-if="something"> Shubham </h1>
      <h1 v-else>Bum</h1>

      <p v-text="user.number"></p>
      <div v-for = "fruit in fruits" class="b0b w-25 mx-auto my-2"><p>{{fruit.fruit}}</p></div>
      <button v-on:click="sayhello('hello world')" class="button is-primary m-3">Say Hello</button><br>
      <input type="text" class="" name="inp" id="inp" v-on:keyup="keyfunc" v-on:keyup.enter="enterpressed"  v-on:keyup.alt="altpressed" >
      <hr>
      <input type="text" class="" v-model="user.name">
      <input type="text" class="" v-model="user.number">
      <p>{{namenum}}</p>
      <p>{{mesg}}</p>
      <br>
      <a href="/"><button class="button is-link"> Go to home Page</button></a>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    mesg: {
      type: String,
      default: "some msg"
    }
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      user: {
        name: "Name",
        number: 12371390123
      },
      active: true,
      something: []+{},
      fruits: [
        {fruit : "apple"},
        {fruit : "orange"},
        {fruit : "guava"}
      ]
    }
  },
  methods: {
    sayhello: function(x){
      alert(x);
    },
    keyfunc: function(e){
      console.log(e.target.value);
    },
    enterpressed: function(){
      alert("Enter Pressed");
    },
    altpressed: function(){
      console.log("alt Pressed");
    },
  },
  computed: {
    namenum: function(){
      return this.user.name+"'s Phone number is  "+this.user.number;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.b0b{
  border: 1px solid black;
}
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
