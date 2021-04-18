<template>
  <dir>
    <div>{{ label }} : {{ user.name }}</div>
    <div>{{ description }}</div>

    <button @click="submit">Submit</button>
    <hr>
    <slot />
  </dir>
</template>

<script>
import { ref, toRefs, computed, onMounted } from "vue";
export default {
  props: {
    label: {
      type: String,
      default: "",
    },
    user: {
      type: Object,
      default: () => {},
    },
  },
  setup(props, { attrs, slots, emit }) {
    const { label, user } = toRefs(props);
    const description = computed(() => {
      return `${label.value} : ${user.value.name}`;
    });

    onMounted(() => {
      console.log(attrs);
      console.log(slots);
    });

    const submit = () => {
      emit("submit", "ini adalah emit dari user component");
    };

    return { description,submit };
  },
};
</script>
<style>
</style>