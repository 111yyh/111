<template>
  <a-form name="form" :model="formState">
    <a-form-item name="inputValue" :rules="rules.input">
      <a-input
        v-model:value="formState.inputValue"
        placeholder=""
        @change="update"
      />
    </a-form-item>
  </a-form>
  <a-button type="primary" @click="dianji()" :disabled="!formState.state">点击</a-button>
</template>

<script>
export default {
  data() {
    return {
      formState: {
        inputValue: "",
        state: false
      },
      rules: {
        input: [
          {
            validator: this.checkValue,
            trigger: "change",
          },
        ],
      },
    };
  },
  emits: ["update"],
  props: {
    index: {
      type: Number,
      default: 0
    }
  },
  methods: {
    checkValue(_rule, value) {
      let RegNum = /^[0-9]+(\.[0-9]{1})?$/;
      if (parseFloat(value) == NaN || !RegNum.test(value)) {
        this.formState.state = false;
        return Promise.reject('请输入整数或一位小数的数字');
      } else {
        this.formState.state = true;
        return Promise.resolve();
      }
    },
    dianji() {
      console.log(this.formState.inputValue);
    },
    update(e) {
      this.$emit("update", e.target.value, this.$props.index, this.formState.state);
    },
  },
};
</script>
