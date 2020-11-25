<template>
  <button @click="emitClick">イベント駆動ボタン</button>
</template>

<script lang="ts">
import Vue from "vue";
import { Component, Emit } from "vue-property-decorator";

export type EmitButtonClickEventValue = {
  message: string;
};

@Component
export default class EmitButton extends Vue {
  @Emit("click")
  emitClick(): EmitButtonClickEventValue {
    return {
      message: "myEmitMessage"
    };
  }
}
</script>

<style></style>
