<template>
    <div class="content">
        <div class="container-fluid">
            <div class="row d-flex justify-content-center flex-md-wrap" style="padding-top: 190px;">
                <div class="col-3 ">
                    <img class="row img-fluid" src="@/assets/CoverDilan.jpg" alt="" style="width: 250px;">                  
                </div>
                <div class="col-8 card rounded-5 text-dark text-center" style="width: 30rem; height: 20rem; padding-top: 50px; margin-top: 30px;">
                    <div class="row">
                        <h4>Judul Buku: Dilan 1990</h4>
                        <h4>Penulis : pidi baiq</h4>
                        <h4>Penerbit : Bandung Mizan Pustaka</h4>
                        <h4>Tahun Terbit : 2014</h4>
                        <h4>Lokasi Buku : Rak 1</h4>
                        <h4>Kategori : Novel, Fiksi</h4>
                    </div>
                </div>
            </div>
            <div class="row float-end">
                <NuxtLink to="/buku/" class="btn btn-lg rounded-5" style="width: 10rem;">Kembali</NuxtLink>
            </div>
        </div>
    </div>
</template>

  
  <script setup>
  
  </script>
  
  <style scoped>
  .content {
    background-image: url('@/assets/bg-home-cari-buku.jpg');
    background-size: cover;
    width: 100%;
    height: 100vh;
    font-family: 'Jockey One';
    color: rgb(255, 255, 255);
  }
  .btn {
    background-color: #fffeee;
    
  }
  </style>
