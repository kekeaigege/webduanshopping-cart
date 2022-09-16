<!--
 * @Author: wangxue 3208230974@qq.com
 * @Date: 2022-09-15 16:35:26
 * @LastEditors: wangxue 3208230974@qq.com
 * @LastEditTime: 2022-09-16 10:32:18
 * @FilePath: \code-shopping-car\src\components\body.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<template>
  <div class="cart-by-body">
    <ul>
      <li v-for="item in listDate" :key="item.id">
        <div class="picItem">
          <div class="left-check">
            <label class="radio-inline group_allcheck">
              <input type="checkbox" class="inputcheck" v-model="item.check" />
            </label>
          </div>
          <div class="pic">
            <img :src="item.picurl" alt="" />
          </div>
          <div class="right-box">
            <div class="top-title">{{ item.descript }}</div>
            <div class="bottom-bar">
              <div class="price">
                ￥<span>{{ item.price }}</span>
              </div>
              <ShopCount class="ev-num"></ShopCount>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
import ShopCount from "./shopCountBtn.vue";
export default {
  props: {
    listDate: {
      type: Array,
      required: true,
      default: [
        {
          id: 1,
          picurl:
            "http://img14.360buyimg.com/n7/jfs/t1/28128/7/18573/161061/62e14d6cE1e18d640/3cf8ed57a7dabd5a.jpg",
          descript: "女士风衣",
          price: "188",
          count: 1,
          check: true,
        },
      ],
    },
  },
  data() {
    return {};
  },
  components: {
    ShopCount,
  },
};
</script>
<style lang="less">
.picItem {
  margin: 0 auto;
  margin-left: 0;
  margin-right: 0;
  margin-top: 40px;
  width: 95%;
  height: 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  .pic {
    width: 30%;
    height: 100%;
    img {
      max-width: 100%;
      height: 100%;
    }
  }
}
.left-check {
  overflow: hidden;
  width: 10%;
  .inputcheck {
    margin: 0px;
  }
}

.right-box {
  flex: 1;
  height: 100%;
  position: relative;
  overflow: hidden;
  .top-title {
    height: 60px;
    padding: 0 5px;
    text-align: left;
    width: 100%;
    overflow: hidden;
    font-size: 14px;
    word-wrap: break-word;
    font-weight: 600;
  }
  .bottom-bar {
    height: 40px;
    bottom: 0;
    left: 0;
    padding: 0 5px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    .ev-num {
      width: 50%;
    }
    .price {
      color: rgb(230, 43, 43);
      font-weight: 700;
    }
  }
}

.group_allcheck {
  padding-left: 0px !important;
  margin: 0;
}
</style>
