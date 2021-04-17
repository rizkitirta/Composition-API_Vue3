<template>
  <div>Name : {{ user.name }}</div>
  <div>Age : {{ user.age }}</div>
</template>

<script>
import { reactive } from "vue";
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
      user,
    };
  },
};
</script>

<style>
</style>