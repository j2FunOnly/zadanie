<template>
  <div class="panel">
    <h2 class="heading">{{ heading }}</h2>
    <slot></slot>
  </div>
</template>

<script>
/**
 * Just block with heading, have slot
 * @param {string} heading text of the h2
 */
export default {
  props: {
    heading: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped lang="scss">
.panel {
  margin-bottom: 40px;
}
.heading {
  margin: 0;
  margin-bottom: 18px;
  line-height: 1;
  font-size: 24px;
  font-weight: 400;
}
</style>
