<template>
  <user-component
    class="active"
    :label="label"
    :user="user"
    blabla="testing"
    @submit="onSubmit"
  >
    <div>Ini Slot</div>
  </user-component>
  <button @click="changeName">Change</button>
</template>

<script>
import { ref, reactive } from "vue";
import UserComponent from "./components/UserComponent.vue";
export default {
  components: { UserComponent },
  setup() {
    const label = ref("Biodata");
    const user = reactive({
      name: "Rizki",
      age: 25,
    });

    const changeName = () => {
      user.name = "Admin Kedua";
    };

    const onSubmit = (val) => {
      console.log(val);
    };

    return {
      label,
      user,
      changeName,
      onSubmit,
    };
  },
};
</script>

<style>
</style>