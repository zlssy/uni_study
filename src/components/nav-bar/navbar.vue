<template>
  <view class="th-nav-bar" :class="[extClass]" :style="navBarContainerStyle">
    <view
      class="th-nav-bar-inner f-container"
      :class="[extInnerClass]"
      :style="navBarInnerStyle"
    >
      <view
        class="left f-container f-center"
        :class="{ ios: systemInfo.ios, android: !systemInfo.ios }"
      >
        <view v-if="!$slots.left" class="f-container f-center">
          <view class="iconfont iconfanhui"></view>
        </view>
        <slot v-else name="left" />
      </view>
      <view class="content flex f-center" :class="[extContentClass]">
        <text v-if="title">{{ title }}</text>
        <view v-else-if="searchBar">
          <view class="search-body" :class="[searchBody]">{{
            searchText
          }}</view>
          <icon
            type="search"
            class="search-icon"
            :class="[searchIcon]"
            @tap="handlerSearch"
          />
        </view>
      </view>
      <view class="right" :class="[extRightClass]"><slot name="right"/></view>
    </view>
  </view>
</template>

<script>
export default {
  props: {
    title: String,
    extClass: String,
    navBarContainerStyle: String,
    extInnerClass: String,
    extContentClass: String,
    extRightClass: String,
    navBarInnerStyle: String,
    back: {
      type: Boolean,
      default: false,
    },
    searchText: {
      type: String,
      default: '点击搜索',
    },
  },
  data() {
    return {};
  },
  computed:{
      systemInfo(){
          return {};
      }
  },
  methods: {
    handlerSearch() {
      this.$emit('onSearch');
    },
  }
};
</script>

<style lang="scss">
@import '../../common/common.scss';

.th-nav-bar {
  $nav-bar-full-height: 97rpx;

  .th-nav-bar-inner {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: $nav-bar-full-height;
    padding-top: 20px;
    background-color: $primary;
    color: white;

    .left {
      position: relative;
      width: 120rpx;
    }
    .content {
      position: relative;
      flex: 1;
    }
    .right {
      position: relative;
      width: 100rpx;
    }
  }
}
</style>
