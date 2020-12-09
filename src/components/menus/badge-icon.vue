<template>
  <view class="th-badge-icon f-container f-center">
    <slot />
    <view class="badge-icon">
      <slot name="badge" />
    </view>
  </view>
</template>

<script>
import tag from '../tags/tag.vue';
export default {
  components: { tag },
};
</script>

<style lang="scss" scoped>
@import '../../common/common.scss';

.th-badge-icon {
  position: relative;
  width: 100%;
  height: 100%;

  .badge-icon-container {
    width: 80%;
    height: 80%;
  }
  .badge-icon {
    position: absolute;
    top: 0;
    right: 0;
  }
}
</style>
