<template>
    <div>
      <h1>Daftar Buku</h1>
      <router-link to="/buku/tambah" class="btn btn-primary">Tambah Buku</router-link>
  
      <table class="table">
        <thead>
        <tr>
          <th>Kode</th>
          <th>Judul</th>
          <th>Pengarang</th>
          <th>Penerbit</th>
          <th>Tahun terbit</th>
          <th>Harga</th>
          <th>Aksi</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="book in buku" :key="book.id">
          <td>{{ book.kode }}</td>
          <td>{{ book.judul }}</td>
          <td>{{ book.pengarang }}</td>
          <td>{{ book.penerbit }}</td>
          <td>{{ book.tahun }}</td>
          <td>{{ book.harga }}</td>
          <td>
            <router-link :to="`/buku/ubah/${book.kode}`" class="btn btn-primary">Ubah</router-link>
            <button @click="deleteBook(book.kode)" class="btn btn-danger">Hapus</button>
          </td>
        </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    name: 'App',
    data() {
      return {
        buku : [],
      };
    },
    methods: {
      fetchBooks() {
        axios.get('http://localhost/buku/selectBuku.php')
            .then(response => {
              this.buku = response.data;
            })
            .catch(error => {
              console.error(error);
            });
      },
      deleteBook(kode) {
        if (confirm('Are you sure you want to delete this book?')) {
          axios.delete(`hhttp://localhost/buku/deleteBuku.php?kode=${kode}`)
              // eslint-disable-next-line no-unused-vars
              .then(response => {
                this.fetchBooks();
              })
              .catch(error => {
                console.error(error);
              });
        }
      },
    },
    mounted() {
      this.fetchBooks();
    },
  };
  </script>
  