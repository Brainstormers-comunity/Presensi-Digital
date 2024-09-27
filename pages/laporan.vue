<template>
    <div class="row">
        <div class="col">
            <h1 class="text-center my-3"> LAPORAN RIWAYAT KEHADIRAN </h1> 
        </div>
     </div>
     <div class="row justify-content-center">
        <div class="col-11"> 
            <input type="text"class="form-control form-control-lg form-select mb-3"  placeholder="filter" style="width: 110rem;height:3rem;background-color: #D9D9D9; ">
        </div>
     </div>  
     <div class="row justify-content-center">
            <div class="col-11">
             <table class="table table-striped table-bordered">
                <thead>
                    <tr>
                        <th class="text-center" rowspan ="2">Tanggal</th>
                        <th class="text-center" rowspan="2">Kelas</th>
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
                        <td>XI TOI</td>
                        <td>33</td>
                        <td>30</td>
                        <td>1</td>
                        <td>1</td>
                        <td>1</td>
                        <td>0</td>
                    </tr>
                </thead>
             </table>
             <div class="col-1 ms-auto mb-3">
                <NuxtLink to="">
                    <button type="button" class="btn" style="background-color: #D9D9D9;">Kembali</button>
                </NuxtLink>
             </div>
         </div>
         </div>
</template>