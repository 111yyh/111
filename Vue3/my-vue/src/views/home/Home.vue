<template>
  <div v-for="(item, index) in list" :index="item.id">
    <common :index="index" @update="handleInputChange"></common>
  </div>
  <a-button @click="d()" :disabled="!allState">11</a-button>
  <div>
    <interval></interval>
  </div>
</template>

<script>
import { defineComponent, ref, reactive, computed } from "vue";
import common from "../../components/common.vue";
import interval from "../../components/interval.vue"
export default defineComponent({
  components: {
    common,
    interval
  },
  setup() {
    let State = ref(true);
    const value1 = ref("");
    const val = ref([]);
    const list = reactive([
      {
        id: "g",
        name: "g",
        value: "",
        state: true,
      },
      {
        id: "y",
        name: "y",
        value: "",
        state: true,
      },
    ]);
    const allState = computed(() => {
      for (let index = 0; index < list.length; index++) {
        if (list[index].state == false) {
          State.value = false;
          break;
        } else {
          continue;
        }
      }
      if (State.value == false) {
        return false;
      } else {
        return true;
      }
    });
    const handleInputChange = (value, index, state) => {
      // 根据索引保存每个子组件的值
      console.log("1111", value);
      val.value[index] = value;
      list[index].state = state;
      console.log("222", list);
    };
    const d = () => {
      console.log(val.value);
    };
    return {
      d,
      allState,
      val,
      list,
      value1,
      handleInputChange,
    };
  },
});
</script>
