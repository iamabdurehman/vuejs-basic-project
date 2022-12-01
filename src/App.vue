<template>
  <img :class="gender" v-bind:src="picture" :alt="firstName">
  <h1>{{firstName}} {{lastName}}</h1>
  <h4>Email: {{email}}</h4>
  <button :class="gender" v-on:click="getUser()">Get Random User</button>
</template>
 
<script>
export default {
  name: 'App',
  data(){
    return{
      firstName:'John',
      lastName:'Smith',
      email:'johnSmith@gmail.com',
      gender:'male',
      picture:'https://randomuser.me/api/portraits/men/10.jpg',
    }
  },
  methods:{
    async getUser()
    {
      const res = await fetch('https://randomuser.me/api')
      const {result} = await res.json()

      console.log(result)

      this.firstName=result[0].name.firstName
      this.lastName=result[0].name.lastName
      this.email=result[0].email
      this.gender=result[0].gender
      this.picture=result[0].picture
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
#app{
  width: 400px;
  height: 100vh;
  margin: auto;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
h1{
  margin: 0;
  font-weight: normal;
}
h4{
  margin-top: 0.2rem;
  margin-bottom: 1rem;
  font-weight: normal;
}
img{
  width:100px;
  border-radius: 50%;
  border:5px rgb(158, 158, 158) solid;
  margin-bottom: 0.5rem;
}
.male{
  border-color: rgb(20, 86, 254);
  background-color: rgb(67, 120, 255);
}
.female{
   border-color: rgb(211, 116, 255);
  background-color: rgb(211, 116, 255);
}
body {
  font-family: 'Poppins', sans-serif;
}
button{
  cursor: pointer;
  font-size: 0.9rem;
  border: none;
  width: 10rem;
  height: 2.5rem;
  color: rgb(253, 253, 253);
  border: 1px rgb(158, 158, 158) solid;
}
button:hover{
  border: 1px rgb(158, 158, 158) solid;
  color: white;
  background-color: rgb(158, 158, 158);
}
</style>
