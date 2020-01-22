<template>
  <div>
    <img v-bind:src="image_url" />
  </div>
</template>

<script>
export default {
  props: ["image_url"]
};
</script>
