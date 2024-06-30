# komputer
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistem Pakar Troubleshooting Komputer</title>
    <style>
        /* Tambahkan CSS di sini untuk styling */
    </style>
</head>
<body>
    <header>
        <h1>Sistem Pakar Troubleshooting Komputer</h1>
        <p>Diagnosa dan perbaiki masalah komputer Anda dengan mudah</p>
    </header>

    <nav>
        <ul>
            <li><a href="#home">Beranda</a></li>
            <li><a href="#diagnosis">Mulai Diagnosis</a></li>
            <li><a href="#about">Tentang</a></li>
        </ul>
    </nav>

    <main>
        <section id="home">
            <h2>Selamat Datang</h2>
            <p>Gunakan sistem pakar kami untuk mendiagnosis masalah komputer Anda.</p>
        </section>

        <section id="diagnosis">
            <h2>Mulai Diagnosis</h2>
            <form id="troubleshootForm">
                <label for="category">Pilih Kategori Masalah:</label>
                <select id="category" name="category">
                    <option value="">--Pilih Kategori--</option>
                    <option value="boot">Masalah Boot</option>
                    <option value="internet">Koneksi Internet</option>
                    <option value="audio">Masalah Audio</option>
                    <option value="display">Masalah Tampilan</option>
                </select>

                <div id="questions">
                    <!-- Pertanyaan akan dimuat secara dinamis berdasarkan kategori -->
                </div>

                <button type="submit">Diagnosa</button>
            </form>
        </section>

        <section id="result" style="display: none;">
            <h2>Hasil Diagnosis</h2>
            <div id="diagnosisResult"></div>
            <div id="solution"></div>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 Sistem Pakar Troubleshooting Komputer. Hak Cipta Dilindungi.</p>
    </footer>

    <script>
    
       const knowledgeBase = {
    boot: [
        { question: "Apakah komputer tidak menyala sama sekali?", id: "boot1" },
        { question: "Apakah Anda mendengar suara beep saat startup?", id: "boot2" },
        { question: "Apakah layar tetap hitam setelah komputer menyala?", id: "boot3" }
    ],
    internet: [
        { question: "Apakah ikon koneksi internet menunjukkan tidak ada koneksi?", id: "net1" },
        { question: "Apakah Anda dapat mengakses router?", id: "net2" },
        { question: "Apakah perangkat lain dapat terhubung ke internet?", id: "net3" }
    ],
    // Tambahkan kategori lain sesuai kebutuhan
};

const solutions = {
    boot: {
        "boot1-yes": "Periksa kabel power dan pastikan sumber listrik berfungsi.",
        "boot2-yes": "Dengarkan pola beep dan konsultasikan dengan manual motherboard.",
        "boot3-yes": "Periksa koneksi kabel monitor atau coba monitor lain jika tersedia.",
        "default": "Jika masalah berlanjut, pertimbangkan untuk menghubungi teknisi."
    },
    internet: {
        "net1-yes": "Periksa koneksi kabel ethernet atau pengaturan Wi-Fi.",
        "net2-no": "Reset router Anda dan tunggu beberapa menit.",
        "net3-yes": "Masalah mungkin pada perangkat Anda. Coba restart komputer.",
        "default": "Hubungi penyedia layanan internet Anda untuk bantuan lebih lanjut."
    },
    // Tambahkan solusi untuk kategori lain
};

document.addEventListener('DOMContentLoaded', () => {
    const categorySelect = document.getElementById('category');
    const questionsDiv = document.getElementById('questions');
    const troubleshootForm = document.getElementById('troubleshootForm');
    const resultSection = document.getElementById('result');
    const diagnosisResult = document.getElementById('diagnosisResult');
    const solutionDiv = document.getElementById('solution');

    categorySelect.addEventListener('change', loadQuestions);
    troubleshootForm.addEventListener('submit', processAnswers);
