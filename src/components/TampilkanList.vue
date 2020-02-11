<template>
  <div id="tampilkanList">
      <div class="judulTabel">
          <!-- <h2>Daftar List Tugas</h2> -->
          <div class="jumbotron">
            <h1 class="display-4">Assignment List</h1>
            <p class="lead"><i>"Kemenangan itu manja, harus direbut dengan perjuangan yang keras"</i></p>
            <p class="lead">dr Gamal Albinsaid, M.Biomed.</p>
            <hr class="my-4">
            <a class="btn btn-primary btn-lg" href="#mulai" role="button">Get Started</a>
        </div>
      </div>
      <br>
      <div class="btnTambah" id="mulai">
          <br>
          <div class="container">
          <button class="btn btn-success" mt-5 mb-5 @click="tambahkan">Tambahkan Tugas</button>
          <!-- <button @click="showAlert">Hello world</button> -->
          <!-- <button @click="destroy(statuses.id)" class="btn btn-danger btn-flat btn-sm"> <i class="fa fa-remove"></i> </button> -->
          </div>

    <div class="inputan">
        <div class="card mb-3" v-for="(datas,index) in allData" :key="index">
          <div class="card-body">
              <span class="float-right" style="cursor: pointer">
                  <button class="btn btn-danger" @click="hapusi(index)">hapus</button>
              </span>

              <h3 class="card-title">Tugas ke-{{index+1}}</h3>

              <div class="employee-form">
                  <input type="text" class="form-control mb-2" placeholder="Nama Tugas" v-model="datas.namaTugas">
                  <input type="text" class="form-control mb-2" placeholder="Mata Kuliah" v-model="datas.mataKuliah">
                  <input type="date" class="form-control mb-2" placeholder="Deadline" v-model="datas.deadline">
                  <textarea class="form-control" cols="30" rows="10" placeholder="Deskripsi" v-model="datas.deskripsi"></textarea>
              </div>
              <br>
              <p>
                    <a class="btn btn-primary" data-toggle="collapse" href="#collapseExample" role="button" aria-expanded="false" aria-controls="collapseExample">
                        Detail
                    </a>
                    </p>

                        <div class="collapse" id="collapseExample">
                    <div class="card card-body">
                        <h3>Detail Tugas ke-{{index+1}}</h3>
                        <hr>
                        <div class="detail">
                        <h4><b>Nama Tugas  : {{datas.namaTugas}}</b></h4>
                        <h4><b>Mata Kuliah : {{datas.mataKuliah}}</b></h4>
                        <h4><b>Deadline    : {{datas.deadline}}</b></h4>
                        <h4><b>Deskripsi   : {{datas.deskripsi}}</b></h4>
                        </div>
                    </div>
                    </div>
          </div>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import LembarTengah from './components/HelloWorld.vue'
export default {
  name: 'tampilkanList',
  components: {

  },
  data () {
    return {
      allData: [
        {
          namaTugas: '',
          mataKuliah: '',
          deadline: '',
          deskripsi: ''
        }
      ]
    }
  },
  methods: {
    tambahkan () {
      this.allData.push({
        namaTugas: '',
        mataKuliah: '',
        deadline: '',
        deskripsi: ''
      })
      this.$swal('Tugas Berhasil Ditambahkan!')
    },
    hapus (index) {
      this.allData.splice(index, 1)
      this.$swal('Tugas Berhasil Dihapus!')
    },
    showAlert () {
      this.$swal('Hello Vue world!!!')
    },
    hapusi (index) {
      this.$swal.fire({
        title: 'Are you sure?',
        text: "You won't be able to revert this!",
        icon: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        confirmButtonText: 'Yes, delete it!'
      }).then((result) => {
        if (result.value) {
          this.allData.splice(index, 1)
          this.$swal.fire(
            'Deleted!',
            'Your file has been deleted.',
            'success'
          )
        }
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center ;
  color: #2c3e50;
}
.inputan{
    text-align: center;
    margin-left: 100px;
    margin-right: 100px;
    margin-top: 20px;
    background-color: rgb(2, 2, 2);
}
.judulTabel{
    color: black;
    align-content: center;
}
div.btnTambah{
    position: -webkit-sticky;
  position: sticky;
  top: 0;
  padding: 5px;
  background-color: #2c3e50;
  border: 2px solid #4CAF50;
}
.detail{
    text-align: left;
    background: rgb(0, 191, 255);
    padding: 10px;
}
.cd-popup {
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.3s 0s, visibility 0s 0.3s;
}

.cd-popup.is-visible {
  opacity: 1;
  visibility: visible;
  transition: opacity 0.3s 0s, visibility 0s 0s;
}

.cd-popup-container {
  transform: translateY(-40px);
  transition-property: transform;
  transition-duration: 0.3s;
}

.is-visible .cd-popup-container {
  transform: translateY(0);
}
</style>
