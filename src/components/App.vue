<template>
  <div>
    <h1 class="pwp">Page with ToDo</h1>
    <div class="mtb">
      <to-do-button @click="showDialog">Create todo</to-do-button>
    </div>
    <div class="mtb"></div>
    <dialog-to-do @hide="hideDialog" :show="dialogVisible">
      <to-do-form @create="createToDo"></to-do-form>
    </dialog-to-do>
    <to-do-list
      :toDos="toDos"
      @remove="removeToDo"
      @edit="editToDo"
    ></to-do-list>
  </div>
</template>
<script>
import ToDoForm from "@/components/ToDoForm";
import ToDoList from "@/components/ToDoList";
import DialogToDo from "@/components/DialogToDo.vue";
import ToDoButton from "@/components/ToDoButton.vue";
import ToDoInput from "@/components/ToDoInput.vue";

export default {
  components: {
    ToDoForm,
    ToDoList,
    DialogToDo,
    ToDoButton,
    ToDoInput,
  },
  data() {
    return {
      toDos: [],
      dialogVisible: false,

      sortOptions: [
        { value: "title", name: "By name" },
        { value: "body", name: "By content" },
      ],
    };
  },
  methods: {
    createToDo(toDo) {
      this.toDos.push(toDo);
      this.dialogVisible = false;
    },
    removeToDo(toDo) {
      this.toDos = this.toDos.filter((p) => p.id !== toDo.id);
    },
    editToDo(editedToDo) {
      const index = this.toDos.findIndex((toDo) => toDo.id === editedToDo.id);
      if (index !== -1) {
        const updatedToDos = [...this.toDos];
        updatedToDos[index] = editedToDo;
        this.toDos = updatedToDos;
      }
    },

    hideDialog() {
      this.dialogVisible = false;
    },
    showDialog() {
      this.dialogVisible = true;
    },
  },
  mounted() {
    const storedToDos = localStorage.getItem('toDos');
    if (storedToDos) {
      this.toDos = JSON.parse(storedToDos);
    }
  },

  watch: {
    toDos: {
      handler(newToDos) {
        localStorage.setItem('toDos', JSON.stringify(newToDos));
      },
      deep: true, 
    },
  },






};
</script>
<style>
.mtb {
  display: inline-block;
  margin-top: 10px;
  margin-bottom: 20px;
  margin-left: 15px;
}
.pwp {
  margin-left: 15px;
}
.inpcl {
  width: 20%;
  margin-left: 15px;
}
::selection {
  color: whitesmoke;
  background-color: darkcyan;
}
</style>
