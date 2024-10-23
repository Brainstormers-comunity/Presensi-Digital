<template>
    <div class="row">
        <div class="col">
            <h1 class="text-center my-3">RIWAYAT KEHADIRAN </h1> 
        </div>
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
                    <tr>
                        <td>1</td>
                        <td>Gina</td>
                        <td>20 mei 2024</td>
                        <td>SAKIT</td>
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

definePageMeta({
  middleware: 'auth',
})
</script>