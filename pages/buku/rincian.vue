<template>
    <div class="content">
        <div class="container-fluid">
            <div class="row d-flex justify-content-center flex-md-wrap" style="padding-top: 190px;">
                <div class="col-3 ">
                    <img class="row img-fluid" src="@/assets/CoverDilan.jpg" alt="" style="width: 250px;">
                    <div class="row">
                        <NuxtLink to="/buku/" class="btn btn-lg rounded-5" style="width: 10rem;">Kembali</NuxtLink>
                    </div>
                </div>
                <div class="col-8">
                    <div class="row">
                        <h1>Dilan 1990</h1>
                    </div>
                    <div class="row">
                        <h4>Pengarang : pidi baiq</h4>
                        <h4>Tahun Terbit : 2014</h4>
                        <h4>Genre : Novel, Fiksi</h4>
                    </div>
                    <div class="row">
                    </div>
                </div>
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
