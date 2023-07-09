<template>
  <a-layout-header class="header">
    <div class="left">
      <!-- 左侧图标 -->
      <a-button>
        <appstore-outlined :style="{ fontSize: '16px', color: '#08c' }" />
      </a-button>
    </div>
    <div class="right">
      <a-dropdown :trigger="['click']">
        <a-avatar size="large">
          <template #icon>
            <img src="../assets/images/user.png" alt="" @click.prevent />
          </template>
        </a-avatar>
        <template #overlay>
          <a-menu>
            <a-menu-item>
              <a href="javascript:;">1st menu item</a>
            </a-menu-item>
            <a-menu-item>
              <a href="javascript:;">2nd menu item</a>
            </a-menu-item>
            <a-menu-item>
              <a href="javascript:;">3rd menu item</a>
            </a-menu-item>
          </a-menu>
        </template>
      </a-dropdown>
    </div>
  </a-layout-header>
</template>

<script>
import { defineComponent } from "vue";
import { AppstoreOutlined } from "@ant-design/icons-vue";
export default defineComponent({
  components: {
    AppstoreOutlined,
  },
});
</script>

<style scoped>
.header {
  background-color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.header {
    padding: 0 10px 0 0;
}
</style>
