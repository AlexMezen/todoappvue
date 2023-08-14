<template>
  <input :value="modelValue" @input="updateInput" class="input" type="text" />
</template>

<script>
export default {
  props: {
    modelValue: [String, Number],
  },
  methods: {
    updateInput(event) {
      this.$emit("update:modelValue", event.target.value);
    },
  },
};
</script>

<style scoped>
.input {
  margin-top: 15px;
  margin-right: 10px;
  padding: 15px;
  border: 1px solid rgb(0, 92, 128);
  color: rgb(0, 92, 128);
}
</style>
