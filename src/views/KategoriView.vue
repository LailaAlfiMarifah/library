<template>
    <div>
      <h1>Kategori Buku</h1>
      <!-- Tampilkan daftar kategori -->
      <table class="table">
        <thead>
        <tr>
          <th>Kode</th>
          <th>Kategori</th>
          <th>Aksi</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="category in kategori" :key="category.id">
          <td>{{ category.kode }}</td>
          <td>{{ category.kategori }}</td>
          <td>
            <router-link :to="`/kategori/${category.kode}`" class="btn btn-primary">Ubah</router-link>
            <button @click="deleteCategory(category.kode)" class="btn btn-danger">Hapus</button>
          </td>
        </tr>
        </tbody>
      </table>
      <router-link to="/kategori/tambah" class="btn btn-success">Tambah Kategori</router-link>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'App',
    data() {
      return {
        kategori: [],
      };
    },
    methods: {
      fetchCategories() {
        axios.get('http://localhost/buku/selectKategori.php')
            .then(response => {
              this.kategori = response.data;
            })
            .catch(error => {
              console.error(error);
            });
      },
      deleteCategory(kode) {
        if (confirm('Are you sure you want to delete this category?')) {
          axios.delete(`http://localhost/buku/deleteKategori.php?kode=${kode}`)
              .then(() => {
                alert('Category deleted successfully');
                this.fetchCategories();
              })
              .catch(error => {
                console.error(error);
              });
        }
      },
  
    },
    created() {
      this.fetchCategories();
    },
  };
  </script>
  