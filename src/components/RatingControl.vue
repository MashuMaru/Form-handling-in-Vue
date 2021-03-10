<template>
  <ul>
    <li v-bind:class="{ active: modelValue === 'poor' }">
      <button type="button" v-on:click="activate('poor')">Poor</button>
    </li>
    <li v-bind:class="{ active: modelValue === 'average' }">
      <button type="button" v-on:click="activate('average')">Average</button>
    </li>
    <li v-bind:class="{ active: modelValue === 'great' }">
      <button type="button" v-on:click="activate('great')">Great</button>
    </li>
  </ul>
</template>

<script>
export default {
  computed: {
    activeOption() {
        return this.modelValue;
    }
  },
  props: ['modelValue'],
  emits: ['update:modelValue'],
  methods: {
    activate(option) {
    //   this.activeOption = option;
      this.$emit('update:modelValue', option);
    }
  }
};
</script>

<style scoped>
.active {
  border-color: green;
}

.active button {
  color: green;
  border: 3px solid green;
}

ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}

li {
  margin: 0 1rem;
  border: 1px solid #ccc;
  padding: 1rem;
  display: flex;
  justify-content: center;
}

button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>
