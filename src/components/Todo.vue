<script>
export default {
  data() {
    return {
      todo: "",
      todos: [
        {
          description: "Steal bananas",
        },
        {
          description: "Gas",
        },
      ],
    };
  },

  methods: {
    submitTask() {
      if (this.todo.length === 0) return;

      this.todos.push({
        description: this.todo,
        status: "to-do",
      });

      this.todo = "";
    },

    deleteTask(index) {
      // we would generally want to delete based on id (by adding a unique uuid to each todo item as it is created)
      this.todos.splice(index, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <h2 class="text-center mt-5">Todo App</h2>

    <div class="d-flex">
      <input
        v-model="todo"
        type="text"
        class="form-control"
        placeholder="Enter Todo"
      />
      <button @click="submitTask" class="btn btn-warning rounded-0">
        Submit
      </button>
    </div>

    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col" class="text-center">Task</th>
          <!-- <th scope="col" class="text-center">Status</th> -->
          <th scope="col" />
          <!-- <th scope="col" /> -->
        </tr>
      </thead>
      <tbody>
        <tr v-for="(todo, index) in todos" :key="index">
          <td>{{ todo.description }}</td>
          <!-- <td>{{ todo.status }}</td> -->
          <!-- <td>
            <div class="text-center" @click="editTask(index)">
              <span class="fa fa-pen" />
            </div>
          </td> -->
          <td>
            <div class="text-center" @click="deleteTask(index)">
              <span class="fa fa-trash" />
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>
