<template>
  <div id="app1">
    <h2>{{msg}}</h2>
    <br>

    <h3>{{obj.name}}</h3>
    <br/>
    <ul v-for="item in list1">
      <li>{{item}}</li>
    </ul>

    <br>
    <ol>
      <li v-for="item in list2">{{item.title}}</li>
    </ol>


    <br>
    <ul>
      <li v-for="ch in list3">
        {{ch.channel}}
        <ol>
          <li v-for="ty in ch.type">{{ty.title}}</li>
        </ol>
      </li>
    </ul>

    <br>
    <input type="button" value="Test" v-on:click="test01(money)" />
    <h3>
      <p>fengxu Money:</p>
      <p>{{money}}</p>
    </h3>
  </div>
</template>

<script>
  //import axios from 'axios'

  export default{
    name:"app1",
    data(){
      return {
        msg:"Welcome!",
        money:0,
        obj:{
          name:"zhangsan"
        },
        list1:['item1','item2','item3'],
        list2:[
          {'title':'item11'},
          {'title':'item22'},
          {'title':'ite33'},
          {'title':'item44'},
        ],
        list3:[
          {
            "channel":"电影",
            "type":[
              {'title':'科幻'},
              {'title':'恐怖'},
              {'title':'冒险'},
            ]
          },
          {
            'channel':"电视剧",
            'type':[
              {'title':'科幻'},
              {'title':'恐怖'},
              {'title':'冒险'},
            ]
          },
          {
            'channel':"综艺",
            'type':[
              {'title':'脱口秀'},
              {'title':'综艺2'},
              {'title':'综艺3'},
            ]
          },
        ],
      }
    },
    methods:{
      test02(){
        this.axios.get("src/main.js")
          .then(function(response){
            alert(response.data);
          })
      },
      test01(money){
        this.axios.get('/api/linnoreading/AndroidTest/master/MyData/fengxumoney.txt',{
            headers:{
              'Content-Type': 'application/x-www-form-urlencoded'
            }
          })
          .then(function(response){
            console.log(response);
            debugger;
            this.money=response.data;
          })
      }
    },
    // mounted() {
    //     console.log("1111")
    //     console.log(this.axios)
    //   },

  }
</script>

<style>

</style>



