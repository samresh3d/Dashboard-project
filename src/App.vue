<template>

  <div >
    <NavigationBar />
    <div class="horizontal-scrollable full-height m-5">
    <div class="row">
      <TaskBoardColumn
        heading="Project Overview"
        :initial-array="projectOverviewArray"
        alert-class="alert-info"
        :on-clicked="add"
        :edit="updateDataForTaskEditor"
      />
      <TaskBoardColumn
        heading="Tasks"
        :initial-array="tasksArray"
        alert-class="alert-info"
        :on-clicked="add"
        :edit="updateDataForTaskEditor"
      />
      <TaskBoardColumn
        heading="In-Progress"
        :initial-array="inProgressArray"
        alert-class="alert-warning"
        :on-clicked="add"
        :edit="updateDataForTaskEditor"
      />
      <TaskBoardColumn
        heading="In Review"
        :initial-array="inReviewArray"
        alert-class="alert-warning"
        :on-clicked="add"
        :edit="updateDataForTaskEditor"
      />
      <TaskBoardColumn
        heading="Completed"
        :initial-array="completedArray"
        alert-class="alert-success"
        :on-clicked="add"
        :edit="updateDataForTaskEditor"
      />
    </div>
    <TaskEditor
      :updateData="updateTask"
      :editorOpen="isEditorOpen"
      :description="updatedDescription"
      :task="updatedTask"
      :hideBox="hideEditor"
    />
  </div>
      <FooterSection />
  </div>
</template>

<script>
import TaskBoardColumn from "./components/TaskBoardColumn.vue";
import TaskEditor from "./components/TaskEditor.vue";
import NavigationBar from "./components/NavigationBar.vue";
import FooterSection from "./components/FooterSection.vue";

export default {
  name: "App",
  created() {
    document.title = "Trello dashboard Task || Samresh Pathak";
  },
  components: {
    TaskBoardColumn,
    TaskEditor,
    NavigationBar,
    FooterSection,
  },
  data() {
    return {
      newTask: "",
      updatedDescription: "",
      updatedTask: "",
      selectedElement: null,
      isEditorOpen: false,
      projectOverviewArray: [
        {
          task: "Lorem ipsum dolor sit amet, consectetuer adipiscing elit.",
          description: "This is Lorem ipsum description",
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
      ],
      tasksArray: [
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
      ],
      inProgressArray: [
        {
          task: "Nunc dignissim risus id metus.",
          description: "This is water description",
        },
        {
          task: "Cras ornare tristique elit.",
          description: "This is firming  description",
        },
      ],
      inReviewArray: [
        {
          task: "Vestibulum commodo felis quis tortor.",
          description: "This is water description",
        },
      ],
      completedArray: [
        {
          task: "Ut aliquam sollicitudin leod",
          description: "This is firming  description",
        },
      ],
    };
  },
  methods: {
    add() {
      if (this.newTask) {
        this.projectOverview.push({ task: this.newTask });
        this.newTask = "";
      }
    },
    updateDataForTaskEditor(element) {
      this.isEditorOpen = true;
      this.selectedElement = element;
      this.updatedDescription = this.selectedElement.description;
      this.updatedTask = this.selectedElement.task;
    },
    updateTask(updatedDescription, updatedTask) {
      console.log(`${updatedDescription}\n${updatedTask}`);
      this.isEditorOpen = false;
      this.selectedElement.description = updatedDescription;
      this.selectedElement.task = updatedTask;
    },
    hideEditor() {
      this.isEditorOpen = false;
    },
  },
};
</script>

<style>
.full-height {
  min-height: 70vh;
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
