<template>
  <div id="app">
    <emit-button @click="onEmitButtonClick" />
    <callback-button :on-click="onCallbackButtonClick" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import EmitButton, {
  EmitButtonClickEventValue
} from "./components/EmitButton.vue";
import CallbackButton, {
  CallbackButtonOnClickCallback
} from "./components/CallbackButton.vue";

@Component({
  components: {
    EmitButton,
    CallbackButton
  }
})
export default class App extends Vue {
  // イベント駆動の場合、イベントから渡される値の型を知っている必要がある
  onEmitButtonClick(value: EmitButtonClickEventValue) {
    console.log(value.message);
    // -> 'myEmitMessage'
  }

  // コールバック駆動の場合、コールバック関数のインターフェースを知っている必要がある
  onCallbackButtonClick: CallbackButtonOnClickCallback = value => {
    console.log(value.message);
    // -> 'myCallbackMessage'
  };
}
</script>

<style></style>
