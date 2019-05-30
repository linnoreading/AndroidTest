<template>
  <div id="app">
    <input type="button" value="Click" v-on:click="test01()"/>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  methods: {
    test01(){
        axios.get('/api/linnoreading/AndroidTest/master/MyData/fengxumoney.txt',{
            headers:{
              'Content-Type': 'application/x-www-form-urlencoded'
            }
          })
          .then(function(response){
            console.log(response);
          })
      }
  },
}
</script>
