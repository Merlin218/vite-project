<template>
  <layout>
    <template #header>
      <layout-header :navBarConfig="indexConfig">
        <template #title>
          <span
            :style="{
              color: '#fff',
            }"
            >首页</span
          >
        </template>
        <template #footer>
          <a-button @click="router.push('/login')">管理员登录</a-button>
        </template>
      </layout-header>
    </template>
    <template #sider>
      <layout-sider></layout-sider>
    </template>
    <template #content>
      <router-view></router-view>
    </template>
  </layout>
</template>

<script>
import { provide } from 'vue';
import { useRouter } from 'vue-router';
import Layout from '../components/Layout/Layout.vue';
import LayoutHeader from '../components/Layout/LayoutNav.vue';
import LayoutSider from '../components/Layout/LayoutSider.vue';
import {
  navBarConfig as indexConfig,
  navBarTheme,
} from '../configs/index.config';

export default {
  components: {
    Layout,
    LayoutHeader,
    LayoutSider,
  },
  setup() {
    const router = useRouter();
    provide('theme', navBarTheme);
    console.log(router.currentRoute.value.fullPath);
    return {
      indexConfig,
      router,
    };
  },
};
</script>

<style></style>
