<template>
  <div class="spinner-container">
    <div class="spinner"></div>
  </div>
</template>

<style lang="scss" scoped>
@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.spinner {
  display: inline-block;
  width: 80px;
  height: 80px;

  &:after {
    content: " ";
    display: block;
    width: 64px;
    height: 64px;
    margin: 8px;
    border-radius: 50%;
    border: 6px solid #fff;
    border-color: #fff transparent #fff transparent;
    animation: lds-dual-ring 1.2s linear infinite;
  }

  &-container {
    background-color: rgba($color: #000000, $alpha: 0.5);
    display: flex;
    align-items: center;
    height: 100%;
    justify-content: center;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
  }
}
</style>
