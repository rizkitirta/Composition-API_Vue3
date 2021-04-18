<template>
  <div>Count : {{ nilai }}</div>
  <button @click="add">Add</button>
</template>

<script>
import { reactive, ref, toRefs, computed, watch } from "vue";
export default {
  setup() {
    const counter = reactive({
      nilai: 0,
    });

    const num1 = ref(1);
    const num2 = ref(2);

    const add = () => {
      // counter.nilai++;
      num1.value++;
      num2.value++;
    };

    watch([num1, num2], (after, before) => {
      console.log(after,before);
      // console.log(num2.value);
      // console.log(after);
      // console.log(before);
    });

    // watch(
    //   () => counter.nilai,
    //   (current, before) => {
    //     console.log(counter.nilai);
    //     console.log(current);
    //     console.log(before);
    //   }
    // );

    return {
      ...toRefs(counter),
      add,
    };
  },
};
</script>

<style>
</style>