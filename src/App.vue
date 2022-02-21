<template>
  <div id="app">
    <img 
    :class="gender"
    :src="picture" 
    :alt="`${firstName} ${lastname}`"
    />
    <h1>{{firstName}} {{lastName}}</h1>
    <h3 :class="gender" >Email:{{email}}</h3>
    <button :class="gender" v-on:click="getUser()" >Get Rondom User</button>
  </div>
</template>

<script>
export default {
data(){
  return{
    firstName:'John',
    lastName:'Doe',
    email:'john@gmail.com',
    gender:'male',
    picture: 'https://randomuser.me/api/portraits/men/10.jpg',
  }
},
methods:{
   async getUser(){
     const res = await fetch('https://randomuser.me/api')
     const {results} = await res.json()
     console.log('ok')

     this.firstName = results[0].name.first
     this.lastName = results[0].name.last
     this.email = results[0].email
     this.gender = results[0].gender
     this.picture = results[0].picture.large
  },
},

}
</script>

<style>
*{
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
html,body{
  font-family: sans-serif;
  margin-top: 5%;
  background:rgb(148, 124, 3);
}
#app{
  width: 500px;
  height: 100vh;
  margin: auto;
  border: 1px solid black;
  text-align: center;
  /* display: flex; */
  justify-content: center;
  padding-top: 5%;
  background: rgb(148, 124, 3);
  align-items: center;
  flex-wrap: wrap;
  margin-bottom: 50px;
  border-radius: 20px;
  box-shadow: 0 0 10px 5px #333;
}
h1,h3{
  margin-bottom: 1rem;
  font-weight: normal;
  display: block;
  padding: 10px;
  font-weight: bold;
}
img{
 border-radius: 50%;
  border: 5px  solid #333;
  margin-bottom: 1rem;
  box-shadow:0 0 10px 6px #333;
}
.male{
  border-color: teal;
  background: teal;
  color: white;
}
.female{
  border-color: crimson;
  background: crimson;
  color: white;
}
button{
  margin-top: 150px;
  cursor: pointer;
  display: inline-block;
  background: #333;
  color: white;
  border-radius: 6px;
  font-size: 18px;
  border:none;
  outline: none;
  padding: 1rem 1.5rem;
}
</style>