<template>
<div class="content">
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3 text-muted">menampilkan {{ visitors.length }}</div>
        <div class="table table-responsive">
          <table class="table table-bordered border-dark text-white ">
            <thead>
                <tr class="text-center">
                  <td>ID</td>
                  <td>NAMA</td>
                  <td>KATEGORI</td>
                  <td>KELAS</td>
                  <td>KEPERLUAN</td>
                  <td>TANGGAL</td>
                  <td>WAKTU</td>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(visitor,i) in visitors" :key="i" class="text-center">
                  <td>{{ i+1 }}.</td>
                  <td>{{ visitor.nama }}</td>
                  <td>{{ visitor.keanggotaan.nama }}</td>
                  <td>{{ visitor.tingkat}}-{{ visitor.jurusan }}{{ visitor.kelas }}</td>
                  <td>{{ visitor.keperluan.nama }}</td>
                  <td>{{ visitor.tanggal }}</td>
                  <td>{{ visitor.waktu.split(".")[0] }} </td>
                </tr>
              </tbody>
          </table>
        </div>
        </div>
        <div class="row d-flex justify-content-end text-center">
          <nuxt-link to="/buku" class="col-lg-3 col-2 btn btn-dark btn-lg rounded-5 px-5 mx-2">Mencari Buku</nuxt-link>
          
          <nuxt-link to="/" class="col-lg-3 col-2 btn btn-dark btn-lg rounded-5 px-5 mx-2">Selesai</nuxt-link>
        </div>
      
        <!-- <button type="submit" class="btn btn-dark btn-lg rounded-5 px-5">Selesai</button> -->
        </div>
      </div>
    </div>
  
  <!-- <button type="submit" class="btn btn-dark btn-lg rounded-5 px-5">Mencari Buku</button> -->
</template>

<script setup>
const supabase= useSupabaseClient()

const visitors = ref([])

const getPengunjung = async () => {
  const { data, error } = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
  if(data) visitors.value = data
}


onMounted(() => {
    getPengunjung()
})
</script>

<style scoped>
.content {
  background-image: url('@/assets/home.png');
  background-size: cover;
  height: 100vh;
  width: 100%;
  padding-top: 15%;
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
