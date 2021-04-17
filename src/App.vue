<template>
  <div>{{message}}</div>
</template>

<script>
import {ref} from "vue";
export default {
  setup(){
    const message = ref('hello');

    setTimeout(() => {
      message.value ='composition api';
    },2000);

    return {
      message
    }
  }
}
</script>

<style>

</style>