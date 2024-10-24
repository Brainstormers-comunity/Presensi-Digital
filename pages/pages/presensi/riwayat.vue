<template>
    <div class="row">
        <div class="col">
            <h1 class="text-center my-5">RIWAYAT KEHADIRAN </h1> 
        </div>
    </div>
    <div class="row justify-content-center" style="width: 100rem; height:3rem;background-color: #D9D9D9; ">
        <input type="date" @change="getSchedule">
        {{ schedule }}
    </div>
    <div class="row justify-content-center">
        <div class="col-11">
            <table class="table table-striped table-bordered">
                <thead>
                    <tr>
                        <th class="text-center">No</th>
                        <th class="text-center">Nama</th>
                        <th class="text-center">Tanggal</th>
                        <th class="text-center">Keterangan</th>
                    </tr>
                    <tr v-for="(visitor,i) in students" :key="i">
                            <td>{{ i+1 }}.</td>
                            <td>{{ visitor?.id_siswa.nama }}</td>
                            <td>{{ visitor.tgl }}</td>
                            <td>{{ visitor.keterangan }}</td>
                        </tr>
                </thead>
            </table>
            <div class="col-1 ms-auto mb-3">
                <NuxtLink to="/">
                    <button type="button" class="btn" style="background-color: #D9D9D9;">Kembali</button>
                </NuxtLink>
            </div>
        </div>
            
    </div>

</template>

<script setup>
const supabase = useSupabaseClient()
const date = ref('')
const students = ref([])

const getSchedule = async (event) => {
    date.value = event.target.value
    const { data, error } = await supabase
    .from('daftar_kehadiran')
    .select(`*, id_siswa(nama)`);
    //.eq('tgl', date.value)
    if(data) students.value = data
//     if (error) throw error
//     visitor.value = data
}
onMounted (() => {
    getSchedule();
})
</script>