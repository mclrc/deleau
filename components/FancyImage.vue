<template>
  <div
    class="image-container"
    :style="{
      height,
      width,
      background: backgroundProperty,
      backgroundRepeat: 'no-repeat',
      backgroundSize: 'cover',
      backgroundPosition: 'center',
      backgroundAttachment: 'fixed',
    }"
  >
    <h1>{{ $props.label }}</h1>
  </div>
</template>

<script>

export default {
  props: ["src", "dimm", "width", "height", "label"],
  computed: {
    backgroundProperty() {
      return `linear-gradient(rgba(0, 0, 0, ${
        this.$props.dimm || 0.5
      }), rgba(0, 0, 0, ${this.$props.dimm || 0.5})), url('${
        this.$props.src
      }')`;
    },
  },
};
</script>

<style lang="scss" scoped>
.image-container {
  display: flex;
  justify-content: center;
  align-items: center;

  h1 {
    color: white;
    font-size: 3rem;
    font-weight: lighter;
    letter-spacing: 4px;
    margin: 3rem;
  }
}
</style>