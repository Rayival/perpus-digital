<template>
  <div class="wrapper">
  <div class="content"></div>
      <div class="container-fluid">
              <form @submit.prevent="getBooks" class="row pt-5 d-flex justify-content-center">
                  <div class="col-lg-10">
                      <input v-model="keyword" type="search" class="form-control form-control-md rounded-5" name="cari-buku" id="cari-buku" placeholder="Mau baca apa hari ini?" autocomplete="off">
                  </div>
              </form>
              <div class="row my-3 d-flex justify-content-center ps-0">
                  <p class="col-5 m-0 pt-2 text-white" style="letter-spacing: 3px;">Menampilkan {{ books.length }} buku</p>
                  <p class="col-2 text-white m-0 text-end mt-2" style="letter-spacing: 3px;">kategori :</p>
                  <div class="col-3">
                      <select v-model="kategori" name="kategori" id="kategori" class="form-control form-control-sm rounded-5 form-select">
                          <option value="" disabled selected>Kategori?</option>
                          <option v-for="(kategori, i) in kategories" :key="i" :value="kategori.nama">{{ kategori.nama }}</option>
                      </select>
                  </div>
              </div>
          <div class="row">
              <div v-for="(book, i) in bookFiltered" :key="i" class="col">
                  <div class="col-lg-11 col-1 card cb">
                      <div class="card-body">
                          <NuxtLink :to="`/buku/${book.id}`" style="text-decoration:none">
                              <img :src="book.cover" class="cover border" alt="cover">
                          </NuxtLink>
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

<script setup>
const supabase = useSupabaseClient()

const books = ref([])
const kategories = ref([])
const keyword = ref('')
const kategori = ref('')

async function getBooks() {
    const {data, error} = await supabase.from('buku')
    .select(`*, kategori(*)`)
    .ilike('judul', `%${keyword.value}%`)
    if (error) throw error
    if (data) {
    books.value = data; 
        data.forEach(book => {
            const { data } = supabase.storage.from('cover').getPublicUrl(book.cover)
            if (data) {
                book.cover = data.publicUrl
            }
        })
    }
}

async function getKategori(){
    const{data, error} = await supabase.from('kategori_buku')
    .select('*')
    if(data) kategories.value = data
}

const bookFiltered = computed (() => {
    return books.value.filter((b) => {
        return (
            b.judul?.toLowerCase().includes(keyword.value?.toLowerCase()) ||
            b.kategori?.nama.toLowerCase().includes(kategori.value?.toLowerCase())
        )
    })
}) 


onMounted(() => {
    getBooks()
    getKategori()
})
</script>

<style scoped>
.content {
  background-image: url('@/assets/bg-home-cari-buku.jpg');
  background-size: cover;
  width: 100%;
  height: 100%;
  bottom: 0;
  top: 0;
  left: 0;
  right: 0;
  position: fixed;
  z-index: -1;

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
.cb {
    background-color: #fffeee83;
    border: 0;
    height: 250px;
    width: 180px;
    margin: 5px 5px;
}
</style>
