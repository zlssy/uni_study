<template>
  <view class="th-menus-group">
    <swiper :indicator-dots="hasDots">
      <swiper-item>
        <view class="menus-group-container">
          <view
            class="menus-group-item"
            :style="{
              width: itemWidth + '%',
              height: itemHeight + '%',
            }"
          >
            <badge-icon class="menus-group-icon">
              <tag slot="badge" name="测试" style="background:red;"></tag>
              <view class="iconfont icontijiao menus-group-icon-item"></view>
            </badge-icon>
            <view class="menus-group-text"><text>AAA</text></view>
          </view>
        </view>
      </swiper-item>
    </swiper>
  </view>
</template>

<script>
import Tag from '../tags/tag.vue';
import badgeIcon from './badge-icon.vue';
export default {
  components: { badgeIcon, Tag },
  props: {
    menus: {
      type: Array,
      default: [],
    },
    row: {
      type: Number,
      default: 4,
    },
    col: {
      type: Number,
      default: 2,
    },
  },
  data() {
    return {};
  },
  computed: {
    itemWidth() {
      return 100 / this.row;
    },
    itemHeight() {
      return 100 / this.col;
    },
    groupCount() {
      return this.row * this.col;
    },
    hasDots() {
      const groups = Math.ceil(this.menus / this.groupCount);
      return groups > 1;
    },
  },
};
</script>

<style lang="scss" scoped>
@import '../../common/common.scss';

.th-menus-group {
  height: 100%;

  swiper {
    height: 100%;
  }
  .menus-group-container {
    height: 100%;
    display: flex;
    overflow: hidden;

    .menus-group-item {
      display: flex;
      flex-direction: column;

      ::v-deep .menus-group-icon {
        flex: 4;
        .th-badge-icon .badge-icon{
          .th-tag {
            background-color: red;
            color: red;
          }
        }
        .menus-group-icon-item {
          font-size: 48px;
          text-align: center;
        }
      }
      .menus-group-text {
        flex: 1;
        text-align: center;
        text-overflow: ellipsis;
      }
    }
  }
}
</style>
