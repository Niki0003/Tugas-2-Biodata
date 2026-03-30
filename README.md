<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>UTS Platform</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>

<!-- NAVBAR -->
<nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
  <div class="container">
    <a class="navbar-brand">My Profile</a>
    <button class="navbar-toggler" data-bs-toggle="collapse" data-bs-target="#nav">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="nav">
      <ul class="navbar-nav ms-auto">
        <li class="nav-item"><a class="nav-link" href="#beranda">Beranda</a></li>
        <li class="nav-item"><a class="nav-link" href="#tentang">Tentang</a></li>
        <li class="nav-item"><a class="nav-link" href="#galeri">Galeri</a></li>
        <li class="nav-item"><a class="nav-link" href="#pendidikan">Pendidikan</a></li>
        <li class="nav-item"><a class="nav-link" href="#tugas">Tugas</a></li>
      </ul>
    </div>
  </div>
</nav>

<div style="margin-top:80px"></div>

<!-- BERANDA -->
<section id="beranda" class="container text-center">
    <div class="p-5 bg-primary text-white rounded">
        <img src="https://via.placeholder.com/150" class="rounded-circle mb-3">
        <h2>Nama Kamu</h2>
        <p>NIM Kamu</p>
    </div>
</section>

<!-- TENTANG -->
<section id="tentang" class="container mt-5">
    <h2 class="text-center">Tentang</h2>
    <div class="row mt-3">
        <div class="col-md-6">
            <p>Lorem ipsum dolor sit amet...</p>
        </div>
        <div class="col-md-6">
            <p>Lorem ipsum dolor sit amet...</p>
        </div>
    </div>
</section>

<!-- GALERI -->
<section id="galeri" class="container mt-5">
    <h2 class="text-center">Galeri</h2>
    <div class="row">
        <div class="col-md-4">
            <div class="card">
                <img src="https://via.placeholder.com/300" class="card-img-top">
                <div class="card-body">Foto 1</div>
            </div>
        </div>
    </div>
</section>

<!-- PENDIDIKAN -->
<section id="pendidikan" class="container mt-5">
    <h2 class="text-center">Pendidikan</h2>
    <table class="table table-bordered">
        <tr>
            <th>Tahun</th>
            <th>Sekolah</th>
            <th>Alamat</th>
        </tr>
        <tr>
            <td>2020</td>
            <td>SMA</td>
            <td>Yogyakarta</td>
        </tr>
    </table>
</section>

<!-- TUGAS -->
<section id="tugas" class="container mt-5">
<h2 class="text-center">Tugas</h2>

<div class="card p-3">
    <input id="nama" class="form-control mb-2" placeholder="Nama">
    <input id="alamat" class="form-control mb-2" placeholder="Alamat">
    <input id="email" type="email" class="form-control mb-2" placeholder="Email">
    <input id="jmlBahasa" type="number" class="form-control mb-2" placeholder="Jumlah Bahasa">
    <input id="jmlHobi" type="number" class="form-control mb-2" placeholder="Jumlah Hobi">
    <button onclick="step1()" class="btn btn-primary">OK</button>
</div>

<div id="step2" class="mt-3"></div>
<div id="step3" class="mt-3"></div>
<div id="hasil" class="mt-3 alert alert-success"></div>

</section>

<script>
let bahasa = [], hobi = [];

function step1(){
    let jmlB = document.getElementById("jmlBahasa").value;
    let jmlH = document.getElementById("jmlHobi").value;

    let html = "<h4>Input Bahasa & Hobi</h4>";

    for(let i=1;i<=jmlB;i++){
        html += `<input id="b${i}" class="form-control mb-2" placeholder="Bahasa ${i}">`;
    }

    for(let i=1;i<=jmlH;i++){
        html += `<input id="h${i}" class="form-control mb-2" placeholder="Hobi ${i}">`;
    }

    html += `<button onclick="step2()" class="btn btn-success">OK</button>`;

    document.getElementById("step2").innerHTML = html;
}

function step2(){
    let jmlB = document.getElementById("jmlBahasa").value;
    let jmlH = document.getElementById("jmlHobi").value;

    bahasa = [];
    hobi = [];

    let html = "<h4>Pilih Bahasa & Hobi</h4>";

    for(let i=1;i<=jmlB;i++){
        let val = document.getElementById("b"+i).value;
        bahasa.push(val);
        html += `<input type="radio" name="pilihBahasa" value="${val}"> ${val}<br>`;
    }

    html += "<br>";

    for(let i=1;i<=jmlH;i++){
        let val = document.getElementById("h"+i).value;
        hobi.push(val);
        html += `<input type="checkbox" name="pilihHobi" value="${val}"> ${val}<br>`;
    }

    html += `<button onclick="hasil()" class="btn btn-warning mt-2">OK</button>`;

    document.getElementById("step3").innerHTML = html;
}

function hasil(){
    let nama = document.getElementById("nama").value;
    let alamat = document.getElementById("alamat").value;
    let email = document.getElementById("email").value;

    let pilihB = document.querySelector('input[name="pilihBahasa"]:checked').value;

    let pilihH = [];
    document.querySelectorAll('input[name="pilihHobi"]:checked').forEach(e=>{
        pilihH.push(e.value);
    });

    document.getElementById("hasil").innerHTML =
    `Hallo, nama saya ${nama}, alamat ${alamat}, email ${email}. 
    Saya mempunyai ${bahasa.length} bahasa yaitu ${bahasa.join(", ")} 
    dan saya memilih ${pilihB}. 
    Saya juga mempunyai ${hobi.length} hobi yaitu ${hobi.join(", ")} 
    dan saya memilih ${pilihH.join(", ")}`;
}
</script>

</body>
</html>
