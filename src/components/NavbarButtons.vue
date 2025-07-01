<script setup lang="ts">
import { IconBrandGithub, IconBrandX, IconFeather, IconMoon, IconPencil, IconSun } from '@tabler/icons-vue';
import { useStyleStore } from '@/stores/style.store';

const styleStore = useStyleStore();
const { isDarkTheme } = toRefs(styleStore);
</script>

<template>
  <c-tooltip :tooltip="$t('home.nav.myBlog')" position="bottom">
    <c-button
      circle
      variant="text"
      href="https://blog.eimoon.com"
      rel="noopener"
      target="_blank"
      :aria-label="$t('home.nav.myBlog')"
    >
      <n-icon size="25" :component="IconPencil" color="#14B8A6" />
    </c-button>
  </c-tooltip>

  <c-tooltip :tooltip="$t('home.nav.github')" position="bottom">
    <c-button
      circle
      variant="text"
      href="https://github.com/CorentinTh/it-tools"
      target="_blank"
      rel="noopener noreferrer"
      :aria-label="$t('home.nav.githubRepository')"
    >
      <n-icon size="25" :component="IconBrandGithub" color="#166534" />
    </c-button>
  </c-tooltip>

  <!-- <c-tooltip :tooltip="$t('home.nav.twitterX')" position="bottom">
    <c-button
      circle
      variant="text"
      href="https://x.com/ittoolsdottech"
      rel="noopener"
      target="_blank"
      :aria-label="$t('home.nav.twitterXAccount')"
    >
      <n-icon size="25" :component="IconBrandX" color="#000000" />
    </c-button>
  </c-tooltip> -->

  <!-- <c-tooltip :tooltip="$t('home.nav.about')" position="bottom">
    <c-button circle variant="text" to="/about" :aria-label="$t('home.nav.aboutLabel')">
      <n-icon size="25" :component="IconInfoCircle" />
    </c-button>
  </c-tooltip> -->
  <c-tooltip :tooltip="isDarkTheme ? $t('home.nav.lightMode') : $t('home.nav.darkMode')" position="bottom">
    <c-button circle variant="text" :aria-label="$t('home.nav.mode')" @click="() => styleStore.toggleDark()">
      <n-icon v-if="isDarkTheme" size="25" :component="IconSun" color="#FFA500" />
      <n-icon v-else size="25" :component="IconMoon" color="#4B4B4B" />
    </c-button>
  </c-tooltip>
</template>

<style lang="less" scoped>
.n-button {
  &:not(:last-child) {
    margin-right: 5px;
  }
}
</style>
