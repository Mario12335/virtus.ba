<template>
  <div id="app">
    <form  @submit.prevent="post">
       <input v-model="form.name" type="text" name="name" id="name" placeholder="name"> <br>
       <input  v-model="form.email" type="email" name="email" id="email" placeholder="email"> <br>
       <textarea  v-model="form.message" name="message" id="message" cols="30" rows="10"></textarea> <br>
        <input type="submit" class="submit">
    </form>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'App',
  components: {
   
  },
  data(){
    
    return{
      form:{
        name:undefined,
        email:undefined,
        message:undefined
      },
      
    }
  },

  methods: {
    async post()
    {
      console.log(this.form);
      await axios.post('http://localhost:5000/send-email',this.form).then(console.log("Email send")).catch(error => {
        console.log(error);
      })
    }
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
