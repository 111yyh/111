<template>
    <a-date-picker
        :allowClear="false"
        v-model="startValue"
        :disabled-date="disabledStartDate"
        @change="startDataChange"
        format="YYYY/MM"
        placeholder="Start"
        @openChange="handleStartOpenChange"
        picker="month"
      />
      <span> &nbsp;~&nbsp; </span>

      <a-date-picker
        :allowClear="false"
        v-model="endValue"
        :disabled-date="disabledEndDate"
        @change="endDataChange"
        format="YYYY/MM"
        placeholder="End"
        :open="endOpen"
        @openChange="handleEndOpenChange"
        picker="month"
      />
</template>

<script>

</script>