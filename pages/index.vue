<template>
 <div class="container-fluid">
    <div class="row justify-content-around align-items-center" style="height: 80vh;">
        <div class="col-sm-3">
            <div class="card rounded-3 bg4 shadow">
                <h2 class="card-title">Siswa</h2>
                <div class="card-body">
                </div>
            </div>
        </div>
        <div class="col-sm-3">
            <div class="card rounded-3 bg5 shadow">
                <h2 class="card-title">Presensi</h2>
                <div class="card-body">
                </div>
            </div>
        </div>
    </div>
 </div>   
</template>

<style scoped>
.card-body{
    height: 7rem;
}
.card {
    position: relative;
}
.card .card-title {
    position: relative;
    top: 10;
    left: 10px;
    font-size: 40px;
}

.bg4 {
    background-image: url("/assets/img/bg4.jpeg");
    background-size: 29rem;
    background-repeat: no-repeat;
    background-position: 15%;
}
.bg5 {
    background-image: url("/assets/img/bg5.jpeg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 2%;
}
</style>