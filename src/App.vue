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
    const addNum = ref(2);

    const add = () => {
      counter.nilai++;
    };

    const result = computed(() => 
      counter.nilai + addNum.value
    );

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