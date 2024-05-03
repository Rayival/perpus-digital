<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-12">
          <!-- <h2 class="text-center my-4">BUKU</h2> -->
          <div class="my-3 mt-5">
            <input type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini?">
          </div>
          <div class="row text-end " style="color: white;">
            <p class="col-10 m-0 pt-2">Kategori :</p>
            <div class="col-2 ps-0">
              <select name="kategori" id="kategori" class="form-control form-control-sm rounded-5 form-select">
                <option value="" disabled selected>  </option>
                <option value="">Novel</option>
                <option value="">Pengetahuan Umum</option>
                <option value="">Bahasa</option>
                <option value="">Pengetahuan</option>
                <option value="">Cerita</option>
                <option value="">Pendidikan</option>
              </select>
          </div>
          </div>
          <div class="my-3 text-muted">menampilkan 3 dari 3</div>
          <div class="row">
            <div class="col-lg-2">
              <div class="card mb-3">
                <div class="card-body">
                  <img src="~/assets/CoverDilan.jpg" class="cover" alt="cover1">
                  <NuxtLink to="/buku/rincian"><button type="button" class="cover mt-3 btn btn-primary">lihat rincian</button></NuxtLink>
                </div>
              </div>
            </div>
            <div class="col-lg-2">
              <div class="card mb-3">
                <div class="card-body">
                  <img src="~/assets/CoverMilea.jpg" class="cover" alt="cover2">
                  <NuxtLink to="/buku/rincian"><button type="button" class="cover mt-3 btn btn-primary">lihat rincian</button></NuxtLink>
                </div>
              </div>
            </div>
            <div class="col-lg-2">
              <div class="card mb-3">
                <div class="card-body">
                  <img src="~/assets/CoverAncika.jpg" class="cover" alt="cover3">
                  <NuxtLink to="/buku/rincian"><button type="button" class="cover mt-3 btn btn-primary">lihat rincian</button></NuxtLink>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="row float-end">
        <nuxt-link to="/" class="btn btn-dark btn-lg rounded-5 px-5">selesai</nuxt-link>
      </div>
    </div>
  </div>
</template>


<style scoped>
.content {
  background-image: url('@/assets/bg-home-cari-buku.jpg');
  background-size: cover;
  height: 100vh;
  width: 100%;
}

.card-body {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}
.btn{
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  background-color: rgb(255, 255, 255);
  color: black;
  width: 150px;
  height: 50px;
}
.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}
</style>
