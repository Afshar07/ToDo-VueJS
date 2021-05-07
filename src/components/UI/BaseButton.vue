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
.change{
  border: none;
  width: 15vw;
  height: 7vh;
  background-color: rgba(0, 147, 173, 0.808);
  color: #fff;
  font-size: 1rem;
  border-radius: 20px;
  cursor: pointer;
}
.change:hover{
  background-color: rgba(0, 147, 173);

}


</style>
