<!--
 * @Author: wangxue 3208230974@qq.com
 * @Date: 2022-09-15 16:26:48
 * @LastEditors: wangxue 3208230974@qq.com
 * @LastEditTime: 2022-09-15 17:12:59
 * @FilePath: \code-shopping-car\src\App.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<template>
  <div id="mater container">
    <Head></Head>
    <BodyShop :listDate="listDate"></BodyShop>
    <FootShop
      @delGoodlist="delList"
      @updataAlllist="updataAlllist"
      :totalAmount="totalprice"
      :goodCount="goodNum"
    ></FootShop>
  </div>
</template>

<script>
import Head from "./components/header.vue";
import BodyShop from "./components/body.vue";
import FootShop from "./components/footer.vue";
import bus from "./EventBus/event";
export default {
  name: "App",
  components: {
    Head,
    BodyShop,
    FootShop,
  },
  data() {
    return {
      totalprice: 0,
      goodNum: 0,
      listDate: [
        {
          id: 1,
          picurl:
            "http://img14.360buyimg.com/n7/jfs/t1/28128/7/18573/161061/62e14d6cE1e18d640/3cf8ed57a7dabd5a.jpg",
          descript: "女士风衣",
          price: 188,
          count: 1,
          check: true,
        },
        {
          id: 2,
          picurl:
            "http://img12.360buyimg.com/n2/jfs/t1/29308/30/19373/53535/6308aebdE40f8ccb3/0b7c29e0e1623fdb.jpg",
          descript: "女士冲锋衣",
          price: 288,
          count: 2,
          check: false,
        },
      ],
    };
  },
  created() {
    bus.on("countChange", (map) => {
      this.listDate.forEach((v) => {
        if (v.id == map.goodId) {
          this.listDate[v.id-1].count = map.goodCount;
        }
      });
    });
  },
  methods: {
    //全选功能
    updataAlllist(check) {
      this.listDate.forEach((v) => (v.check = !check));
    },
    delList() {
      this.listDate.forEach((v) => {
        // if (v.check) {
        //    this.listDate = this.listDate.splice(v.id-1,1);
        //   console.log(v.id);
        // }
      });
    },
  },
  computed: {
    totalprice() {
      var total = 0;
      this.listDate.forEach((v) => {
        if (v.check) {
          total = v.price * v.count + total;
        }
      });
      return total;
    },
    goodNum() {
      var total = 0;
      this.listDate.forEach((v) => {
        if (v.check) {
          total = total + 1;
        }
      });
      this.goodNum = total;
      return total;
    },
  },
};
</script>
<style lang="less" scoped>
#mater {
  height: 500px;
}
</style>
