<template>
  <div>
    <!-- 头部 -->
    <v-header :seller="seller"></v-header>
    <div class="tab">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script type="text/ecmascript-6">
  import header from 'components/header/header.vue';
  import data from 'common/json/data.json';
//  这边webpack.base.conf.js中配置过了，components相当于'../src/components'
//  import data from './common/json/data.json';

  export default {
    data() {
      return {
        seller: {}
      };
    },
    created() {
//      this.$http.get('/api/seller?id=' + this.seller.id).then((response) => {
//        response = response.body;
//        if (response.errno === ERR_OK) {
//          this.seller = response.data;
//          this.seller = Object.assign({}, this.seller, response.data);
//        }
//      });
      this.seller = data.seller;
//      console.log(data);
    },
    components: {
      'v-header': header
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "common/stylus/mixin.styl";
  .tab {
    display flex
    width 100%
    height 40px
    line-height 40px
    border-1px(rgba(7, 17, 27, .1))
    .tab-item {
      flex 1
      text-align center
      & > a {
        display block
        font-size 14px
        color rgb(77, 85, 93)
        &.active {
          color rgb(240, 20, 30)
        }
      }
    }
  }

</style>
