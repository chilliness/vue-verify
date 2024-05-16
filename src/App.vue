<template>
  <div class="page-wrap">
    <div class="btn" v-for="(item, i) in 3" :key="i" @click="which = i">{{ "样式" + (i + 1) }}</div>
    <template v-for="(item, i) in 3" :key="i">
      <tag-captcha :type="i + 1" @handleClose="which = -1" @handleRefresh="handleRefresh" @handleSucc="handleSucc" @handleFail="handleFail" v-if="which === i" />
    </template>
  </div>
</template>

<script>
import { toRefs, reactive } from "vue";
import TagCaptcha from "@/components/tag-captcha/index.vue";

export default {
  components: { TagCaptcha },
  setup(props) {
    let vm = reactive({ which: -1 });

    vm.handleRefresh = (args) => console.log("刷新", args);
    vm.handleSucc = (args) => console.log("成功", args);
    vm.handleFail = (args) => console.log("失败", args);

    return { ...toRefs(vm) };
  },
};
</script>

<style lang="scss" scoped>
.page-wrap {
  padding-top: 25vh;
  .btn {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100px;
    height: 36px;
    margin: 30px auto;
    font-size: 14px;
    color: #fff;
    cursor: pointer;
    border-radius: 50px;
    background: #3c76f4;
    -webkit-tap-highlight-color: transparent;
  }
}
</style>
