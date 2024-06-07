<template>
  <div class="intro" style="background-color:#23323D">
      <div class="text-center" style="padding-top: 190px;">
          <h2>ISI BUKU KUNJUNGAN</h2>
          <div class="container-fluid">
            <form class="py-3 m-5" @submit.prevent="kirimData">
              <div class="row m-3 d-flex justify-content-center">
                <div class="col-sm-7">
                      <input v-model="nama" type="text" style="box-shadow: 2px 2px 2px #424242;" class="form-control" placeholder="Nama ..." aria-label="Nama ..." required/>
                    </div>
                  </div>
            <div class="mb-3">
                <div class="row m-3 justify-content-center">
                  <div class="col-sm-7">
                      <select v-model="kategori" class="form-control form-control-lg form-select" style="box-shadow: 2px 2px 2px #424242;" required>
                        <option value="" disabled selected>Kategori ...</option>
                        <option v-for="(item,i) in members" :key="i" :value="item.id">{{ item.nama }}</option>
                      </select>
                  </div>
                </div>
            </div>
                  <div class="row m-3 justify-content-center" v-if="kategori == '1'" @change="resetkelas">
                    <div class="col-sm-2 pb-2">
                              <select v-model="tingkat" class="form-select" aria-label="Disabled select example" style="box-shadow: 2px 2px 2px #424242;" required>
                                  <option value="">Tingkat</option>
                                  <option value="X">X</option>
                                  <option value="XI">XI</option>
                                  <option value="XII">XII</option>
                              </select>
                          </div>
                          <div class="col-sm-3 justify-content-center pb-2">
                              <select v-model="jurusan" class="form-select" aria-label="Disabled select example" style="box-shadow: 2px 2px 2px #424242;" required>
                                  <option value="">Jurusan</option>
                                  <option value="TJKT">TJKT</option>
                                  <option value="TBSM">TBSM</option>
                                  <option value="PPLG">PPLG</option>
                                  <option value="DKV">DKV</option>
                                  <option value="TOI">TOI</option>
                              </select>
                          </div>
                          <div class="col-sm-2 justify-content-center">
                              <select v-model="kelas" class="form-select" aria-label="Disabled select example" style="box-shadow: 2px 2px 2px #424242;" required>
                                  <option value="">Kelas</option>
                                  <option value="1">1</option>
                                  <option value="2">2</option>
                                  <option value="3">3</option>
                                  <option value="4">4</option>
                              </select>
                          </div>
                      </div>
                      <div class="row m-3 justify-content-center">
                          <div class="col-sm-7">
                            <select v-model="keperluan"  class="form-control">
                            <option value="" disabled>Keperluan</option>
                            <option v-for="(item,i) in objectives" :key="i" :value="item.id">{{ item.nama }}</option>
                            </select>
                          </div>
                      </div>
                          <input type="submit" class="btn btn-dark btn-lg rounded-5 px-5" value="Kirim">
                  </form>
              
          </div>
      </div>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const members = ref([])
const objectives = ref([])
// const form = ref({
//   nama: '',
//   kategori : '',
//   tingkat : '',
//   jurusan : '',
//   kelas : '',
//   waktu : '',
//   keperluan: ''
// })

const nama = ref('')
const kategori = ref('')
const kelas = ref('')
const jurusan = ref('')
const tingkat = ref('')
const keperluan = ref('')
// const kelasLengkap = ref('')
const kirimData = async () => {
  // console.log(form.value);
  // kelasLengkap.value = `${tingkat.value} ${jurusan.value} ${kelas.value}`
  const { error } = await supabase.from('pengunjung').insert([{
    kategori: kategori.value,
    kelas: kelas.value,
    tingkat: tingkat.value,
    jurusan: jurusan.value,
    nama: nama.value,
    keperluan: keperluan.value
  }])
  if (error) throw error
  else navigateTo('/pengunjung/')
}
const getKeanggotaan = async () => {
  const { data, error } = await supabase.from('keanggotaan').select('*')
  if(data) members.value = data
}
const getKeperluan = async () => {
  const { data, error } = await supabase.from('keperluan').select('*')
  if(data) objectives.value = data

}
function resetKelas(e){
    if(e.target.value != '2'){
        kelas.value= ''
        tingkat.value= ''
        jurusan.value= ''
    }
}
onMounted(() => {
  getKeanggotaan()
  getKeperluan()
})

</script>

<style scoped>
.intro{
  height: 100vh;
  /* padding-bottom: 10%; */
}
.text-center{
  padding-top: 5%;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif ;
  font-size: 190%;
  color: rgb(255, 255, 255);
  text-align: center;
}

.btn{
  background-color: white;

  box-shadow: 2px 2px 2px #424242;
  color: black;
  
}
</style>
