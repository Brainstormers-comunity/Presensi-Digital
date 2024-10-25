<template>
    <div class="row">
        <div class="col">
            <h1 class="text-center my-3 judul"> LAPORAN RIWAYAT KEHADIRAN </h1> 
        </div>
     </div>
     <div class="row  justify-content-center">
        <input type="date" @change="getSchedule" style="width: 110rem; height:3rem;background-color: #D9D9D9;" class="rounded-3 my-3" >
        {{ schedule }}
    </div>
     <div class="row justify-content-center">
            <div class="col-11">
             <table class="table table-striped table-bordered">
                <thead>
                    <tr>
                        <th class="text-center" rowspan ="2">Tanggal</th>
                        <th class="text-center" rowspan="2">Tingkat</th>
                        <th class="text-center" rowspan="2">Jumlah Siswa</th>
                        <th class="text-center" colspan="5">KETERANGAN</th>
                    </tr>
                    <tr>
                        <th>H</th>
                        <th>I</th>
                        <th>S</th>
                        <th>A</th>
                        <th>D</th>
                    </tr>

                    <tr>
                        <td>25 SEPTEMBER 2024</td>
                        <td>X TOI</td>
                        <td>34</td>
                        <td>30</td>
                        <td>1</td>
                        <td>1</td>
                        <td>1</td>
                        <td>3</td>
                    </tr>

                    <tr>
                        <td>25 SEPTEMBER 2024</td>
                        <td>XI TOI</td>
                        <td>32</td>
                        <td>30</td>
                        <td>1</td>
                        <td>1</td>
                        <td>1</td>
                        <td>3</td>
                    </tr>

                    <tr>
                        <td>25 SEPTEMBER 2024</td>
                        <td>XII TOI</td>
                        <td>32</td>
                        <td>30</td>
                        <td>1</td>
                        <td>1</td>
                        <td>1</td>
                        <td>3</td>
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