<template>
  <div class="app">
    <Editor v-model="state" :formData="formData"></Editor>
  </div>
</template>

<script>
import { ref, provide } from "vue";
import data from "./data.json";
import Editor from "./package/editor";
import { registerConfig as config } from "./utils/editor-config";

export default {
  components: {
    Editor,
  },
  setup() {
    const state = ref(data);

    provide("config", config); // 将组件配置直接传入

    const formData = ref({});

    return { state, formData };
  },
};
</script>

<style lang="scss">
.app {
  position: fixed;
  top: 20px;
  left: 20px;
  right: 20px;
  bottom: 20px;
}
</style>
