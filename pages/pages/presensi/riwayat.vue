<template>
    <div class="row">
        <div class="col">
            <h1 class="text-center my-5">RIWAYAT KEHADIRAN </h1> 
        </div>
    </div>
    <div class="row">
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
                    <tr v-for="(visitor,i) in visitors" :key="i">
                            <td>{{ i+1 }}.</td>
                            <td>{{ visitors.siswa }}</td>
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
const visitors = ref([])

const getSchedule = async (event) => {
    date.value = event.target.value
    const { data, error } = await supabase
    .from('daftar_kehadiran')
    .select();
    //.eq('tgl', date.value)
    if(data) visitors.value=data
//     if (error) throw error
//     visitor.value = data
}
onMounted (() => {
    getSchedule();
})
</script>