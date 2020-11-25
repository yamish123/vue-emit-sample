<template>
  <button @click="executeClickCallback">コールバック駆動ボタン</button>
</template>

<script lang="ts">
import Vue from "vue";
import { Component, Prop } from "vue-property-decorator";

export type CallbackButtonOnClickCallback = (value: {
  message: string;
}) => void;

@Component
export default class CallbackButton extends Vue {
  @Prop({ type: Function, required: false })
  onClick?: CallbackButtonOnClickCallback;

  executeClickCallback() {
    if (!this.onClick) return;
    this.onClick({ message: "myCallbackMessage" });
  }
}
</script>

<style></style>
