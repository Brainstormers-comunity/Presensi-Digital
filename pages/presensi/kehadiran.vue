<template>
    <div class="row">
        <div class="col">
            <h1 class="text-center my-3">DAFTAR KEHADIRAN </h1>
            <select @change="pilihKelas">
                <option value="">Pilih Tingkat</option>
                <option v-for="k in kelas" :key="k.id" :value="k.id">{{ k.kelas }}</option>
                
            </select>
            
            <ul v-for="s in siswa" :key="s.id">
                <li>{{ s.nama }}</li>
            </ul>
        </div>
    </div>
    
</template>

<script setup>
const client = useSupabaseClient()

const kelas = ref([])
const siswa = ref([])

async function getKelas() {
    let { data, error } = await client
        .from('kategori_kelas')
        .select()
    if(data) kelas.value = data
}

async function pilihKelas(event) {
    let id_kelas = event.target.value
    let { data, error } = await client
        .from('siswa')
        .select(`*, kelas(kelas)`)
        .eq('kelas', id_kelas)
    if(data) siswa.value = data
}

onMounted(()=>{
    getKelas()
})
</script>