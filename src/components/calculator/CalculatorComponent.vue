<template>
  <div class="calculator">
    <div class="screen">{{ input }}</div>
    <div class="buttons-container">
      <Button
        v-for="button in buttons"
        :label="button.val"
        :key="button.val"
        :type="button.type"
        @click="handleInput(button)"
      />
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import Button from "./ButtonComponent.vue";

export default defineComponent({
  data() {
    return {
      input: " ",
      history: [],
      buttons: [
        { val: "(", type: "operator" },
        { val: ")", type: "operator" },
        { val: "AC", type: "clear" },
        { val: "-", type: "operator" },
        { val: "7", type: "num" },
        { val: "8", type: "num" },
        { val: "9", type: "num" },
        { val: "/", type: "operator" },
        { val: "4", type: "num" },
        { val: "5", type: "num" },
        { val: "6", type: "num" },
        { val: "*", type: "operator" },
        { val: "3", type: "num" },
        { val: "2", type: "num" },
        { val: "1", type: "num" },
        { val: "+", type: "operator" },
        { val: " ", type: "num" },
        { val: "0", type: "num" },
        { val: ".", type: "num" },
        { val: "=", type: "equal" },
      ],
    };
  },
  components: {
    Button,
  },
  methods: {
    handleInput(button: any) {
      if (button.type == "equal") {
        this.input = eval(this.input);
      } else if (button.type == "clear") {
        this.input = "";
      } else {
        this.input += this.validateInput(button);
      }
    },
    validateInput(button: any) {
      if (button.type == "operator") {
        if (
          (button.val != "+" || button.val != "-") &&
          this.input.length == 0
        ) {
          console.log(this.input.length);
          return "";
        }
      }
      return button.val;
    },
  },
});
</script>
<style scoped>
.calculator {
  margin: auto;
  width: 40%;
}
.buttons-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(5, 1fr);
  grid-gap: 5px;
  padding: 10px;
  border: 1px solid #ccc;
}

.screen {
  padding: 10px;
  text-align: right;
  height: 1.5em;
  background-color: #fff;
  border: 1px solid #ccc;
  font-size: 1.5em;
}
</style>
