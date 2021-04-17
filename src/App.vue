<template>
  <div>Count : {{ nilai }}</div>
  <button @click="add">Add</button>
  <div>Result : {{ result }}</div>
</template>

<script>
import { reactive, ref, toRefs, computed } from "vue";
export default {
  setup() {
    const counter = reactive({
      nilai: 0,
    });
    const addNum = ref(1);

    const add = () => {
      result.value = 5;
      counter.nilai++;
    };

    const result = computed({
      get: () => counter.nilai + addNum.value,
      set: val => addNum.value = val
    });

    return {
      ...toRefs(counter),
      add,
      result,
    };
  },
};
</script>

<style>
</style>