<script setup lang="ts">
import { onMounted, ref, watch } from 'vue';
import { useRoute } from 'vue-router';

const props = withDefaults(defineProps<{
  slot: string
  client?: string
  format?: string
  responsive?: boolean
  layout?: string
  style?: string
}>(), {
  client: 'ca-pub-7372212183953468',
  format: 'auto',
  responsive: true,
  layout: '',
  style: 'display:block',
});

const insRef = ref<HTMLElement | null>(null);
const route = useRoute();

function pushAd() {
  try {
    // @ts-expect-error injected by AdSense script
    (window.adsbygoogle = window.adsbygoogle || []).push({});
  }
  catch (e) {
    console.warn('[AdSense] push failed', e);
  }
}

onMounted(pushAd);
watch(() => route.fullPath, () => {
  if (insRef.value && !insRef.value.getAttribute('data-adsbygoogle-status')) {
    pushAd();
  }
});
</script>

<template>
  <ins
    ref="insRef"
    class="adsbygoogle"
    :style="style"
    :data-ad-client="client"
    :data-ad-slot="slot"
    :data-ad-format="format"
    :data-ad-layout="layout || undefined"
    :data-full-width-responsive="responsive ? 'true' : 'false'"
  />
</template>
