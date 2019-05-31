<template>
  <div>
    <el-row :gutter="20">
      <el-col :span="6">
        <el-input v-model="name" @change="getName" placeholder="请输入姓名" maxlength="15" type="text"></el-input>
      </el-col>
      <el-col :span="6">
        <el-input
          v-model="age"
          @change="getAge"
          placeholder="请输入年龄"
          maxlength="3"
          type="text"
          value="number"
        ></el-input>
      </el-col>
      <el-col :span="6">
        <el-input v-model="address" @change="getAddress" placeholder="请输入地址" maxlength="15"></el-input>
      </el-col>
      <el-col :span="6">
        <el-button type="success" @click="addContent">添加</el-button>
      </el-col>
    </el-row>

    <el-table :data="list_data" style="width: 100%">
      <el-table-column
        v-for="{prop , label} in text_Array"
        :key="prop"
        :label="label"
        :prop="prop"
        width="200"
      ></el-table-column>
      <el-table-column label="操作">
        <template scope="scope">
          <el-button size="small" @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
          <el-button size="small" type="warning" @click="handleDelete(scope.$index, scope.row)">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    this.text_Array = [
      { prop: "image", label: "头像" },
      { prop: "name", label: "姓名" },
      { prop: "age", label: "年龄" },
      { prop: "address", label: "地址" }
    ];
    return {
      name: "",
      age: "",
      address: "",
      list_data: [
        { image: "不会弄", name: "马冬梅", age: "32", address: "中南海" },
        { image: "不会弄", name: "马日天", age: "22", address: "地中海" },
        { image: "不会弄", name: "马日地", age: "16", address: "洱海" },
        { image: "不会弄", name: "马日鬼", age: "19", address: "玄海" },
        { image: "不会弄", name: "马日蛇", age: "31", address: "沧海" }
      ]
    };
  },
  methods: {
    // 获取名字
    getName(e) {
      console.info(e);
      this.name = e;
    },
    //获取年龄
    getAge(e) {
      console.info(e);
      this.age = e;
    },
    //获取地址
    getAddress(e) {
      console.info(e);
      this.address = e;
    },
    addContent() {
      if (!this.name && !this.age && !this.address) {
        alert("完善内容在提交");
        return;
      }
      let item = {
        image: "不会弄",
        name: this.name,
        age: this.age,
        address: this.address
      };
      this.list_data.push(item);
      this.name = "";
      this.age = "";
      this.address = "";
    },
    handleEdit(index, row) {
      console.log(index, row);
    },
    handleDelete(index, row) {
      this.list_data.splice(index, 1);
    }
  }
};
</script>
    
<style scoped>
.row {
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-around;
}
</style>
