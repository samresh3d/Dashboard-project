<template>
  <div class=" horizontal-scrollable  full-height m-5">
    <div class="row">
      <TaskBoardColumn
        heading="Project Overview"
        :initial-array="projectOverviewArray"
        alert-class="alert-info"
        :on-clicked="add"
      />
      <TaskBoardColumn
        heading="Tasks"
        :initial-array="tasksArray"
        alert-class="alert-info"
        :on-clicked="add"
      />
      <TaskBoardColumn
        heading="In-Progress"
        :initial-array="inProgressArray"
        alert-class="alert-warning"
        :on-clicked="add"
      />
      <TaskBoardColumn
        heading="In Review"
        :initial-array="inReviewArray"
        alert-class="alert-warning"
        :on-clicked="add"
      />
      <TaskBoardColumn
        heading="Completed"
        :initial-array="completedArray"
        alert-class="alert-success"
        :on-clicked="add"
      />
    </div>
  </div>
</template>

<script>
import TaskBoardColumn from "./components/TaskBoardColumn.vue";

export default {
  name: "App",
  components: {
    TaskBoardColumn,
  },
  data() {
    return {
      newTask: "",
      projectOverviewArray: [
        {
          task: "Lorem ipsum dolor sit amet, consectetuer adipiscing elit.",
          description: "This is description",
        },
        {
          task: "Aliquam tincidunt mauris eu risus.",
          description: "This is two description",
        },
        {
          task: "Vestibulum auctor dapibus neque",
          description: "This is three description",
        },
        {
          task: "Nunc dignissim risus id metus.",
          description: "This is water description",
        },
        {
          task: "Cras ornare tristique elit.",
          description: "This is firming  description",
        },
        {
          task: "Vivamus vestibulum ntulla nec ante.",
          description: "This is description",
        },
        {
          task: "Fusce pellentesque suscipit nibh.",
          description: "This is two description",
        },
        {
          task: "Integer vitae libero ac risus egestas placerat.",
          description: "This is three description",
        },
        {
          task: "Vestibulum commodo felis quis tortor.",
          description: "This is water description",
        },
        { task: "Ut aliquam sollicitudin leod", description: "This is firming  description" },
      ],
      tasksArray: [],
      inProgressArray: [],
      inReviewArray: [],
      completedArray: [],
    };
  },
  methods: {
    add() {
      if (this.newTask) {
        this.projectOverview.push({ task: this.newTask });
        this.newTask = "";
      }
    },
  },
};
</script>

<style>
.full-height{
  height: 100%;
}
.horizontal-scrollable > .row {
  overflow-x: auto;
  white-space: nowrap;
  flex-wrap: nowrap;
}

.horizontal-scrollable > .row > .col {
  display: inline-block;
  float: none;
}
</style>
