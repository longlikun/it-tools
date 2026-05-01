<script setup lang="ts">
import { useHead } from '@vueuse/head';
import AdSense from '../components/AdSense.vue';

useHead({ title: 'About - IT Tools' });
</script>

<template>
  <div mx-auto mt-50px max-w-600px>
    <c-markdown :markdown="$t('about.content')" />
    <div class="mt-40px">
      <AdSense slot="4322640612" format="fluid" layout="in-article" />
    </div>
  </div>
</template>
