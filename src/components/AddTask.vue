<template>
  <form @submit="onSubmit" class="add-form">
    <div class="mb-3">
      <label for="Task" class="form-label">Task</label>
      <input
        type="text"
        v-model="text"
        class="form-control"
        id="Task"
        placeholder="Add Task"
      />
    </div>
    <div class="mb-3">
      <label for="DateTime" class="form-label">Day & Time</label>
      <input
        type="Datetime"
        v-model="day"
        class="form-control"
        id="DateTime"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-check">
      <label class="form-check-label" for="Reminder"> Set Reminder </label>
      <input
        class="form-check-input"
        v-model="reminder"
        type="checkbox"
        value=""
        id="Reminder"
      />
    </div>
    <button type="submit" class="btn btn-dark" style="width: 100%">
      Save Task
    </button>
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      day: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      if (!this.text) {
        alert("Please add a task");
        return;
      }

      const newTask = {
        // id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      }
      this.$emit('add-task', newTask)
        
      this.text = "";
      this.day = "";
      this.reminder = "";
    },
  },
};
</script>