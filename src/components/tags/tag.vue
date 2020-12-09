<template>
  <view class="th-tag flex" :class="[extClass]" @tap="handlerClick">
    <slot name="before" />
    <text>{{ name }}</text>
    <slot name="after" />
  </view>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: '',
    },
    extClass: String,
  },
  computed: {},
  methods: {
    handlerClick() {
      this.$emit('itemTap');
    },
  },
};
</script>

<style lang="scss" scoped>
@import '../../common/common.scss';

.th-tag {
  box-sizing: border-box;
  padding: 1px 4px;
  border-radius: 12px;
  background-color: white;
  color: black;
}
</style>
