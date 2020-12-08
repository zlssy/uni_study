<template>
  <view>
      <text class="f-test-color">{{test}}</text>
  </view>
</template>

<script>
export default {
    data(){
        return {
            test:'健康'
        }
    },
    onLoad(options){
        const {id} = options;
        console.log(`Param is ${id}`);
    }
}
</script>

<style>

</style>