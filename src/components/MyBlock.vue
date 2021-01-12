<template>
  <div
    class="test__block"
    :style="{ left: positionX + 'px', top: positionY + 'px' }"
  >
    {{ position.posx }} , {{ position.posy }}
  </div>
</template>

<script>
export default {
  props: ["position"],
  computed: {
    positionX() {
      return this.position.posx * 40;
    },
    positionY() {
      return this.position.posy * 40;
    },
  },
};
</script>

<style>
.test__block {
  position: absolute;
  content: "";
  display: inline;
  padding: 0.2rem;
  text-align: center;
  margin: 0;
  height: 2rem;
  width: 2rem;
  background-image: linear-gradient(to right, #7ed56f, #28b485);
}
</style>
