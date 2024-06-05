<template>
    <div class="wrapper">
        <div class="content"></div>
        <div class="container-fluid">
            <div class="row d-flex justify-content-center align-content-center align-items-center" style="padding-top: 190px;">
                <div class="col-lg-3 col-md-4 col-6 mt-5">
                    <img :src="buku?.cover" class="cover border" alt="cover" style="width: 200px;">
                </div>
                <div class="col-lg-9 col-md-8 col-8 card rounded-5 text-dark text-center mt-5" style="width: 30rem; height: 20rem; padding-top: 50px;">
                    <div class="row">
                        <h1>{{ buku?.judul }}</h1>
                    </div>
                    <div class="row">
                        <h4>Pengarang : {{ buku?.penulis }}</h4>
                        <h4>Penerbit : {{ buku?.penerbit }}</h4>
                        <h4>Tahun Terbit : {{ buku?.tahun_terbit }}</h4>
                        <h4>Kategori : {{ buku?.kategori_buku?.nama }}</h4>
                    </div>
                    <div class="row">
                        <h6>{{ buku?.deskripsi }}.</h6>
                    </div>
                </div>
            </div>
            <div class="row float-end pe-5 mt-5">
                <NuxtLink to="/buku/" class="btn btn-lg rounded-5" style="width: 10rem;">Kembali</NuxtLink>
            </div>
        </div>
    </div>
    </template>
    
    <script setup>
    const supabase = useSupabaseClient()
    
    const route = useRoute()
    const buku = ref()
    
    const getBookById = async () => {
    const { data, error } = await supabase.from('buku')
    .select(`*, kategori_buku(*)`)
    .eq('id', route.params.id)
    .maybeSingle()
    if (error) throw error
    if (data) {
        const { data: url } = supabase.storage.from('cover').getPublicUrl(data.cover)
        if (url) {
            data.cover = url.publicUrl
        }
        buku.value = data
    }
    }
    
    onMounted(() => {
        getBookById()
    })
    </script>
    
    <style scoped>
.content {
    background-color: #23323D;
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
    .btn  {
        background-color: #fffeee;
    }
    
    .form-control{
        background-color: #fffeee;
    }
    
    img {
        width: 150px;
    }
    
    .cb {
        background-color: #fffeee83;
        border: 0;
        height: 250px;
        width: 180px;
        margin: 5px 5px;
    }
    </style>
