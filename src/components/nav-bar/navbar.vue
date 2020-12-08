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
        <view
          class="search-container flex f-center"
          v-if="searchBar"
          @tap="handlerSearch"
        >
          <view class="search-body" :class="[searchBody]">{{
            searchText
          }}</view>
          <icon
            type="search"
            class="search-icon"
            size="16"
            :class="[searchIcon]"
          />
        </view>
        <text class="main-title" v-else>{{ title }}</text>
      </view>
      <view class="right flex f-center" :class="[extRightClass]"
        ><slot name="right" />
      </view>
    </view>
  </view>
</template>

<script>
export default {
  props: {
    title: { type: String, default: '腾讯医疗' },
    extClass: String,
    navBarContainerStyle: String,
    extInnerClass: String,
    extContentClass: String,
    extRightClass: String,
    navBarInnerStyle: String,
    searchBody:String,
    searchIcon:String,
    back: {
      type: Boolean,
      default: false,
    },
    searchText: {
      type: String,
      default: '点击搜索',
    },
    searchBar: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {};
  },
  computed: {
    systemInfo() {
      return {};
    },
  },
  methods: {
    handlerSearch() {
      this.$emit('search');
    },
  },
};
</script>

<style lang="scss">
@import '../../common/common.scss';

.th-nav-bar {

  .th-nav-bar-inner {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: $navBarFullHeight;
    padding-top: $statusBarHeight;
    background-color: $primary;
    color: white;
    z-index: 5001;

    .left {
      position: relative;
      width: 120rpx;
    }
    .content {
      position: relative;
      flex: 1;
      justify-content: flex-start;

      .search-container {
        width: 80%;

        .search-body {
          width: 100%;
          height: 48rpx;
          line-height: 48rpx;
          border-radius: 24rpx;
          background-color: white;
          color: #666666;
          text-align: center;
          font-size: 12px;
        }

        .search-icon {
          width: 24px;
          position: relative;
          right: 24px;
        }
      }
      .main-title{
          width: 100%;
          text-align: center;
          font-size: 16px;
          font-weight: bold;
      }
    }
    .right {
      position: relative;
      width: 100rpx;
    }
  }
}
</style>
