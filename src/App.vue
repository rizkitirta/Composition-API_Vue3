<template>
  <div>Count : {{ nilai }}</div>
  <button @click="add">Add</button>
</template>

<script>
import { reactive, ref, toRefs, computed, watchEffect } from "vue";
export default {
  setup() {
    const counter = reactive({
      nilai: 0,
    });

    const add = () => {
      counter.nilai++;
    };

    watchEffect(() => {
      console.log(counter.nilai)
    })

    return {
      ...toRefs(counter),
      add,
    };
  },
};
</script>

<style>
</style>