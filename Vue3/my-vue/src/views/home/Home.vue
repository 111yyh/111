<template>
  <div v-for="(item, index) in list" :index="item.id">
    <common :index="index" @update="handleInputChange"></common>
  </div>
  <a-button @click="d()" :disabled="allState">11</a-button>
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
    let State = ref([]);
    const value1 = ref("");
    const val = ref([]);
    const list = reactive([
      {
        id: "g",
        name: "g",
        value: "",
      },
      {
        id: "y",
        name: "y",
        value: "",
      },
    ]);
    const allState = computed(() => {
      return State.value.some(value => value)
    });
    const handleInputChange = (value, index, state) => {
      // 根据索引保存每个子组件的值
      console.log("1111", value);
      val.value[index] = value;
      State.value[index] = state;
      console.log("222", State.value);
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
