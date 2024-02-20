<script>
export default {
  data() {
    return {};
  },
};
</script>

<template>
  <nav class="navbar">
    <div class="container container-fluid">
      <a class="navbar-brand">Instagram</a>
      <form class="d-flex" role="search">
        <input
          class="form-control me-2"
          type="search"
          placeholder="Search"
          aria-label="Search"
        />
      </form>
      <div class="d-flex align-items-center">
        <font-awesome-icon icon="fa-regular fa-heart" size="xl" />
        <font-awesome-icon icon="fa-solid fa-house-chimney" />
        <div class="profile-pic">
          <img class="profile img-fluid" src="../../assets/img/grumpy-675.jpg" alt="">
        </div>
      </div>
    </div>
  </nav>
</template>

<style lang="scss" scoped>
.navbar {
  border-bottom: 2px solid rgb(200, 200, 200);

  .fa-heart,
  .fa-house-chimney {
    cursor: pointer;
    margin-right: 15px;
  }
  .profile-pic {
    width: 50px;
    height: 50px;
    border-radius: 50%;

    .profile{
      border-radius: 50%;
    }
  }
}
</style>
