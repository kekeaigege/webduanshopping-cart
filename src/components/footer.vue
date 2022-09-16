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
            />
            全选
          </label>
        </li>
        <li>
          合计:
          <span class="redcolor">￥232.00</span>
        </li>
        <li>
          <button
            type="button"
            class="btn btn-primary resetbtn"
            @clink="submitPrice(totalPrice)"
          >
            结算(<span>{{ totalPrice }}</span
            >)
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  props: {},
  data() {
    return {
      totalPrice: 55,
      check: false,
    };
  },
  methods: {
    submitPrice(totalPrice) {
      console.log(totalPrice);
    },
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
  background: orange;
  border: none;
  height: 35px;
  border-radius: 19px;
  font-size: 12px;
}
</style>
