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
          <view class="f-container hot-container">
            <text>热门搜索</text>
            <tag-group class="index-tags" :data="hotTagList" @tagTap="hotTagTap"></tag-group>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
import navbar from '../../components/nav-bar/navbar.vue';
import TagGroup from '../../components/tags/tag-group.vue';

export default {
  components: { navbar, TagGroup },
  data() {
    return {
      title: '腾讯健康',
      cityName: '长沙',
      hotTagList: [],
    };
  },
  onLoad() {
    console.log('page onload');
    const createTag = (name, link = '') => ({ name, link });
    this.hotTagList = [
      createTag('百万医疗险'),
      createTag('HPV疫苗'),
      createTag('流感疫苗'),
    ];
  },
  methods: {
    search() {
      console.log('goto search page.');
    },
    hotTagTap(index) {
      console.log(index);
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
  height: 300px;
  border-bottom-left-radius: 12px;
  border-bottom-right-radius: 12px;
  background-color: $primary;
}
.hot-container {
  color: #c6c6c6;
  align-items: center;
}
::v-deep .index-tags .th-tag{
	color: #666;
	background-color: white;
}
</style>
