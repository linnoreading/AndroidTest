<template>
  <div id="app1">

    <div>
      <!--绑定属性-->
      <div v-text="VueItems.bindProperty.title"></div>
      {{VueItems.bindProperty.h}}
      <div v-text="VueItems.bindProperty.h"></div>
      <div v-html="VueItems.bindProperty.h"></div>

      <img v-bind:src="VueItems.bindProperty.img.imgUrl" v-bind:alt="VueItems.bindProperty.img.alt"
      :title="VueItems.bindProperty.img.alt">

      <div v-bind:title="title">Move On</div>
      <br>

      <!--v-bind:class-->
      <div v-bind:class="{red:flag}">This is a test.</div>
      <div :class="{red:flag,blue:!flag}">This is another test.</div>
      <ul v-for="(item,key) in list1">
          <li :class="{red:key==0}">{{key}}--{{item}}</li>
        </ul>


    </div>

    
    <div>


      <h2>{{msg}}</h2>
      <br>

      <h3>{{obj.name}}</h3>
      <br />
      

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
      <div>

        <div>fengxu Money:</div>
        <input type="button" value="Get FX M" v-on:click="getFXM()" />
        <div>{{money}}</div>
        <input type="text" v-model="money">
        <input type="button" value="Set FX M，不可用" v-on:click="setFXM()">

      </div>

    </div>



  </div>
</template>

<script>
  //import axios from 'axios'

  export default {
    name: "app1",
    data() {
      return {
        flag:false,
        msg: "Welcome!",
        money: 0,
        title: "This is a div title.",
        obj: {
          name: "zhangsan"
        },
        list1: ['item1', 'item2', 'item3'],
        list2: [
          { 'title': 'item11' },
          { 'title': 'item22' },
          { 'title': 'ite33' },
          { 'title': 'item44' },
        ],
        list3: [
          {
            "channel": "电影",
            "type": [
              { 'title': '科幻' },
              { 'title': '恐怖' },
              { 'title': '冒险' },
            ]
          },
          {
            'channel': "电视剧",
            'type': [
              { 'title': '科幻' },
              { 'title': '恐怖' },
              { 'title': '冒险' },
            ]
          },
          {
            'channel': "综艺",
            'type': [
              { 'title': '脱口秀' },
              { 'title': '综艺2' },
              { 'title': '综艺3' },
            ]
          },
        ],
        robot: {

        },
        VueItems: {
          "bindProperty": {
            "title": "绑定属性:v-bind:,v-html,v-text",
            "img": {
              "imgUrl": "src/assets/header_robot.png",
              "alt": "This is Robot."
            },
            "h": "<h4>This is H4.</h4>",
          }
        }

      }
    },
    methods: {
      getFXM() {
        var that = this
        //this.money=222;
        var httpRequest = new XMLHttpRequest();//第一步：建立所需的对象
        httpRequest.open('GET', 'https://raw.githubusercontent.com/linnoreading/AndroidTest/master/MyData/fengxumoney.txt', true);//第二步：打开连接  将请求参数写在url中  ps:"./Ptest.php?name=test&nameone=testone"
        httpRequest.send();//第三步：发送请求  将请求参数写在URL中
        /**
         * 获取数据后的处理程序
         */
        httpRequest.onreadystatechange = function () {
          if (httpRequest.readyState == 4 && httpRequest.status == 200) {
            var json = httpRequest.responseText;//获取到json字符串，还需解析
            console.log(json);
            debugger
            that.money = json;
            //mm.value=json;
          }
        };


      },
      setFXM() {
        //未验证通过，因为GitHub不会允许写的操作。
        var httpRequest = new XMLHttpRequest();//第一步：创建需要的对象
        httpRequest.open('POST', 'https://raw.githubusercontent.com/linnoreading/AndroidTest/master/MyData/fengxumoney.txt', true); //第二步：打开连接
        httpRequest.setRequestHeader("Content-type", "application/x-www-form-urlencoded");//设置请求头 注：post方式必须设置请求头（在建立连接后设置请求头）
        httpRequest.send('name=teswe&ee=ef');//发送请求 将情头体写在send中
        httpRequest.onreadystatechange = function () {//请求后的回调接口，可将请求成功后要执行的程序写在其中
          debugger
          if (httpRequest.readyState == 4 && httpRequest.status == 200) {//验证请求是否发送成功
            var json = httpRequest.responseText;//获取到服务端返回的数据
            console.log(json);
          }
        };
      },
      test01(money) {
        this.axios.get('/api/linnoreading/AndroidTest/master/MyData/fengxumoney.txt', {
          headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
          }
        })
          .then(function (response) {
            //console.log(response);
            console.log(money);
            money = response.data;

            console.log(money);
            //debugger;
            //this.money=response.data;
          });
        console.log("x:" + money);
      },
      changename() {
        this.money = 22;
      }
    },
    // mounted() {
    //     console.log("1111")
    //     console.log(this.axios)
    //   },

  }
</script>

<style>
  .blue{
    color: blue;
  }
  .red{
    color: red;
  }
  
</style>