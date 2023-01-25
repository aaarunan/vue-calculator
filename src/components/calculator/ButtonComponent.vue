<template>
  <div :class="[type, 'button']" @click="handleInput">
    {{ label }}
  </div>
</template>
<style scoped>
.button {
  background-color: #fff;
  border: 1px solid #ccc;
  text-align: center;
  font-size: 1.5em;
  padding: 20px 0;
}

.button:hover {
  background-color: #f7f7f7;
  cursor: pointer;
}
</style>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    label: String,
    value: Number,
    type: String,
  },
  methods: {
    handleInput() {
      this.$emit("handleData", { value: Number });
    },
  },
});
</script>
<style scoped>
.operator {
  background-color: #ffc107;
  color: #fff;
}

.operator:hover {
  background-color: #ffa000;
}

.equal {
  background-color: #4caf50;
  color: #fff;
}

.equal:hover {
  background-color: #3e8e41;
}

.clear {
  background-color: #f44336;
  color: #fff;
}

.clear:hover {
  background-color: #e53935;
}
</style>
