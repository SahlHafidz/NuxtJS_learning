<template>
    <div class="hello">
        <h1 v-if="awesome">Alkademi Terbaik
        </h1>
        <h1 v-else>Belajar Pemrograman</h1>
        <div v-if="number > 0.5">
            Now you see me {{ number }}
        </div>
        <div v-else>
            Now you dont {{ number }}
        </div>
        <p v-if="angka === 0"> The number is 0</p>
        <p v-else-if="angka >= 0">The number is positive</p>
        <p v-else-if="angka < 0">The number is negative</p>
        <p v-else>Bukan termasuk angka</p>
        <div v-if="type === 'A'">A</div>
        <div v-else-if="type === 'B'">B</div>
        <div v-else-if="type === 'C'">C</div>
        <div v-else>Not A/B/C</div>
        <p v-if="kalimat.includes('pizza')">Teks tersebut mengandung kata 'pizza'</p>
        <p v-else-if="kalimat.includes('bakso')">Teks tersebut mengandung kata 'bakso'</p>
        <p v-else>Kata 'pizza' dan 'bakso' tidak ditemukan pada teks</p>
        <p v-if="ganteng || kaya">Makmur</p>
        <p v-else>Sejahtera</p>
        <p v-show="ok">Hello Show!</p>
        <p v-if="ok">Hello If!</p>
        <div :class="{ invisible: !value1}">Saya Terlihat</div>
        <div :class="{ invisible: !value2}">Tidak Terlihat</div>
        <div> Name: {{ kondisi == 1 ? 'Lulus' : 'Gagal' }} </div>
        <div class="dropdown">
  <a class="btn btn-secondary dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
    Dropdown link
  </a>

  <ul class="dropdown-menu">
    <li><a class="dropdown-item" href="#">Action</a></li>
    <li><a class="dropdown-item" href="#">Another action</a></li>
    <li><a class="dropdown-item" href="#">Something else here</a></li>
  </ul>
</div>
    </div>
</template>
<script>
export default {
    layout (contect) {
        return 'custom'
    },
    name: "HelloWolrd",
    data() {
        return {
            shopNumber: 12,
            awesome: true,
            number: Math.random(),
            angka: "10,10",
            type: "A",
            kalimat: 'Saya suka sekali makan bakso, mi ayam, siomay, dan Pizza',
            ganteng: 1,
            kaya: "A",
            ok: false,
            value1: true,
            value2: false,
            kondisi: 1
        }
    },
    computed: {
        count: function() {
            return 'The shop number is '+ this.shopNumber
        }
    }
}
</script>
<style scoped>
.invisible {
    visibility: hidden;
}
</style>