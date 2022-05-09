<template>
  <div class="lds-dual-ring"></div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.lds-dual-ring {
  margin-top: 6rem;
  display: inline-block;
  width: 80px;
  height: 80px;
}
.lds-dual-ring:after {
  content: " ";
  display: block;
  width: 64px;
  height: 64px;
  margin: 8px;
  border-radius: 50%;
  border: 6px solid $color-heading;
  border-color: $color-heading transparent $color-heading transparent;
  animation: lds-dual-ring 1.2s linear infinite;
}
@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
