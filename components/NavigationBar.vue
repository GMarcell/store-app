<template>
  <div class="Navbar">
    <div class="left">
      <h2>LOGO</h2>
    </div>
    <div class="right">
      <h2>User Management</h2>
      <h2>Product Management</h2>
      <h2>Cart</h2>
      <h2>Login</h2>
    </div>
  </div>
</template>
<script>
export default {
    
}
</script>
<style lang="scss" scoped>
  h2{
    margin-right: 10px;
    margin-left: 10px;
  }
  .Navbar{
    background-color: blue;
    display: flex;
    justify-content: space-between;
    .right{
      display: flex;
    }
  }
</style>