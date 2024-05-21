<template>
<div class="content">
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
          <input type="search" class="form-control form-control-lg rounded-5" placeholder="Filter...">
        </div>
        <div class="my-3 text-muted">menampilkan 1 dari </div>
        <table class="table table-bordered border-dark text-white ">
          <thead>
              <tr class="text-center">
                <td>ID</td>
                <td>NAMA</td>
                <td>KEANGGOTAAN</td>
                <td>KELAS</td>
                <td>KEPERLUAN</td>
                <td>TANGGAL</td>
                <td>JAM</td>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(visitors,i) in visitors" :key="i" class="text-center">
                <td>{{ i+1 }}.</td>
                <td>{{ visitors.nama }}</td>
                <td>{{ visitors.keanggotaan.nama }}</td>
                <td>{{ visitors.tingkat}}-{{ visitors.jurusan }}{{ visitors.kelas }}</td>
                <td>{{ visitors.keperluan.nama }}</td>
                <td>{{ visitors.tanggal }}</td>
                <td>{{ visitors.jam.split(".")[0] }} </td>
              </tr>
            </tbody>
        </table>
        </div>
        </div>
      </div>
    </div>
  
  <!-- <button type="submit" class="btn btn-dark btn-lg rounded-5 px-5">Mencari Buku</button> -->
  <nuxt-link to="/buku" class="btn btn-dark btn-lg rounded-5 px-5 mx-2">Mencari Buku</nuxt-link>

  <!-- <button type="submit" class="btn btn-dark btn-lg rounded-5 px-5">Selesai</button> -->
  <nuxt-link to="/" class="btn btn-dark btn-lg rounded-5 px-5">Selesai</nuxt-link>
</template>

<script setup>
const supabase= useSupabaseClient()

const visitors = ref([])
const getPengunjung =async () => {
  const { data, error } = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
  if(data) visitors.value = data
}
onMounted(() =>{
  getPengunjung()
})



</script>

<style scoped>
.content {
  background-image: url('@/assets/home.png');
  background-size: cover;
  height: 100vh;
  width: 100%;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  color:rgb(255, 255, 255);
}
.btn{
  font-family: sans Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  background-color: rgb(255, 255, 255);
  color: rgb(0, 0, 0);
  float :right;
}

thead, tbody, td{
  border: 2px solid black;
}
</style> 
