<template>
  <view>
      <text class="f-test-color">{{test}}</text>
  </view>
</template>

<script>
export default {
    data(){
        return {
            test:'This is test content'
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