<script lang="ts" setup>
import {
  ref,
  computed,
  onMounted,
  onUnmounted,
  $navigateTo,
} from "nativescript-vue";
import Details from "./Details.vue";
import TestPage from "./TestPage.vue";
import WrapperPage from "./WrapperPage.vue";

const counter = ref(0);
const message = computed(() => {
  return `Blank {N}-Vue app: ${counter.value}`;
});

function logMessage() {
  console.log("You have tapped the message!");
}

let interval: any;
onMounted(() => {
  console.log("mounted");
  interval = setInterval(() => counter.value++, 100);
});

onUnmounted(() => {
  console.log("unmounted");
  clearInterval(interval);
});
</script>

<template>
  <Frame>
    <Page>
      <ActionBar>
        <Label text="Home" class="font-bold text-lg" />
      </ActionBar>

      <GridLayout rows="*, auto, auto, auto, auto, *" class="px-4">
        <Label
          row="1"
          class="text-xl align-middle text-center text-gray-500"
          :text="message"
          @tap="logMessage"
        />

        <Button
          row="2"
          @tap="$navigateTo(Details, { clearHistory: true })"
          class="mt-4 px-4 py-2 bg-white border-2 border-blue-400 rounded-lg"
          horizontalAlignment="center"
        >
          View Details
        </Button>

        <Button
          row="3"
          @tap="$navigateTo(TestPage, { clearHistory: true })"
          class="mt-4 px-4 py-2 bg-white border-2 border-blue-400 rounded-lg"
          horizontalAlignment="center"
        >
          View Test Page
        </Button>

        <Button
          row="4"
          @tap="$navigateTo(WrapperPage, { clearHistory: true })"
          class="mt-4 px-4 py-2 bg-white border-2 border-blue-400 rounded-lg"
          horizontalAlignment="center"
        >
          View Wrapper Page with nested Frame
        </Button>
      </GridLayout>
    </Page>
  </Frame>
</template>

<style>
/* .info {
    font-size: 20;
  } */
</style>
