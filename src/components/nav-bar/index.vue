<script setup lang="ts">
import { useDarkMode, useToggleDarkMode } from "@/composables/useToggleDarkMode";

const onClickRight = (event: TouchEvent | MouseEvent) => {
  useToggleDarkMode(event);
};
</script>

<template>
  <van-nav-bar left-text="返回" left-arrow fixed placeholder>
    <template #right>
      <div id="navbar_right"></div>
    </template>
  </van-nav-bar>
</template>

<style scoped></style>
