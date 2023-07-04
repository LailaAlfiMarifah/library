<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container">
        <router-link to="/" class="navbar-brand">My Library</router-link>
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
            <router-link to="/" class="nav-link">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/buku" class="nav-link">Daftar Buku</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/kategori" class="nav-link">Kategori Buku</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/anggota" class="nav-link">Daftar Anggota</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/keterangan" class="nav-link">Keterangan</router-link>
          </li>
        </ul>
      </div>
    </nav>
    <div class="container mt-4">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
}
.navbar-brand{
  border: 1px solid #ffffff;
  padding: 5px 10px;
  border-radius: 20px;
  text-decoration: none;
  color: white;
}
</style>
