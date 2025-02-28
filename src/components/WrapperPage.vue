<template>
  <Page>
    <StackLayout>
      <Label text="Wrapper Page!" />
      <Frame id="main-frame">
        <InnerPage />
      </Frame>
    </StackLayout>
  </Page>
</template>

<script>
import InnerPage from "./InnerPage.vue";
export default {
  components: { InnerPage },
};
</script>

<style></style>
