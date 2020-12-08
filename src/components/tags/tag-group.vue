<template>
  <view class="th-tag-group" :class="[extClass]">
    <tag
      v-for="(tag, index) in data"
      :key="index"
      :name="tag.name"
      @itemTap="handlerItemTap(index)"
    ></tag>
  </view>
</template>

<script>
import tag from './tag.vue';

export default {
  components: { tag },
  props: {
    data: {
      type: Array,
      default: [],
    },
  },
  methods: {
    handlerItemTap(index) {
      this.$emit('tagTap', index);
    },
  },
};
</script>

<style lang="scss" scoped>
@import '../../common/common.scss';
.th-tag-group {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;

  tag {
    margin: 0 4px;
  }
}
</style>
