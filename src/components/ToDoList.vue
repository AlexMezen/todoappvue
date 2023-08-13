<template>
  <div v-if="toDos?.length > 0">
    <h3 class="pl">ToDo list</h3>
    <TransitionGroup name="toDo-list">
      <to-do-item
        class="toDo"
        v-for="toDo in toDos"
        :toDo="toDo"
        :key="toDo.id"
        @edit="handleEdit"
        @remove="$emit('remove', toDo)"
      >
      </to-do-item>
    </TransitionGroup>
  </div>
  <h3 v-else class="ple">ToDo list is empty</h3>
</template>

<script>
import ToDoItem from "@/components/ToDoItem";
export default {
  components: { ToDoItem },
  props: {
    toDos: {
      type: Array,
      required: true,
    },
  },
  methods: {
    handleEdit(editedToDo) {
      this.$emit("edit", editedToDo);
    },
  },
};
</script>

<style>
.pl {
  display: inline;
  margin-left: 15px;
}
.ple {
  display: flex;
  margin-left: 15px;
  color: red;
}
.toDo-list-enter-active,
.toDo-list-leave-active {
  transition: opacity 0.4s ease;
}

.toDo-list-enter-from,
.toDo-list-leave-to {
  opacity: 0;
}
.toDo-list-move {
  transition: transform 0.4s ease;
}
</style>
