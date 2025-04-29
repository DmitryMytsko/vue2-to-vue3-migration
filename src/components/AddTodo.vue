<template>
  <div class="container">
    <h2 class="">Add Todo</h2>
    <div class="card">
      <div class="d-flex">
        <input
          class="form-control"
          placeholder="Add new todo"
          v-model="newTodo"
        />
        <button
          type="button"
          class="btn btn-primary"
          @click="addNewTodo"
        >
          Add
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import { useStore } from 'vuex';

export default {
  name: "AddTodo",
  setup() {
    const store = useStore();
    const newTodo = ref('');

    const addNewTodo = () => {
      store.dispatch('addTodo', newTodo.value);
      newTodo.value = '';
    };

    return {
      newTodo,
      addNewTodo,
    };
  },
};
</script>
