<template>
  <view
    class="th-tag"
    :class="[extClass]"
    @tap="handlerClick"
  >
    {{ name }}
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
  padding: 1px 4px;
  border-radius: 12px;
}
</style>
