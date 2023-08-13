<template>
  <form @submit.prevent>
    <h3>Create todo</h3>
    <to-do-input
      v-model="toDo.title"
      class="input"
      type="text"
      placeholder="Name"
    />
    <to-do-input
      v-model="toDo.body"
      class="input"
      type="text"
      placeholder="Description"
    />
    <to-do-button class="btn-inp" @click="createToDo">Create</to-do-button>
  </form>
</template>

<script>
import ToDoButton from "./ToDoButton.vue";
import ToDoInput from "./ToDoInput.vue";
export default {
  components: {
    ToDoButton,
    ToDoInput,
  },
  data() {
    return {
      toDo: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createToDo() {
      this.toDo.id = Date.now();
      this.$emit("create", this.toDo);
      this.toDo = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
.btn-inp {
  margin-top: 15px;
}
</style>
