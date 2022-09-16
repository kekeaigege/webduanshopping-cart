<!--
 * @Author: wangxue 3208230974@qq.com
 * @Date: 2022-09-16 09:54:25
 * @LastEditors: wangxue 3208230974@qq.com
 * @LastEditTime: 2022-09-16 10:29:25
 * @FilePath: \code-shopping-car\src\components\shopCountBtn.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<template>
  <div class="numBtn">
    <div class="cutBtn btn" @click="cutFn">-</div>
    <div class="goodCount">
      <span >{{count}}</span>
    </div>
    <div class="addBtn btn" @click="addFn">+</div>
  </div>
</template>
<script>
import bus from "../EventBus/event";
export default {
  name: "shopCount",
  props: ["goodAccount","goodId"],
  data() {
    return {
      count: this.goodAccount,
      id:this.goodId
    };
  },
  created(){
  },
  methods: {
    cutFn() {
      if (this.count >= 2) {
        this.count = this.count - 1;
        bus.emit("countChange", {goodCount:this.count,goodId:this.id});
      }
    },
    addFn() {
      this.count = this.count + 1;
      bus.emit("countChange", {goodCount:this.count,goodId:this.id});
    },
  },
};
</script>
<style scoped lang="less">
.numBtn {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100%;
  .goodCount {
    width: 40%;
    height: 80%;
    border: 1px solid #ccc;
    border-radius: 5px;
    color: rgb(114, 112, 112);
    line-height: 29px;
  }
  .btn {
    width: 30%;
  }
}
</style>
