<template>
  <button :type="type" :class="mode">
      <slot></slot>
  </button>
</template>

<script>
export default {
  props: ['type', 'mode']
};
</script>

<style scoped>
.delete {
  border: none;
  width: 6vw;
  height: 4vh;
  background-color: rgba(160, 0, 0, 0.84);
  color: #fff;
  cursor: pointer;
  border-radius: 30px;
}
.delete:hover {
  background-color: rgb(160, 0, 0);
}
</style>
