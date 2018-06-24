<template>
  <div class="fruit">
      <h1 class="has-text-danger">Fruits<i class="fab fa-apple"></i> </h1>
      <h4 class="has-text-success">I don't like em though</h4><br>
      <h3>Add New Fruit</h3>
      <div class="px-auto w-100 ">
      <form v-on:submit="addfruit" class="container w-50 mx-auto my-5 " style="background: #eee;">
      <input class= "input" type="text" name="fruit"  id="fruit" v-model="newfruit.fruit" placeholder="fruit">
      <input class= "input" type="number" name="price"  id="price" v-model="newfruit.price" placeholder="price">
      <input class= "input" type="text" name="color"  id="color" v-model="newfruit.color" placeholder="color"><br>
      <br>isRotten?<input type="checkbox" name="isRotten"  id="isRotten" v-model="newfruit.isRotten" ><br><br>
      <input type="submit" value="Add new Fruit" class="button is-primary">
      </form>
      </div>
      <br><br>
      <ul>
        <li v-for="fruit in fruits" class="row b0b px-auto" style="width: 45%;">
          
          <span :class="{rotten: fruit.isRotten}" class="col-8" style="display: inline;">{{fruit.fruit}} costing  {{fruit.price}} is {{fruit.color}} is </span>
          <span class="col-2 columns mx-auto my-0" style="vertical-align: middle;">
            <p v-if="fruit.isRotten" :class="{rotten: fruit.isRotten}">Rotten</p>
            <p v-else class="">Fresh</p>
            <input type="checkbox" class="toggle my-auto py-auto" v-model="fruit.isRotten">
          </span>
          <button class="col-1 button is-danger" v-on:click="deleteFruit(fruit)">x</button>
          <br>
        </li>
      </ul>
      <a href="/test"><button class="button is-info my-5"> Go to Test Page</button></a>
  </div>
</template>

<script>
export default {
  name: 'Fruit',
  props: {
    mesg: {
      type: String,
      default: "some msg"
    }
  },
  data () {
    return {
      newfruit : {},
      msg: 'Welcome to Your Vue.js App',
      user: {
        name: "Shubas",
        number: 12371390123
      },
      active: true,
      something: []+{},
      fruits: [
        {fruit : "apple", price: 35, color: "red" , isRotten: false},
        {fruit : "orange", price: 45, color: "orange" , isRotten: false},
        {fruit : "guava", price: 65, color: "green" , isRotten: false}
      ]
    }
  },
  methods: {
    addfruit: function(e){
      console.log(JSON.stringify(this.newfruit));
      this.fruits.push(this.newfruit);
      this.newfruit = {};
      e.preventDefault();
    },
    deleteFruit: function(fruit){
      this.fruits.splice(this.fruits.indexOf(fruit),1);
    },
    sayhello: function(x){
      console.log(x);
    },
    keyfunc: function(e){
      console.log(e.target.value);
    },
    enterpressed: function(){
      console.log("Enter Pressed");
    },
    altpressed: function(){
      console.log("alt Pressed");
    },
  },
  computed: {
    namenum: function(){
      return this.user.name+" "+this.user.number;
    }
  },
  created: function(){
    // confirm("eho");
    this.$http.get("https://api.myjson.com/bins/ii6sm").then(function(response){
      this.fruits = response.data;
    })
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
*{
  margin: 5px;
  padding: 5px;
}
.rotten{
  text-decoration: line-through;
}
</style>
