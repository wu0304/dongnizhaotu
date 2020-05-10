<template>
  <view class="video_category">
    <view class="video_item" v-for="item in category" :key="item.id">
      <image mode="aspectFill" :src="item.cover"></image>
      <view class="video_name">{{item.name}}</view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      category: []
    };
  },
  props: {
    urlobj: Object
  },
  mounted() {
    // console.log(this.urlobj);
    this.getList();
  },
  methods: {
    getList() {
      this.request({
        url: this.urlobj.url
      }).then(result => {
        // console.log(result);
        this.category = result.res.category
      });
    }
  }
};
</script>

<style lang="scss" scoped>
.video_category{
  display: flex;
  flex-wrap: wrap;
  .video_item{
    width: 50%;
    position: relative;
    border: 5rpx solid #fff;
    image{
      height: 240rpx;
    }
    .video_name{
      position: absolute;
      width: 100%;
      height: 50rpx;
      left: 0;
      bottom: 0;
      color: #fff;
      // css3 渐变
      background-image: linear-gradient(to right top,rgba(0,0,0,.2),rgba(0,0,0,0));
      font-size: 40rpx;
      display: flex;
      align-items: center;
      padding-left: 20rpx;
    }
  }
}
</style>