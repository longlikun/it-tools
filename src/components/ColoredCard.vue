<script setup lang="ts">
import type { Component } from 'vue';

const props = defineProps<{ icon: Component; title: string }>();
const { icon, title } = toRefs(props);
</script>

<template>
  <c-card class="colored-card">
    <div class="card-content">
      <div class="icon-wrapper">
        <n-icon class="icon" size="32" :component="icon" />
      </div>
      <div class="text-content">
        <n-h3 v-if="title" class="title">
          <n-ellipsis>{{ title }}</n-ellipsis>
        </n-h3>

        <div class="description">
          <n-ellipsis :line-clamp="1" :tooltip="false">
            <slot />
          </n-ellipsis>
        </div>
      </div>
    </div>
  </c-card>
</template>

<style lang="less" scoped>
.colored-card {
  background: rgb(37, 99, 108);
  background: linear-gradient(48deg, rgba(37, 99, 108, 1) 0%, rgba(59, 149, 111, 1) 60%, rgba(20, 160, 88, 1) 100%);
  color: #fff;
  border: none;
  padding: 10px 16px; 

  .card-content {
    display: flex;
    align-items: center;
    gap: 16px;
  }

  .icon-wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    
    .icon {
      opacity: 0.9;
    }
  }

  .text-content {
    flex: 1;
    min-width: 0; 
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .title {
    color: #fff;
    margin: 0;
    font-size: 22px;
    font-weight: 600;
    line-height: 1.2;
  }

  .description {
    opacity: 0.9;
    margin: 2px 0 0 0;
    font-size: 16px;
    line-height: 1.4;
    font-weight: 400;

    ::v-deep(a) {
      color: inherit;
      text-decoration: underline;
      font-weight: 600;
      transition: opacity ease 0.2s;
      padding: 0 4px;

      &:hover {
        opacity: 0.8;
      }
    }
  }
}
</style>
