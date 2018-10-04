<template>
  <div class="app-container">
    <el-row type="flex" justify="center" :gutter="20">
      <el-col :xs="20" :lg="4" >
        <el-input placeholder="Please input" v-model="input"></el-input>
      </el-col>
    </el-row>
    <el-row type="flex" justify="center" :gutter="20">
      <el-col :xs="20" :lg="4" >
        <el-alert v-if="showError"
          title="error alert"
          type="error">
        </el-alert>
      </el-col>
    </el-row>
    <el-row :gutter="20" type="flex" justify="center">
      <el-col  :xs="25" :sm="12" :md="20" :lg="20" >
          <el-row  type="flex" justify="center">
            <el-button type="primary" @click="btnPressed(1)" round>1</el-button>
            <el-button type="primary" @click="btnPressed(2)" round>2</el-button>
            <el-button type="primary" @click="btnPressed(3)" round>3</el-button>
            <el-button type="warning" @click="btnPressed('*')" round>*</el-button>

          </el-row>
          <el-row  type="flex" justify="center">
            <el-button type="primary" @click="btnPressed(4)" round>4</el-button>
            <el-button type="primary" @click="btnPressed(5)" round>5</el-button>
            <el-button type="primary" @click="btnPressed(6)" round>6</el-button>
            <el-button type="warning" @click="btnPressed('/')" round>/</el-button>
          </el-row>
          <el-row  type="flex" justify="center">
            <el-button type="primary" @click="btnPressed(7)" round>7</el-button>
            <el-button type="primary" @click="btnPressed(8)" round>8</el-button>
            <el-button type="primary" @click="btnPressed(9)" round>9</el-button>
            <el-button type="warning" @click="btnPressed('-')" round>-</el-button>
          </el-row>
        <el-row  type="flex" justify="center">
          <el-button type="danger" @click="clear()" round>C</el-button>
          <el-button type="primary" @click="btnPressed(0)" round>0</el-button>
          <el-button type="info" @click="getSum()"  round>=</el-button>
          <el-button type="warning" @click="btnPressed('+')" round>+</el-button>

        </el-row>
      </el-col>
    </el-row>
    <el-row type="flex" justify="center">
      <el-badge :value="history.length" class="item">
        <el-button @click="showHistory=!showHistory">calculation history</el-button>
      </el-badge>
    </el-row>
      <el-row type="flex" justify="center">
        <transition name="fade">
            <historyView v-if="showHistory" @historyClicked="historyClicked" @ke :historyValues="history"></historyView>
        </transition>
    </el-row>
  </div>
</template>

<script>
import historyView from "./historyVIew"
export default {
  components:{
    historyView
  },
  data() {
    return {
      input:"",
      showError : false,
      history:[],
      showHistory:false
    }
  },
  methods: {
    btnPressed(val) {
      this.input+=val;
    },
    clear(){
      this.input = "";
    },
    getSum(){
      try{
        var result =  eval(this.input);
      }
      catch(err){
          this.showError = true;
      }
      finally {
        if (result){
          console.log(result)
          this.showError = false;
          this.history.push({stat:this.input,result})
          this.input = result;

        }
      }
    },
    historyClicked(val){
      this.input = val;

    }
  }
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

