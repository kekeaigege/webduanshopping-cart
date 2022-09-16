<!--
 * @Author: wangxue 3208230974@qq.com
 * @Date: 2022-09-15 16:35:16
 * @LastEditors: wangxue 3208230974@qq.com
 * @LastEditTime: 2022-09-15 17:56:45
 * @FilePath: \code-shopping-car\src\components\header.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<template>
  <div class="foot_container">
    <div class="box">
      <ul>
        <li>
          <label class="radio-inline group_allcheck">
            <input
              type="checkbox"
              value="全选"
              v-model="check"
              class="inputcheck"
              @click="allCheck"
            />
            全选
          </label>
        </li>
        <li v-show="!controlDel">
          合计:
          <span class="redcolor">￥{{ totalAmount }}</span>
        </li>
        <li v-show="controlDel">
          <button type="button" class="btn btn-warning delBtn" @click="delFn">删除</button>
        </li>
        <li v-show="!controlDel">
          <button
            type="button"
            class="btn btn-primary resetbtn"
            @click="submitPrice"
          >
            结算(<span>{{ goodCount }}</span
            >)
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
import bus from "../EventBus/event";
export default {
  props: ["totalAmount", "goodCount"],
  data() {
    return {
      check: false,
      controlDel: false,
    };
  },
  created() {
    bus.on("changeManageBtn", (v) => {
      this.controlDel = v;
    });
  },
  emits: ["updataAlllist"],
  methods: {
    submitPrice() {
      console.log(this.totalAmount);
      if (this.totalAmount == 0 || this.totalAmount == "") {
        alert("请选择商品");
      } else {
        alert("当前支付金额为" + this.totalAmount);
      }
    },
    //全选功能实现
    //修改父元素中的list值
    allCheck() {
      console.log(this.check);
      this.$emit("updataAlllist", this.check);
    },
    delFn(){
       this.$emit("delGoodlist");
    }
  },
};
</script>
<style lang="less" scoped>
.foot_container {
  background-color: #fff;
  z-index: 999;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 50px;
  text-align: center;
  line-height: 50px;
  border-top: 1px solid #ccc;
}
.box {
  margin: 0 auto;
  width: 95%;
  font-size: 13px;
  ul {
    padding: 0;
    margin: 0;
    display: flex;
    justify-content: space-between;
    li {
      float: left;
      height: 50px;
    }
    .delBtn {
      width: 100px;
    }
  }
}

.group_allcheck {
  display: flex;
  justify-content: space-between;
  align-items: center;
  .inputcheck {
    margin: 0px;
    margin-right: 4px;
  }
}
.redcolor {
  color: rgb(241, 123, 12);
  font-weight: 700;
}
.resetbtn {
  background: #f0ad4e;
  border: none;
  height: 35px;
  border-radius: 19px;
  font-size: 12px;
}
</style>
