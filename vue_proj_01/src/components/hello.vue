<template>
    <div>
        <h1>{{h1}}</h1>
        <button @click="btn">点击</button>
        <hr>
         <label for="">
            ID
               <input type="text" v-model="id">
        </label>
        <label for="">
            姓名
               <input type="text" v-model="name">
        </label>
        <label for="">
            年纪
                  <input type="text" v-model="age">
        </label>
     
  
        <input type="button" value="添加" @click="btn1">

        <table border="1" id="table">
            <thead>
                 <tr>
                <th>ID</th>
                <th>姓名</th>
                 <th>年龄</th>
            </tr> 
            </thead>

            <tbody>
            <tr v-for="item in list" :key="item.id">
                <td>{{item.id}}</td>
                 <td>{{item.name}}</td>
                  <td>{{item.age}}</td>
            </tr> 
            </tbody>
          
          
        </table>
    </div>
</template>
<script>
export default {
    data(){
        return {
            h1:"哈哈哈",
            name:'',
            age:'',
            id:'',
            list:[
                {
                    id:"1",
                    name:"aaa",
                    age:"18"
                },
                  {
                      id:"2",
                    name:"bbb",
                    age:"20"
                }
            ]
        }
    },
    methods: {
        btn(){
            this.h1 = '孤儿亚索'
        },
        btn1(){
            var user = {
            id:this.id,
            name:this.name,
            age:this.age
            }
            this.list.push(user)
            this.id=this.name=this.age = ''
        
        }
    },
}
</script>

<style>
    #table{
        margin:0 auto
    }
</style>