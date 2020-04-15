<template>
  <div>
    <label for>
      名字:
      <el-input v-model="name" placeholder="请输入名字" id="name" style="width:250px"></el-input>
    </label>

    <label for>
      地址
      <el-input v-model="adress" placeholder="请输入地址" id="adress" style="width:250px"></el-input>
    </label>
    <label for="">
         <el-button type="success" round @click="btn">添加</el-button>
    </label>

    <el-table :data="tableData" stripe style="width: 100%">
      <el-table-column prop="date" label="日期" width="180">{{data | time()}}</el-table-column>
      <el-table-column prop="name" label="姓名" width="180"></el-table-column>
      <el-table-column prop="adress" label="地址"></el-table-column>
    </el-table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "",
      adress: "",
      data: new Date(),
      tableData: [
        {
          date: new Date(),
          name: "zhy",
          adress: "China"
        },
        {
          date: new Date(),
          name: "czf",
          adress: "China"
        }
      ]
    };
  },
  methods: {
   btn(){
var user = {
    date:this.date,
    name:this.name,
    adress:this.adress
}

this.tableData.push(user)
this.date=this.name=this.adress = ''
      }
  },
  filters: {
    time: function(dateStr, pattren = "") {
      var dt = new Date(dateStr);
      console.log(dateStr);

      //yyyy-mm-dd
      var y = dt.getFullYear();
      var m = (dt.getMonth() + 1).toString().padStart(2, "0");
      var d = dt
        .getDate()
        .toString()
        .padStart(2, "0");

      if (pattren.toLowerCase() === 'yyyy-mm-dd"') {
        return `${y}-${m}-${d}`;
      } else {
        var hh = dt
          .getHours()
          .toString()
          .padStart(2, "0"); //padStart用于进行补零操作
        var mm = dt
          .getMinutes()
          .toString()
          .padStart(2, "0");
        var ss = dt
          .getSeconds()
          .toString()
          .padStart(2, "0");
        return `${y}-${m}-${d}  ${hh}:${mm}:${ss}`;
      }
    }
  }
};
</script>

<style>


</style>