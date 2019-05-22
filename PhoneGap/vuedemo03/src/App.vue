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
  </div>
</template>

<script>
  export default{
    name:"app1",
    data(){
      return {
        msg:"Welcome!",
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
    }
  }
</script>

<style>

</style>
