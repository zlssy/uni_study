<template>
  <view class="content">
    <navbar :title="title">
        <view class="city-choose" slot="left">
          <text>{{ cityName }}</text>
          <view class="iconfont iconxiangxia"></view>
        </view>
    </navbar>
  </view>
</template>

<script>
import navbar from '../../components/nav-bar/navbar.vue';

export default {
  components: { navbar },
  data() {
    return {
      title: '腾讯健康',
      cityName: '长沙',
    };
  },
  onLoad() {
    console.log('page onload');
  },
  methods: {},
};
</script>

<style lang="scss">
.city-choose {
  display: flex;
  flex-direction: row;
  width: 100%;
}
</style>
