
<template>
  <div class="modal fade" id="detailbukuModal" tabindex="-1" aria-labelledby="detailbukuModalLabel" :aria-hidden="true">                                                                           
    <div class="modal-dialog modal-dialog-centered modal-lg">
      <div class="modal-content">
        <div class="modal-header  text-center">
          <h3 class="modal-title" id="detailbukuModalLabel">Detail Buku</h3>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
              <div class="row">
                  <div class="col-md-3">
                      <img src="~/assets/img/Aboycalledocean.jpg" class="img-fluid">
                  </div>
                  <div class="col-md">
                      <ul class="list-group">
                          <li class="list-group-item"><strong>Judul Buku :</strong> A Boy Called Ocean</li>
                          <li class="list-group-item"><strong>Penulis :</strong> Chris Higgins</li>
                          <li class="list-group-item"><strong>Penerbit :</strong> PT Gramedia Pustaka Utama</li>
                          <li class="list-group-item"><strong>Tahun Terbit :</strong> 2019</li>
                          <li class="list-group-item"><strong>Sinopsis :</strong> Kai frustasi saat melihat Jen dekat dengan orang lain. Kai memutuskan untuk berselancar dan mengikuti arus sampai hatinya tenang. Tanpa sadar, ia sudah berada jauh dari pinggir pantai dan terdampar di tengah laut. Kai berusaha bertahan hidup, tapi keadaan yang dilaluinya semakin berat. Kelaparan, kedinginan dan ada hiu di dekatnya. Mampukah Kai bertahan dan kembali pulang? </li>
                          <li class="list-group-item"><strong>Kategori :</strong> Kesusastraan</li>
                          <li class="list-group-item"><strong>Rak :</strong> 813</li>
                      </ul>
                  </div>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn text-light" data-bs-dismiss="modal">Close</button>
        </div>
      </div>
    </div>
  </div>
  </template>
  
  <style scoped>
  button {
    background-color: #394367;
  }
  </style>
  
    