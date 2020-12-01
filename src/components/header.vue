<template>
  <div class="header">
    <img class="hanger" src="@/assets/hanger.png" alt="hanger_logo" />
    <img class="mycloz" src="@/assets/my_cloz.png" alt="mycloz_logo" />
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  margin: 0 auto;
  justify-content: space-around;
  align-items: center;
  max-width: 350px;
  height: 100px;
  border-bottom: none;
  padding-top: 60px;
  padding-bottom: 70px;
}
.hanger {
  flex: 1;
  width: 120px;
  padding-right: 15px;
  padding-left: 25px;
}
.mycloz {
  flex: 2;
  max-height: 120px;
  padding-right: 25px;
}
</style>
