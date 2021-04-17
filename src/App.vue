<template>
  <div>Name : {{ name }}</div>
  <div>Age : {{ age }}</div>
</template>

<script>
import { reactive, toRefs } from "vue";
export default {
  setup() {
    const user = reactive({
      name: "Rizki ",
      age: "19",
    });

    setTimeout(() => {
      user.name = "Tirta";
      user.age = "20";
    }, 2000);

    return {
      ...toRefs(user),
    };
  },
};
</script>

<style>
</style>