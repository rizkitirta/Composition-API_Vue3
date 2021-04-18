<template>
  <div class="container" style="margin-top: 20px">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">Simple Todo App</h5>
        <div class="row">
          <div class="col-10">
            <input
              v-model="todo"
              type="text"
              class="form-control"
              @keyup.enter="add"
            />
          </div>
          <div class="col-auto">
            <button class="btn btn-success" @click="add">Add</button>
          </div>
        </div>
        <list :todos="list" @deleteTodo="deleteTodo" @doneTodo="doneTodo" />
        <small>Total Todo : {{ totalTODO }}</small>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, reactive, onMounted, computed, toRefs } from "vue";
import List from "./components/List.vue";
export default {
  components: { List },
  setup() {
    const todo = ref("");
    const todos = reactive({
      list: [],
    });

    onMounted(() => {
      todos.list = JSON.parse(localStorage.getItem("todos"));
    });

    const totalTODO = computed(() => {
      return todos.list.length;
    });

    const add = () => {
      todos.list.unshift({
        activity: todo.value,
        isDone: false,
      });
      todo.value = "";
      saveToLocalStorage();
    };

    const deleteTodo = (todoIndex) => {
      todos.list = todos.list.filter((item, index) => {
        if (index != todoIndex) {
          return item;
        }
      });
      saveToLocalStorage();
    };

    const doneTodo = (todoIndex) => {
      todos.list = todos.list.filter((item, index) => {
        if (index == todoIndex) {
          item.isDone = true;
        }

        return item;
      });
      saveToLocalStorage();
    };

    const saveToLocalStorage = () => {
      localStorage.setItem("todos", JSON.stringify(todos.list));
    };

    return { todo, ...toRefs(todos), totalTODO, add, deleteTodo, doneTodo };
  },
};
</script>

<style>
</style>