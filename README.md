<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Happy Birthday My Fav Person! ❤️</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
        }

        html, body {
            width: 100%;
            height: 100%;
            /* Mengunci layar agar tidak bisa goyang/geser ke kanan-kiri */
            overflow-x: hidden; 
        }

        body {
            background: linear-gradient(to bottom, #ffe3e3, #fbc2eb);
            color: #4a4a4a;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            min-height: 100vh;
            position: relative;
        }

        /* Animasi Hati Berterbangan - Diperbaiki agar tidak merusak lebar layar */
        .heart {
            position: absolute;
            color: #ff6b81;
            font-size: 20px;
            animation: floatUp 6s linear infinite;
            opacity: 0.6;
            bottom: -50px;
            z-index: 0;
            pointer-events: none;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) translateX(0) rotate(0deg);
                opacity: 0.7;
            }
            100% {
                transform: translateY(-110vh) translateX(30px) rotate(360deg);
                opacity: 0;
            }
        }

        .container {
            max-width: 600px;
            width: 100%;
            background: rgba(255, 255, 255, 0.85);
            padding: 25px 20px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            text-align: center;
            backdrop-filter: blur(10px);
            margin-top: 10px;
            margin-bottom: 30px;
            z-index: 2; /* Berada di atas efek hati */
            position: relative;
        }

        h1 {
            color: #ff6b81;
            margin-bottom: 10px;
            font-size: 1.8rem;
        }

        p.subtitle {
            font-size: 1rem;
            color: #777;
            margin-bottom: 20px;
            min-height: 45px;
            line-height: 1.4;
        }

        /* Countdown Style */
        .countdown {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin: 20px 0;
        }

        .time-box {
            background: #ff6b81;
            color: white;
            padding: 8px 10px;
            border-radius: 10px;
            font-weight: bold;
            min-width: 65px;
            font-size: 0.8rem;
            box-shadow: 0 4px 10px rgba(255, 107, 129, 0.3);
        }

        .time-box span {
            display: block;
            font-size: 1.3rem;
        }

        /* Foto Style dengan Efek Denyut */
        .photo-frame {
            width: 160px;
            height: 160px;
            border-radius: 50%;
            border: 5px solid white;
            overflow: hidden;
            margin: 0 auto 15px auto;
            box-shadow: 0 5px 15px rgba(0,0,0,0.15);
            animation: pulse 3s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.03); box-shadow: 0 5px 25px rgba(255, 107, 129, 0.4); }
            100% { transform: scale(1); }
        }

        .photo-frame img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        /* Surat/Pesan Style */
        .letter-box {
            background: #ffffff;
            border: 2px dashed #ff6b81;
            padding: 15px;
            border-radius: 15px;
            margin-top: 20px;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .letter-box:hover {
            transform: scale(1.02);
        }

        .hidden-message {
            display: none;
            margin-top: 15px;
            line-height: 1.6;
            color: #4a4a4a;
            text-align: left;
            border-top: 1px solid #eee;
            padding-top: 15px;
            font-size: 0.95rem;
            max-height: 400px; /* Batasi tinggi maksimal agar tidak bablas ke bawah */
            overflow-y: auto;  /* Jika teks terlalu panjang, bisa di-scroll di dalam kotak surat */
        }

        /* Musik & Tombol Style */
        .btn-music {
            background-color: #ff6b81;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 25px;
            font-size: 1rem;
            cursor: pointer;
            margin-top: 20px;
            transition: 0.3s;
            box-shadow: 0 4px 15px rgba(255, 107, 129, 0.2);
            position: relative;
            z-index: 3;
        }

        .btn-music:hover {
            background-color: #ff4757;
        }
    </style>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
</head>
<body>

    <div class="container">
        <!-- Foto Pacar -->
        <div class="photo-frame">
            <img src="https://cdn.phototourl.com/free/2026-06-06-e059cb1f-eb07-4be3-bfdb-230d819c19e2.jpg" alt="Foto Pacar" id="pacar-foto">
        </div>

        <h1>Happy Birthday My Fav Person! ❤️</h1>
        
        <!-- Subtitle dengan Teks Otomatis -->
        <p class="subtitle" id="typing-text"></p>

        <!-- Countdown -->
        <div class="countdown">
            <div class="time-box"><span id="days">00</span>Hari</div>
            <div class="time-box"><span id="hours">00</span>Jam</div>
            <div class="time-box"><span id="minutes">00</span>Menit</div>
            <div class="time-box"><span id="seconds">00</span>Detik</div>
        </div>

        <!-- Surat Interaktif -->
        <div class="letter-box" onclick="bukaSurat()">
            <h3 style="color: #ff6b81; font-size: 1.1rem;">✉️ Klik untuk membuka surat dari akuuu🫶🏻...</h3>
            <div id="pesan-rahasia" class="hidden-message">
                <p>Haii Zaraaaaaa,</p><br>
                <p>Selamat ulang tahun yaaa zaraaaaa! dahhh 21 tahunn jugaaa nihhhh. Di hari yang indah ini, akuu cuma mau bilang terima kasih sudah hadir dan mewarnai hari-harikuu. Aku bersyukur banget yangg akhirnyaa sekarangg bisa dipertemukann kembalii sama kamuu zaraaaaa. Kadang sampe sekarang akuu sendiri masih mikir sii, kenapaa bisaa ujung-ujungnyaa bisaa ketemuu samaa kamuu lagii yaaa zaraaaa?padahal duluu kekk akuu ngiranyaa setelahh kitaa dahh gadaaa hubungann apaa-apaa lagii yaaa yaudaaa akuu mikirrnya kitaa nggaa bakalann ketemuu dalam artian bisaa dekett lagii, bahkann sedeket sekarangg. Kadang sampee sekarangg punn akuuu masihh nggaa percayaa, akuuu masihh tidaa ekspek bisaa dekett samaa zaraaa lagii, dann yapp emangg sepertinyaa Tuhan sudah ngasihh akuu lampu hijau (maybe) yangg dimanaa emangg akuu yang ditakdirkan sama kamu zaraaaa (wkwkwkwkwkw akuuu lagii npd bangett nihh) dann yangg pastii tuhan jugaa tauu manaa yang terbaik bagi seorang hambanya hehehehehe dann mungkinn ituu jugaa yangg menjadikann zaraaaa jawabann darii semuaa do'a-do'a kuu yangg selamaa inii udahh akuu panjatkan ke Tuhan, anjayyy wkwkwkwkwkw.</p><br>
                <p>Ohh iyaaaa sampee kelupaann zaraaaa gara-gara keasyikan ngetik, semogaa di usia zaraaaa yang baru ini yang semakin tuaa (wkwkwkwkwkwkw bercandaa, masih mudaa kokkk zaraaaa), zaraaaaa makin bahagiaa, sehat selaluu, dilancarkann rezekinyaa dann semuaa urusannyaa, dikuranginn cueknyaa apalagii kaloo pass badmood atauu marahh hehe (bolehh kokk badmood, marahh ke akuuu tapii akuu jangann dicuekinn yaaa🫶🏻), dan semuaa impiann zaraaaa satu per satu bisa tercapai dann yangg pastii bisaa membanggakann orang tuaa zaraaa nantinyaa, aamiin. Akuu akan selalu berusahaa ada di sini kokk buatt dukung zaraaaa, nemeninn zaraaaa, semuanyaa pokoknyaa buatt zaraaaaa kapann punn dann dimanaa punn zaraaaa membutuhkann kuuu. 💕</p><br>
                <p>Maaf yaaaa zaraaaa mungkinn akuuu masihh belumm bisaa sepenuhnyaa ngertiin zaraaaa, akuu masihh belajarr jugaa buatt bisaa ngertiin zaraaa sepenuhnyaa. Dan akuuu mintaa maaff jugaa yaaa zaraaaa akuu kadangg masihh nggaa dengerinn zaraaaa, bukann nggaa dengerin zaraaa sii tapii belumm sepenuhnyaa jugaa ngelakuinn apaa yangg zaraaa suruhh kekk nguranginn vape, ngga tidurr malem-malem dann masihh banyakk lagii. </p><br>
                <p>Terimakasihh banyakk yaaa zaraaaa, dengann hadirnyaa zaraaa di kehidupankuu, zaraaaa dahh banyakk bangett ngasihh perubahann ke kehidupankuu, zaraaaa sudaa bawaa motivasii dann semangatt jugaa buatt akuuu, zaraaa dahh bawaa banyakk kebahagiann jugaa yangg pastinyaa buatt akuuu, dann masihh banyakk lagii yangg lainnyaa. Terima kasihh banyakkk yaaa zaraaaa🫶🏻 </p><br>
                <p><i>With love,<br>UQII</i></p>
            </div>
        </div>

        <!-- Tombol Musik -->
        <audio id="bg-music" src="https://preliminary-harlequin-i632odai.edgeone.app/ssstik.io_1780779742906.mp3" loop></audio>
        <button class="btn-music" onclick="putarMusik()">🎵 Putar Musik</button>
    </div>

    <script>
        // 1. KODE TEKS OTOMATIS (Typewriter)
        const txt = "Hari spesial untuk orang yang paling spesial dalam hidupku. 💕";
        let i = 0;
        function typeWriter() {
            if (i < txt.length) {
                document.getElementById("typing-text").innerHTML += txt.charAt(i);
                i++;
                setTimeout(typeWriter, 80);
            }
        }
        window.onload = typeWriter;

        // 2. KODE TABURAN HATI (Floating Hearts) - Batasan area agar aman dari goyang
        function createHeart() {
            const heart = document.createElement("div");
            heart.classList.add("heart");
            
            const heartIcons = ["❤️", "💖", "💝", "💕", "🫶]"];
            heart.innerText = heartIcons[Math.floor(Math.random() * heartIcons.length)];
            
            // Batasi agar hati hanya muncul maksimal 90% lebar layar agar tidak memicu scroll kesamping
            heart.style.left = Math.random() * 90 + "vw"; 
            heart.style.animationDuration = Math.random() * 3 + 4 + "s";
            heart.style.fontSize = Math.random() * 10 + 15 + "px";
            
            document.body.appendChild(heart);
            
            setTimeout(() => {
                heart.remove();
            }, 6000);
        }
        setInterval(createHeart, 500);

        // 3. PENGATURAN TANGGAL ULANG TAHUN ZARA
        const tanggalUltah = new Date("June 07, 2026 18:50:00").getTime();

        const hitungMundur = setInterval(function() {
            const sekarang = new Date().getTime();
            const selisih = tanggalUltah - sekarang;

            const hari = Math.floor(selisih / (1000 * 60 * 60 * 24));
            const jam = Math.floor((selisih % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const menit = Math.floor((selisih % (1000 * 60 * 60)) / (1000 * 60));
            const detik = Math.floor((selisih % (1000 * 60)) / 1000);

            if (selisih > 0) {
                document.getElementById("days").innerHTML = hari < 10 ? "0" + hari : hari;
                document.getElementById("hours").innerHTML = jam < 10 ? "0" + jam : jam;
                document.getElementById("minutes").innerHTML = menit < 10 ? "0" + menit : menit;
                document.getElementById("seconds").innerHTML = detik < 10 ? "0" + detik : detik;
            } else {
                clearInterval(hitungMundur);
                document.getElementById("days").innerHTML = "00";
                document.getElementById("hours").innerHTML = "00";
                document.getElementById("minutes").innerHTML = "00";
                document.getElementById("seconds").innerHTML = "00";
                document.querySelector(".countdown").innerHTML = "<h2 style='color:#ff6b81; margin: 15px 0;'>🎉 HAPPY BIRTHDAY ZARAAAAA! 🎉</h2>";
            }
        }, 1000);

        // 4. FUNGSI BUKA SURAT (Proteksi Waktu)
        function bukaSurat() {
            const sekarang = new Date().getTime();
            const pesan = document.getElementById("pesan-rahasia");

            if (sekarang < tanggalUltah) {
                alert("Eitss, belum hari ulang tahunmuu zaraaaaa! 😜 Suratnya masih dikunci yaa, tunggu sampai tanggal 5 Juli baru bisa dibuka! ❤️");
            } else {
                if (pesan.style.display === "block") {
                    pesan.style.display = "none";
                } else {
                    pesan.style.display = "block";
                }
            }
        }

        // 5. FUNGSI PUTAR MUSIK
        function putarMusik() {
            const musik = document.getElementById("bg-music");
            const tombol = document.querySelector(".btn-music");
            if (musik.paused) {
                musik.play();
                tombol.innerHTML = "⏸️ Jeda Musik";
            } else {
                musik.pause();
                tombol.innerHTML = "🎵 Putar Musik";
            }
        }
    </script>
</body>
</html>
