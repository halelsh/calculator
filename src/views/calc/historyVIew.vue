<template>

  <el-card class="box-card history-box">
    <div v-for="h in historyValues" class="text item" @click="historyClicked(h)" >
        <el-card :span="2" shadow="hover" class="cursor">
        {{h.stat}} = {{h.result}}
        </el-card>
    </div>
  </el-card>
</template>

<script>
    export default {
        name: "history-v-iew",
        props:["historyValues"],
        methods:{
          historyClicked(h){
            console.log("historyClicked",h)
            this.$emit('historyClicked',h.stat)
          }
        }
    }

</script>

<style scoped>
  .text {
    font-size: 14px;
  }

  .item {
    padding: 18px 0;
  }

  .box-card {
    width: 480px;
  }
  .history-box{
    overflow-y: scroll;
    height: 150px;
  }
  .cursor{
    cursor: pointer;
  }
</style>
