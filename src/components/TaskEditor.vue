<template>
  <b-container
    mb="6"
    class="fixed-bottom edit-task border rounded p-3 m-auto"
    :class="{ invisible: !editorOpen }"
  >
    <b-button variant="light" class="float-right close-button" @click="hideBox"
      ><b-icon icon="x"></b-icon
    ></b-button>
    <div class="task mb-3 mt-2">
      <h4>Task</h4>
      <b-form-textarea
        name="inputTask"
        class="mb-2"
        :value="task"
        placeholder="Edit Task... ⏎"
        @keyup="updateTask"
      ></b-form-textarea>
    </div>
    <div class="description mb-3 mt-2">
      <h4>Description</h4>
      <b-form-textarea
        ref="inputDesc"
        class="mb-2"
        :value="description"
        placeholder="Edit Description... ⏎"
        @keyup="updateDescription"
      ></b-form-textarea>
    </div>
    <b-button variant="primary" @click="updateTaskData">Save</b-button>
  </b-container>
</template>

<script>
export default {
  name: "TaskEditor",
  props: {
    updateData: Function,
    hideBox: Function,
    editorOpen: Boolean,
    description: String,
    task: String,
  },
  data() {
    return {
      updatedDescription: this.description,
      updatedTask: this.task,
    };
  },
  methods: {
    updateTaskData() {
      let updatedDescription =
        this.updatedDescription !== ""
          ? this.updatedDescription
          : this.$refs.inputDesc.value;
      let updatedTask =
        this.updatedTask !== "" ? this.updatedTask : this.$refs.inputTask.value;
      this.updateData(updatedDescription, updatedTask);
    },
    updateDescription(event) {
      this.updatedDescription = event.target.value;
    },
    updateTask(event) {
      this.updatedTask = event.target.value;
    },
  },
};
</script>
<style>
.edit-task {
  background: #f2f3f6;
}
</style>
