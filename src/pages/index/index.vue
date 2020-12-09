<template>
  <view class="content">
    <navbar :title="title">
      <view class="city-choose" slot="left">
        <text>{{ cityName }}</text>
        <view class="iconfont iconxiangxia"></view>
      </view>
    </navbar>
    <view class="main-container">
      <view class="header">
        <view class="main-content">
          <view class="f-container index-search" @tap="gotoSearch">
            <view class="iconfont iconsousuo search-icon"></view>
            <view class="search-scroll-text">
              <swiper
                class="search-swiper"
                autoplay="true"
                duration="500"
                interval="5000"
                vertical="true"
                circular="true"
              >
                <swiper-item
                  v-for="(item, index) in hotSearchList"
                  :key="index"
                >
                  <view class="search-swiper-item"
                    ><text>{{ item.title }}</text></view
                  >
                </swiper-item>
              </swiper>
            </view>
            <view class="search-tail-text">搜索</view>
          </view>
          <view class="f-container hot-container">
            <text>热门搜索</text>
            <tag-group
              class="index-tags"
              :data="hotTagList"
              @tagTap="hotTagTap"
            ></tag-group>
          </view>
          <view class="quick-links f-container f-center">
            <view class="quick-links-left f-container f-center">
              <view class="iconfont iconweixin quick-links-icon"></view>
              <view>
                <text class="quick-links-title">医保电子凭证</text>
                <tag class="quick-links-tag" name="现金红包">
                  <view
                    class="iconfont icontijiao quick-links-money"
                    slot="before"
                  ></view>
                </tag>
              </view>
            </view>
            <view class="quick-links-right f-container f-center">
              <view class="iconfont iconQQ-quanquan quick-links-icon"></view>
              <view>
                <text class="quick-links-title">电子健康卡</text>
                <text class="quick-links-subtitle">国家卫生健康委</text>
              </view>
            </view>
            <view></view>
          </view>
        </view>
      </view>
      <view class="main-content menus">
        <slide-menus></slide-menus>
      </view>
    </view>
  </view>
</template>

<script>
import SlideMenus from '../../components/menus/slide-menus.vue';
import navbar from '../../components/nav-bar/navbar.vue';
import TagGroup from '../../components/tags/tag-group.vue';
import Tag from '../../components/tags/tag.vue';

export default {
  components: { navbar, TagGroup, Tag, SlideMenus },
  data() {
    return {
      title: '腾讯健康',
      cityName: '长沙',
      hotTagList: [],
      hotSearchList: [],
    };
  },
  onLoad() {
    console.log('page onload');
    const createTag = (name, link = '') => ({ name, link });
    const createSearch = (title) => ({ title });
    this.hotTagList = [
      createTag('百万医疗险'),
      createTag('HPV疫苗'),
      createTag('流感疫苗'),
    ];
    this.hotSearchList = [
      createSearch('夏日皮肤晒伤怎么办？'),
      createSearch('高血压患者应该注意什么饮食'),
      createSearch('黄芪有什么功效？'),
      createSearch('儿童感冒不可忽视的细节'),
    ];
  },
  methods: {
    search() {
      console.log('goto search page.');
    },
    hotTagTap(index) {
      console.log(index);
    },
    gotoSearch() {
      console.log('goto search');
    },
  },
};
</script>

<style lang="scss" scoped>
@import '../../common/common.scss';

.city-choose {
  display: flex;
  flex-direction: row;
  width: 100%;
  justify-content: center;
}
.header {
  width: 100%;
  height: 200px;
  border-bottom-left-radius: 12px;
  border-bottom-right-radius: 12px;
  background-color: $primary;

  .hot-container {
    color: #c6c6c6;
    align-items: center;
    margin-top: 12px;

    ::v-deep .index-tags .th-tag-item {

      .th-tag {
        color: #666;
        background-color: white;
        font-size: 12px;
        padding: 1px 8px;
      }
    }
  }
}
.index-search {
  border-radius: 12px;
  height: 36px;
  line-height: 36px;
  background-color: white;
  overflow: hidden;
  align-items: center;

  .search-icon {
    width: 40px;
    text-align: center;
    color: $mainText;
  }
  .search-scroll-text {
    flex: 1;
    color: $mainText;

    .search-swiper {
      height: 36px;

      .search-swiper-item {
        height: 36px;
      }
    }
  }
  .search-tail-text {
    width: 60px;
    border-left: 1px solid #f6f6f6;
    text-align: center;
    color: $primary;
    font-weight: bold;
  }
}
.quick-links {
  margin-top: 12px;

  .quick-links-left {
    flex: 1;
  }
  .quick-links-right {
    flex: 1;
    border-left: solid 1px #74a6f1;
  }
  .quick-links-icon {
    width: 60px;
    font-size: 36px;
    color: white;
    text-align: center;
  }
  .quick-links-title {
    display: block;
    font-size: 14px;
    font-weight: bold;
    color: white;
  }
  .quick-links-subtitle {
    font-size: 10px;
    color: #f6f6f6;
  }
  ::v-deep .th-tag {
    width: 90px;
    font-size: 12px;
    color: $primary;
    padding: 3px 6px;
    text-align: center;
  }
  .quick-links-money {
    width: 20px;
    font-size: 12px;
    text-align: center;
    color: red;
    animation: th-shake 2s 0s infinite;
  }
  .quick-links-tag {
    margin-top: 6px;
  }
}
.menus {
  height: 260px;
  background-color: white;
  border-radius: 12px;
  position: relative;
  margin-top: -60px;
}
</style>
