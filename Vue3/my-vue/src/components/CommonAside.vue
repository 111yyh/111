<template>
  <a-layout-sider class="sider">
    <a-menu
      mode="inline"
    >
      <a-menu-item :key="item.name" v-for="item in noChildren()">
        <template #title>{{ item.label }}</template>
      </a-menu-item>
      <a-sub-menu key="sub2">
        <template #title>Navigation Two</template>
        <a-menu-item key="5">Option 5</a-menu-item>
        <a-menu-item key="6">Option 6</a-menu-item>
      </a-sub-menu>
    </a-menu>
  </a-layout-sider>
</template>

<script>
export default {
  setup() {
    const list = [
      {
        path: "/user",
        name: "user",
        label: "用户管理",
        icon: "user",
        url: "User",
      },
      {
        label: "其他",
        icon: "location",
        children: [
          {
            path: "/page1",
            name: "page1",
            label: "页面1",
            icon: "setting",
            url: "Page1",
          },
          {
            path: "/page2",
            name: "page2",
            label: "页面2",
            icon: "setting",
            url: "Page2",
          },
        ],
      },
    ];

    const noChildren = () => {
        return list.filter((item) => {
            !item.children
        })
    };
    const hasChildren = () => {
        return list.filter((item) => {
            item.children
        })
    }

    return {
        noChildren,
        hasChildren
    }
  }
};
</script>
