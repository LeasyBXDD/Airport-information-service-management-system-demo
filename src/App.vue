<template>
  <a-layout style="min-height: 100vh">
    <!-- 侧边栏 -->
    <a-layout-sider v-model:collapsed="collapsed" collapsible>
      <div class="logo" />
      <a-menu :default-selected-keys="['1']" style v-model:selectedKeys="selectedKeys" theme="dark" mode="inline">
        <!-- 图片logo -->
        <a-menu-item>
          <img />
        </a-menu-item>

        <!-- 登录 -->
        <a-menu-item key="1">
          <router-link to="/">
            <pie-chart-outlined />
            <span>登录</span>
          </router-link>
        </a-menu-item>

        <!-- 注册 -->
        <a-menu-item key="2">
          <router-link to="/register">
            <desktop-outlined />
            <span>注册</span>
          </router-link>
        </a-menu-item>

        <!-- 客户 -->
        <a-sub-menu key="sub1">
          <template #title>
            <span>
              <user-outlined />
              <span>客户</span>
            </span>
          </template>
          <a-menu-item key="3">增加</a-menu-item>
          <a-menu-item key="4">删除</a-menu-item>
          <a-menu-item key="5">修改</a-menu-item>
          <a-menu-item key="6">查看</a-menu-item>
        </a-sub-menu>

        <!-- 航班 -->
        <a-sub-menu key="sub2">
          <template #title>
            <span>
              <team-outlined />
              <span>航班</span>
            </span>
          </template>
          <a-menu-item key="7">增加</a-menu-item>
          <a-menu-item key="8">删除</a-menu-item>
          <a-menu-item key="9">修改</a-menu-item>
          <a-menu-item key="10">查看</a-menu-item>
        </a-sub-menu>

        <!-- 预定 -->
        <a-sub-menu key="sub3">
          <template #title>
            <span>
              <user-outlined />
              <span>预定</span>
            </span>
          </template>
          <a-menu-item key="11">增加</a-menu-item>
          <a-menu-item key="12">删除</a-menu-item>
          <a-menu-item key="13">修改</a-menu-item>
          <a-menu-item key="14">查看</a-menu-item>
        </a-sub-menu>

        <!-- 座位 -->
        <a-sub-menu key="sub4">
          <template #title>
            <span>
              <user-outlined />
              <span>座位</span>
            </span>
          </template>
          <a-menu-item key="15">增加</a-menu-item>
          <a-menu-item key="16">删除</a-menu-item>
          <a-menu-item key="17">修改</a-menu-item>
          <a-menu-item key="18">查看</a-menu-item>
        </a-sub-menu>

        <!-- 飞机 -->
        <a-sub-menu key="sub5">
          <template #title>
            <span>
              <user-outlined />
              <span>飞机</span>
            </span>
          </template>
          <a-menu-item key="19">增加</a-menu-item>
          <a-menu-item key="20">删除</a-menu-item>
          <a-menu-item key="21">修改</a-menu-item>
          <a-menu-item key="22">查看</a-menu-item>
        </a-sub-menu>

        <!-- 机场 -->
        <a-sub-menu key="sub6">
          <template #title>
            <span>
              <user-outlined />
              <span>机场</span>
            </span>
          </template>
          <a-menu-item key="23">增加</a-menu-item>
          <a-menu-item key="24">删除</a-menu-item>
          <a-menu-item key="25">修改</a-menu-item>
          <a-menu-item key="26">查看</a-menu-item>
        </a-sub-menu>

        <!-- 文档 -->
        <a-menu-item key="27">
          <file-outlined />
          <span>文档</span>
        </a-menu-item>
      </a-menu>
    </a-layout-sider>

    <!-- 主体 -->
    <a-layout>
      <!-- 头部 -->
      <a-layout-header style="background: #fff; padding: 0" />

      <!-- 内容 -->
      <a-layout-content style="margin: 0 16px">

        <div style="margin-bottom: 18px;"></div>
        <div :style="{ padding: '24px', background: '#fff', minHeight: '360px' }">
          <router-view />
        </div>
      </a-layout-content>

      <!-- 底部 -->
      <a-layout-footer style="text-align: center">
        李奕哲 ©2023 Created by Ant UED
      </a-layout-footer>

    </a-layout>
  </a-layout>
</template>
<script>
import { PieChartOutlined, DesktopOutlined, UserOutlined, TeamOutlined, FileOutlined } from '@ant-design/icons-vue';
import { defineComponent, ref } from 'vue';
export default defineComponent({
  components: {
    PieChartOutlined,
    DesktopOutlined,
    UserOutlined,
    TeamOutlined,
    FileOutlined,
  },
  data() {
    return {
      collapsed: ref(false),
      selectedKeys: ref(['1']),
    };
  },
});
</script>
<style scoped>
#components-layout-demo-side .logo {
  height: 32px;
  margin: 16px;
  background: rgba(255, 255, 255, 0.3);
}

.site-layout .site-layout-background {
  background: #fff;
}

[data-theme='dark'] .site-layout .site-layout-background {
  background: #141414;
}

</style>