<template>
  <div class="app-container">
    <el-row type="flex" justify="center" :gutter="20">
      <el-col :xs="20" :lg="4" >
         Adiel Shalit - Fullstack developer
     </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  components:{
  },
  data() {
    return {
    }
  },
  methods: {
    },
}
</script>

<style scoped>
.line{
  text-align: center;
}
.el-row {
  margin-bottom: 20px;
&:last-child {
   margin-bottom: 0;
 }
}
.el-col {
  border-radius: 4px;
}
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
}
.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
</style>

