<template>
  <div class="toDo">
    <div v-if="!editing">
      <div><strong>ToDo title:</strong> {{ toDo.title }}</div>
      <div><strong>Description:</strong> {{ toDo.body }}</div>
    </div>
    <div v-else>
      <to-do-input v-model="editedTitle" placeholder="Title" />
      <to-do-input v-model="editedBody" placeholder="Description" />
    </div>

    <div class="pst-btns">
      <to-do-button @click="toggleEditMode">{{
        editing ? "Save" : "Edit"
      }}</to-do-button>
      <to-do-button class="btn-del" @click="$emit('remove')"
        >Delete</to-do-button
      >
      <to-do-button @click="toggleCheckmark" :class="{ checked: isChecked }"
        >Done</to-do-button
      >
    </div>
  </div>
</template>

<script>
import ToDoButton from "./ToDoButton.vue";
import ToDoInput from "./ToDoInput.vue";

export default {
  components: {
    ToDoButton,
    ToDoInput,
  },
  props: {
    toDo: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      isChecked: false,
      editing: false,
      editedTitle: this.toDo.title,
      editedBody: this.toDo.body,
    };
  },
  methods: {
    toggleCheckmark() {
      this.isChecked = !this.isChecked;
    },
    toggleEditMode() {
      if (this.editing) {
        this.$emit("edit", {
          ...this.toDo,
          title: this.editedTitle,
          body: this.editedBody,
        });
      }
      this.editing = !this.editing;
    },
  },
};
</script>
<style scoped>
.btn-del {
  margin-right: 15px;
}
.checked::after {
  content: "\2713";
  margin-right: 1px;
}
.toDo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  margin: 15px;
  border: 2px solid rgb(0, 92, 128);
}

.pst-btns {
  display: flex;
  flex-wrap: nowrap;
}
.pst-btns .btn:first-of-type {
  margin-right: 15px;
  margin-left: 10px;
  width: 68px;
}
</style>
