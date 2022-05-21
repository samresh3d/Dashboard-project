<template>
  <div class="col">
    <div class="p-2 alert" :class="alertClass">
      <h3>{{ heading }}</h3>
      <draggable
        class="list-group kanban-column"
        :list="initialArray"
        group="tasks"
      >
        <div
          class="list-group-item"
          v-for="element in initialArray"
          :key="element.task"
        >
          {{ element.task }}
        </div>
      </draggable>
      <div class="form-inline">
        <b-form-input v-model="newTask" placeholder="Enter new Task" @keyup.enter="add"></b-form-input>
        <b-button class="ml-2" varient="primary" @click="add">Add Task</b-button>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";

export default {
  name: "TaskBoardColumn",
  components: {
    draggable,
  },
  props: {
    heading: String,
    initialArray: Array,
    alertClass: String,
  },
  data() {
    return {
      newTask: "",
      taskArray: this.initialArray,
    };
  },

  methods: {
    add() {
      if (this.newTask) {
        this.taskArray.push({ task: this.newTask });
        this.newTask = "";
      }
    },
  },
};
</script>

<style>
.kanban-column {
  min-height: 200px;
  min-width: 200px;
}
</style>
