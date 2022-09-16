<!--
 * @Author: wangxue 3208230974@qq.com
 * @Date: 2022-09-15 16:35:16
 * @LastEditors: wangxue 3208230974@qq.com
 * @LastEditTime: 2022-09-15 17:57:14
 * @FilePath: \code-shopping-car\src\components\header.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<template>
  <div
    :style="{ backgroundColor: bgcolor, color: color, fontSize: fsize + 'px' }"
    class="header_container"
  >
    <span>{{ title }}</span
    ><button
      v-if="openManage"
      type="button"
      class="btn btn-warning manage"
      @click="manageBtnFn"
    >
      完成
    </button>
    <button
      v-else
      type="button"
      class="btn btn-warning manage"
      @click="manageBtnFn"
    >
      管理
    </button>
  </div>
</template>
<script>
import bus from "../EventBus/event";
export default {
  data() {
    return {
      openManage: false,
    };
  },
  methods: {
    manageBtnFn() {
      this.openManage = !this.openManage;
      bus.emit("changeManageBtn", this.openManage);
    },
  },
  props: {
    title: {
      type: String,
      default: "购物车",
    },
    color: {
      type: String,
      default: "white",
    },
    bgcolor: {
      type: String,
      default: "#f1bb55",
    },
    fsize: {
      type: Number,
      default: "12",
    },
  },
};
</script>
<style lang="less" scoped>
.header_container {
  position: fixed;
  z-index: 999;
  top: 0;
  left: 0;
  width: 100%;
  height: 40px;
  text-align: center;
  line-height: 40px;
  .manage {
    position: absolute;
    margin-right: 7px;
    margin-top: 7px;
    right: 0;
    height: 26px;
    border: none;
    border-radius: 20px;
    font-size: 12px;
    background-color: #f1bb55;
    &:hover {
      background-color: #ec971f;
    }
  }
}
</style>
