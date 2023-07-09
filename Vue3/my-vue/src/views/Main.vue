<template>
  <a-layout>
    <CommonAside></CommonAside>
    <a-layout>
      <CommonHeader></CommonHeader>
      <a-layout-content>
        <router-view></router-view>
      </a-layout-content>
    </a-layout>
  </a-layout>
</template>

<script>
import { defineComponent } from 'vue';
import CommonHeader from '../components/CommonHeader.vue'
import CommonAside from '../components/CommonAside.vue'
export default defineComponent({
    components: {
        CommonHeader,
        CommonAside
    }
})

</script>

<style scoped>
.sider {
    background-color: #fff;
}
</style>
