<template>
    <div class="row">
        <div class="col">
            <h1 class="text-center my-3">DAFTAR KEHADIRAN </h1>
        </div>
    </div>
    <div class="row justify-content-center">
        <div class="col-11">
            <select @change="getSiswa" class="form-control form-control-lg form-select mb-3" style="background-color: #D9D9D9;">
                <option value="" disabled>Pilih Tingkat</option>
                <option v-for="k in kelas" :key="k.id" :value="k.id">{{ k.kelas }}</option>
            </select>

        </div>
    </div>
    <div class="row justify-content-center">
        <div class="col-11">
            <table class="table table-striped table-bordered">
                <thead>
                    <tr>
                        <th rowspan="2">Nama Siswa</th>
                        <th colspan="5">KETERANGAN</th>
                    </tr>
                    <tr>
                        <th>H</th>
                        <th>I</th>
                        <th>S</th>
                        <th>A</th>
                        <th>D</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(s, i) in siswa" :key="i">
                        <td>{{ s.nama }}</td>
                        
                        <td><input v-model="presensi[i]" type="radio" :name="`keterangan[${i}]`" value="H" checked></td>
                        <td><input type="radio" :name="`keterangan[${i}]`" value="I"></td>
                        <td><input type="radio" :name="`keterangan[${i}]`" value="S"></td>
                        <td><input type="radio" :name="`keterangan[${i}]`" value="A"></td>
                        <td><input type="radio" :name="`keterangan[${i}]`" value="D"></td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="col-2 ms-auto mb-3">
            <button type="submit" class=" btn btn-light btn-lg rounded-5 px-5" style=" text-decoration-color: #2E4D71;">KIRIM</button>
        </div>       
    </div>
    
</template> 


<script setup>
const client = useSupabaseClient()
const kelas = ref([])
const siswa = ref([])
const presensi = ref([])

async function getKelas() {
    const { data, error } = await client
        .from('kategori_kelas')
        .select()
    if(data) kelas.value = data
}

async function getSiswa(event) {
    let id_kelas = event.target.value
    const { data, error } = await client
        .from('siswa')
        .select()
        .eq('kelas', id_kelas)
    if(data) siswa.value = data
}


function kirimPresensi() {
    console.log(presensi.value)
}

onMounted(() => {
    getKelas()
})
</script>
