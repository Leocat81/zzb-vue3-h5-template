<script setup lang="ts">
import tabbar from "@/components/tabbar/index.vue";
// import NavBar from "@/components/nav-bar/index.vue";
import { useCachedViewStoreHook } from "@/store/modules/cached-view";
import { useDarkMode } from "@/composables/useToggleDarkMode";
import { computed, reactive } from "vue";

const cachedViews = computed(() => {
  return useCachedViewStoreHook().cachedViewList;
});
const themeVars = reactive({
  primaryColor: "#fec54e"
});
</script>

<template>
  <div class="app-wrapper">
    <van-config-provider :theme="useDarkMode() ? 'dark' : 'light'" :theme-vars="themeVars" theme-vars-scope="global">
      <nav-bar />
      <router-view v-slot="{ Component }">
        <keep-alive :include="cachedViews">
          <component :is="Component" />
        </keep-alive>
      </router-view>
      <!-- <tabbar /> -->
    </van-config-provider>
  </div>
</template>

<style lang="less" scoped>
@import "@/styles/mixin.less";

.app-wrapper {
  .clearfix();
  position: relative;
  height: 100%;
  width: 100%;
}
</style>
