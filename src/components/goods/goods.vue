<template>
    <div class="good">
      <div class="menu-wrapper">
        <ul>
          <li v-for="(item, index) in goods" class="menu-item border-1px" :class="{'current':currentIndex === index}">
            <span class="text">
              <span v-show="item.type>0" class="icon" :class="classMap[item.type]"></span>
              {{item.name}}
            </span>
          </li>
        </ul>
      </div>
      <div class="foods-wrapper">
        <ul>
          <li v-for="item in goods" class="food-list food-list-hook">
            <h1 class="title">{{item.name}}</h1>
            <ul>
              <li v-for="food in item.foods" class="food-item">
                <div class="icon">
                  <img :src="food.icon" alt="" width="57">
                </div>
                <div class="content">
                  <h2 class="name">{{food.name}}</h2>
                  <p class="desc">{{food.description}}</p>
                  <div class="extra">
                    <span class="count">月售{{food.sellCount}}</span><span class="count">好评{{food.rating}}</span>
                  </div>
                  <div class="price">
                    <span class="now">¥{{food.price}}</span>
                    <span class="old" v-show="food.oldPrice">¥{{food.oldPrice}}</span>
                  </div>
                </div>
              </li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
</template>
<script type="text/ecmascript-6">
  import BScroll from 'better-scroll';
  import data from 'common/json/data.json';
//  const ERR_OK = 0;

  export default {
    props: {
      seller: {
        type: Object
      }
    },
    data() {
      return {
        goods: [],
        listHeight: []
      };
    },
    created() {
//      this.$http.get('/api/goods').then((response) => {
//        response = response.body;
//        if (response.errno === ERR_OK) {
//         this.goods = response.data;
//       this.$nextTick(() => {
//        this._initScroll();
//        this._calculateHeight();
//       });
//        }
//      });
      this.goods = data.goods;
      console.log(this.goonds);
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
    },
    methods: {
      _initScroll() {
        this.menuScroll = new BScroll(this.$refs.menuWrapper, {
          click: true
        });
      },
      selectMenu(index, event) {
//        if (!event._constructed){
//          // 去掉自带click事件的点击
//          return;
//        }
//        let el = foodList[index];
      }
    },
    computed: {
      currentIndex() {
//        for (let i = 0; i < this.listHeight.length; i++) {
//          let height = this.listHeight[i];
//          let height2 = this.listHeight[i + 1];
//
//        }
        return 0;
      }
    }
  };
</script>
<style scoped rel="stylesheet/stylus" lang="stylus">
  @import "goods.styl";
</style>
