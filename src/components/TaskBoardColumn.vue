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
          class="list-group-item d-flex justify-content-between text-wrap"
          v-for="element in initialArray"
          :key="element.task"
        >
          <span  v-b-tooltip.hover :title="element.description">{{ element.task }}</span>
          <b-button
            class="ml-2 btn btn-light"
            type="button"
            varient="primary"
            @click="updateTask(element)"
            ><b-icon icon="pencil"></b-icon
          ></b-button>
        </div>
      </draggable>
      <div class="form-inline add-task-input-wrapper">
        <b-form-input
          v-model="newTask"
          placeholder="Add Task... ⏎"
          @keyup.enter="add"
        ></b-form-input>
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
    edit:Function,
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
        this.taskArray.push({ task: this.newTask, description: "Add Task Description!" });
        this.newTask = "";
      }
    },
    updateTask(element) {
      this.edit(element);
    },
  },
};
</script>

<style>
.kanban-column {
  min-height: 200px;
  min-width: 200px;
  max-width: 350px;
}

.form-inline .form-control {
  width: 100% !important;
}
</style>
