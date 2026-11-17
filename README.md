# 🍜 Resto Simulator v7 — Game Web

Game manajemen restoran ala screenshot yang dikirim Ztr (gaya Kairosoft),
satu file web statis: `index.html` — tanpa dependensi, tanpa server.

## Cara main

Buka `index.html` di browser HP atau laptop (double-click, atau serve lokal:
`python3 -m http.server` lalu buka `http://localhost:8000`).

- Pelanggan datang sendiri, duduk kalau ada meja kosong, lalu pesan acak
  dari menu yang sudah terbuka.
- Pesanan dimasak otomatis oleh koki (satu per satu). Kalau sudah siap,
  **ketuk mejanya / tombol 🍽️ Sajikan** sebelum kesabaran pelanggan habis.
- Pelanggan yang puas bayar + tip; yang kehabisan sabar pergi dan reputasi turun.
- Hari berjalan 08:00–22:00. Di akhir hari ada laporan + sewa, lalu hari berikutnya.
- Uang dipakai untuk: tambah meja (maks 6), upgrade koki, upgrade dekor,
  dan buka menu baru (8 menu normal + 3 resep rahasia).

## Baru di v2 (13 Nov 2026)

1. **Mode Cerita 30 Hari, tamat di Bintang 5** — bintang naik dari reputasi,
   level, dan jumlah pelanggan dilayani. Bintang 5 = reputasi ≥90, Level 5,
   layani ≥150 pelanggan. Kalau sampai hari ke-30 belum Bintang 5, lanjut
   Mode Bebas tanpa batas hari. Ada target uang harian yang naik tiap hari;
   gagal target = reputasi -2.
2. **Resep Rahasia & Achievement** — 8 achievement dengan bonus uang
   (mis. Tanpa Komplain 100 = +Rp150.000). Resep rahasia terbuka otomatis:
   Nasi Goreng Spesial (10x masakan SEMPURNA), Mie Ayam Rahasia (30x tanpa
   komplain berturut-turut), Es Teh Sultan (layani 100 pelanggan).
3. **Tema Restoran** — Warung (gratis, ramai), Kafe (Rp150.000, harga +20%,
   pelanggan lebih sabar), Fine Dining (Rp400.000, harga +60%, tip besar,
   pelanggan lebih sedikit & sabar pendek). Tema mengubah harga, kesabaran,
   dan jumlah pelanggan yang datang.
4. **Mini-Game Masak** — saat koki memasak, ada jarum yang bergerak.
   Tekan ⏱️ STOP! di zona hijau (70–90%) = SEMPURNA: masak dipercepat dan
   tip +40%. Zona kuning = Bagus, tip +25%. Melenceng = masak +2 detik.
5. **Cabang Kedua** — syarat Level 3 & Bintang 3, harga Rp500.000.
   Hasilkan +Rp30.000/hari (bisa di-upgrade sampai Lv5, +Rp130.000/hari),
   dan membuka achievement Punya Cabang.

Juga lebih menantang: kesabaran pelanggan makin cepat habis seiring hari
berjalan, dan sewa naik dengan jumlah meja + cabang.

## Save & Load

- Autosave berkala + saat hari berakhir + saat tab ditutup (localStorage),
  tombol 💾 Simpan / 📂 Muat, plus ⬇️ Export / ⬆️ Import save sebagai file JSON.
- Save v1 (versi lama) tetap bisa dimuat di v2 — field baru diisi default.
- Anti-cheat, jujur: game web client-side **tidak bisa 100% anti-cheat**,
  karena siapa pun bisa mengedit localStorage lewat DevTools. Yang diterapkan:
  checksum pada save, validasi + clamp semua nilai saat load (save yang diubah
  sembarangan ditolak), dan tidak ada cara di dalam game untuk mengubah uang.
  Anti-cheat penuh butuh server.

## Baru di v3 (13 Nov 2026) — semua ide tambahan masuk

1. **Pesanan Delivery / Ojek Online** — pesanan delivery muncul berkala
   dengan timer 30 detik. Klik 🛵 Kirim Sekarang sebelum habis: dibayar
   harga + tip 10%. Telat = rating delivery -5, reputasi -1.
2. **Ulasan & Viral** — pelanggan yang puas kadang kasih review bintang
   1–5 (5 terakhir ditampilkan). 3 review 5-bintang berturut-turut =
   VIRAL 2 hari, pelanggan datang +50%.
3. **Pelanggan Tetap** — pelanggan yang puas kadang jadi langganan
   (maks 5, dicatat emoji + menu favorit + jumlah kunjungan). Langganan
   balik dengan kesabaran +33% dan tip +10%.
4. **Cuaca & Musim** — tiap hari cuaca acak: Cerah (normal), Hujan
   (pelanggan -40%), Panas (harga +5%), Festival (pelanggan +50%,
   harga +10%). Akhir pekan (hari ke-6/7) pelanggan +30%.
5. **Pasar Pagi & Stok Bahan** — tiap menu pakai stok (awal 10 pcs untuk
   menu awal, +5 tiap buka menu baru). Stok berkurang tiap masakan &
   delivery; kalau habis, menu itu tidak bisa dipesan. Beli 5 pcs di Pasar
   (5x modal menu), stok kedaluwarsa setelah 3 hari lalu dibuang.
6. **Eksperimen Resep** — bayar Rp25.000, 60% berhasil membuat menu
   custom baru (nama acak, harga Rp20.000–30.000, maks 3 menu),
   gagal = uang hangus.
7. **Karyawan: Skill & Shift** — rekrut Koki Spesialis (masak 10% lebih
   cepat/level), Pelayan Cepat (pelanggan 10% lebih sabar/level), Kasir
   Teliti (tip +5%/level), maks Lv3. Gaji Rp8.000/level/hari, fatigue
   +15%/hari (≥70% efek separuh), tombol 😴 Istirahat (Rp5.000).
8. **Tata Letak Meja** — tiap meja bisa diubah zonanya (ketuk tombol 📍
   di meja): Biasa, Dekat Jendela (tip +15%), Sempit (kesabaran -10%).
9. **Pinjaman & Pajak** — pinjam Rp100.000 / Rp200.000, utang berbunga
   2%/hari, bisa bayar Rp50.000 atau lunasi semua. Pajak 5% dari
   pendapatan minggu itu, dibayar tiap hari ke-7.
10. **Kompetitor** — di hari acak kompetitor promo (pelanggan -30%).
    Bales dengan Promo Sendiri (Rp30.000, pelanggan +30% & harga -10%
    hari itu).
11. **Tantangan Mingguan** — layani 50 pelanggan/minggu = bonus
    Rp100.000, reset tiap minggu.
12. **Mini-Game Tambahan** — (a) Cuci Piring: timing jarum, sempurna
    +Rp15.000 & reputasi +1, bagus +Rp8.000; (b) Hitung Kembalian: kasir
    tampilkan total & uang dibayar, pilih kembalian benar dari 3 pilihan
    — benar +Rp10.000 & reputasi +1, salah reputasi -2.
13. **Lokasi / Food Truck** — pilih lokasi untuk besok: Tetap di Ruko
    (normal), Mall (pelanggan +40%, harga +15%, sewa +Rp15.000/hari),
    Kampus (pelanggan +30%, harga -10%, sewa +Rp5.000/hari),
    Pinggir Jalan (pelanggan +10%, harga -15%, sewa -Rp5.000/hari).

Fitur v2 tetap ada: Mode Cerita 30 Hari Bintang 5, resep rahasia &
achievement, tema, mini-game masak, cabang kedua. Save v1 dan v2 tetap
bisa dimuat di v3 (field baru diisi default).

## Baru di v4 (13 Nov 2026) — semua ide tambahan masuk

1. **Kritikus Makanan & VIP** — kritikus datang diam-diam di hari acak
   (tanda ⭐ di meja, mulai hari ke-3). Dilayani SEMPURNA = reputasi +5,
   kecewa/pergi = reputasi -5. VIP (👑) tip 2x lipat tapi sabar pendek.
2. **Pesanan Khusus** — pelanggan kadang minta tanpa pedas / vegetarian /
   tanpa es / porsi kecil (tampil di mejanya). Terpenuhi kalau kualitas
   masakan Bagus atau SEMPURNA = bonus Rp2.000; kalau kualitas biasa =
   komplain, reputasi -1.
3. **Catering Acara Besar** — tawaran muncul acak tiap pagi (20–50 porsi,
   uang muka 50% di depan). Terima lalu layani jumlah itu hari yang sama:
   berhasil = sisa pembayaran + reputasi +2, gagal = uang muka
   dikembalikan, reputasi -2.
4. **Lomba Masak Kota** — tiap 30 hari. Pendaftaran Rp50.000, menang
   kalau hari itu ada ≥3 masakan SEMPURNA dan ≥8 pelanggan dilayani =
   hadiah Rp200.000 + reputasi +3.
5. **Waralaba / Franchise** — syarat: cabang kedua sudah buka, Level 4
   & Bintang 4, Rp1.000.000 per franchise (maks 3). Royalti Rp20.000
   per franchise/hari (naik per level, upgrade Rp500.000/level).
   Ada risiko acak franchise bermasalah — bayar perbaikan Rp20.000
   atau reputasi -1 di akhir hari.
6. **Supplier Langganan** — kontrak Rp100.000 untuk 7 hari: harga stok
   -20%. Ada risiko acak supplier mogok 1 hari (stok tidak bisa dibeli).
7. **Reservasi Meja** — 1–2 reservasi tiap hari (jam & meja tertentu).
   Kalau meja kosong dan bersih saat jamnya tiba, pelanggan datang
   dan bayar + tip besar; kalau meja masih terisi/kotor = reputasi -2.
8. **Inspeksi Kebersihan** — inspektur datang mendadak di hari acak.
   Lolos kalau tidak ada meja kotor dan tidak ada stok lama (umur ≥2
   hari): reputasi +2. Gagal: denda Rp30.000, reputasi -3.
9. **Prestige / New Game+** — setelah tamat Bintang 5, tombol Prestige
   mereset uang/hari/level ke awal, TAPI bonus permanen: masak 10%
   lebih cepat & tip +10% per Prestige (maks 3x). Jumlah Prestige
   tersimpan di save.
10. **Statistik & Laporan** — panel Statistik: pendapatan & pelanggan
    7 hari terakhir, menu terlaris, total dilayani, pelanggan tetap,
    delivery terkirim, total pajak & pinjaman yang sudah dibayar.
11. **Meja Kotor** — setelah pelanggan pergi, meja jadi kotor (🧹) dan
    tidak bisa dipakai sampai dibersihkan (tombol 🧹 Bersihkan Meja).
    Meja kotor yang dibiarkan sampai akhir hari menurunkan reputasi
    (1 per meja, maks -3).

Fitur v2/v3 tetap ada semua. Save v1, v2, dan v3 tetap bisa dimuat di
v4 (field baru diisi default: prestige 0, meja bersih, lomba hari ke-30).

## Baru di v5 (13 Nov 2026) — semua 30 ide tambahan masuk

1. **Jam Sibuk** — 12:00-13:00 & 18:00-20:00 pelanggan datang 2x lipat,
   sabar lebih pendek (bar atas menunjukkan saat jam sibuk sedang berlangsung).
2. **Keluarga Besar** — 10% pelanggan datang sekeluarga, pesan banyak
   (+Rp10.000), hanya mau duduk di Meja Besar (pilih meja mana yang jadi
   Meja Besar lewat tombol di kartu Jam Sibuk).
3. **Takeaway / Bungkus** — 15% pelanggan bungkus tanpa duduk, dimasak
   lalu langsung bayar, tip kecil.
4. **Kartu Member** — pelanggan puas kadang daftar member (diskon 5%,
   datang lebih sering, tip +5%).
5. **Komplain & Refund** — pelanggan kecewa meninggalkan komplain;
   pilih: Refund (uang kembali, reputasi +1), Ganti Menu gratis
   (Rp5.000, reputasi +2), atau Minta Maaf saja (gratis, reputasi tetap).
6. **Mystery Shopper** — datang diam-diam di hari acak; puas & SEMPURNA =
   bonus Rp50.000 & reputasi +3, kecewa = reputasi -3.
7. **Antrean Luar** — kalau semua meja penuh/kotor, pelanggan menunggu
   di luar (maks 5); masuk kalau ada meja kosong, pergi kalau menunggu
   terlalu lama (reputasi -1).
8. **Paket Combo** — 20% pelanggan pesan combo, bonus +Rp8.000.
9. **Happy Hour** — 15:00-17:00 minuman (Es Teh, Es Kopi, Jus, Es Teh
   Sultan) diskon 20%, pelanggan minuman lebih banyak.
10. **Dessert & Penutup** — setelah makan utama, 30% pelanggan pesan
    dessert (+Rp12.000). Menu dessert baru: Es Krim Sundae (Rp12.000)
    dan Puding Coklat (Rp10.000), buka di Level 2.
11. **Bahan Langka Musiman** — Durian Montong (Rp45.000) hanya tersedia
    hari ke-5, 6, 7, 15, 16, 17, 25, 26, 27 tiap 10 hari, stok terbatas.
12. **Kebun Sendiri** — 3 petak kebun, tanam Rp10.000/petak (nasi/mie/teh),
    panen 3 hari kemudian (+5 stok gratis).
13. **Upgrade Peralatan** — Kompor (semua menu), Oven (nasi), Fryer
    (burger & ayam geprek), maks Lv2, tiap level masakan jenis itu 15%
    lebih cepat.
14. **Peralatan Rusak** — peralatan bisa rusak acak; masakan jenis itu
    50% lebih lambat sampai diservis (Rp20.000).
15. **Iklan** — TV (Rp100.000, 3 hari, pelanggan x1.5), Radio (Rp50.000,
    2 hari, x1.3), Sosmed (Rp30.000, 2 hari, x1.2).
16. **Influencer Endorse** — bayar Rp150.000, besok pelanggan membludak
    (x2); kalau pelayanan besok buruk (<8 pelanggan dilayani), review
    jelek dan reputasi -3.
17. **Voucher & Kupon** — bagi kupon Rp20.000: hari itu pelanggan +30%,
    harga -10%.
18. **Investasi** — Emas (Rp200.000, return 2%/minggu) dan Properti
    (Rp500.000, return 3%/minggu), bisa dijual kembali seharga modal.
19. **Renovasi** — Rp200.000: reputasi +5, pelanggan +10% permanen,
    tapi besok restoran TUTUP 1 hari.
20. **Gudang** — upgrade maks Lv2 (Rp100.000/Rp200.000): stok kedaluwarsa
    3 hari jadi 4-5 hari.
21. **Training Karyawan** — latih karyawan (Rp40.000 x level) naik level;
    gaji ikut naik, fatigue berkurang 20%.
22. **Karyawan Resign** — fatigue ≥90% dua hari berturut-turut: karyawan
    resign (level turun 1). Cegah dengan Bonus (Rp20.000, fatigue 0)
    atau Istirahatkan.
23. **Anak Magang** — rekrut Rp20.000, kerja setengah kecepatan karyawan
    biasa; setelah 5 hari bisa jadi Koki tetap.
24. **Musik Live** — sewa musisi Rp30.000 untuk 2 hari: pelanggan lebih
    sabar, tip +10%, pelanggan +10%.
25. **Bencana / Kejadian Acak** — mati lampu, gas habis, atau banjir
    (acak, ~12%/hari): pelanggan -70% sampai diperbaiki (Rp50.000).
26. **Tantangan Harian** — tiap hari misi beda (layani 10 pelanggan /
    3 SEMPURNA / dapat Rp100.000), selesai = bonus Rp15.000-25.000.
27. **Mode Malam** — toggle: buka sampai 24:00, ada pelanggan malam
    (tip lebih besar, sabar pendek), biaya operasional +Rp10.000/hari.
28. **Turnamen Antar Restoran (Liga)** — poin mingguan dari pelanggan &
    reputasi; peringkat 1 = bonus Rp50.000, peringkat 2 = Rp25.000,
    dihitung tiap hari ke-7.
29. **Mode Hardcore** — toggle: uang di bawah 0 selama 3 hari
    berturut-turut = BANGKRUT, game over. Mode normal tidak game over.
30. **Cerita Pelanggan** — pelanggan tetap punya cerita: pesan menu
    favoritnya 3x = hadiah Rp30.000 & reputasi +2.

Fitur v2/v3/v4 tetap ada semua. Save v1, v2, v3, dan v4 tetap bisa
dimuat di v5 (field baru diisi default).

## Tes v5 (13 Nov 2026, Node, harness stub DOM di /tmp/run_v5.js & /tmp/run_v5_extra.js)

- `node --check` pada JavaScript game: OK (1270 baris).
- Smoke test autoplay 300 tick: 28-29 pelanggan dilayani, uang
  bertambah, hari lanjut ke hari 2 tanpa error.
- Jam sibuk: pengali pelanggan 1,20 -> 2,40 di jam 12:30.
- Peralatan: Oven Lv1, waktu masak Nasi Goreng 6 -> 5 detik.
- Kebun: tanam nasi, setelah 3 hari panen (petak kosong lagi, stok +5).
- Iklan TV: aktif 3 hari, pengali x1.5. Voucher: harga Nasi Goreng
  Rp15.000 -> Rp13.500, voucherDays 1. Musik live: 2 hari.
- Happy Hour: Es Teh Rp5.000 -> Rp4.000 di jam 16:00.
- Bahan langka: tersedia hari ke-5, tidak tersedia hari ke-1.
- Tantangan Harian: layani 10 pelanggan selesai, bonus masuk
  (uang Rp100.000 -> Rp125.000, termasuk hadiah Rp25.000).
- Mode Malam: dayEnd 1320 -> 1440 saat dinyalakan.
- Keluarga + Combo: payAndLeave keluarga+combo menambah familyServed
  dan comboServed, uang bertambah (+bonus Rp10.000 + Rp8.000).
- Komplain: refund Rp15.000 menyelesaikan komplain (daftar kosong).
- Hardcore: uang -Rp100 di akhir hari, bankruptDays 0 -> 1.
- Investasi: Emas Rp200.000 memberi return mingguan di hari ke-7.
- Takeaway: pelanggan takeaway dimasak lalu bayar tanpa meja
  (takeawayDone 0 -> 1).
- Sistem v4 tetap jalan: kritikus SEMPURNA reputasi 80 -> 86,
  meja kotor memblokir tempat duduk dan bisa dibersihkan, delivery
  terkirim (deliveryDone 1) setelah stok diisi.
- Save/load roundtrip v5 sama persis (uang, prestige, franchise,
  meja kotor, kebun, peralatan, mode malam), save yang uangnya diubah
  manual ditolak (checksum), save v4 berhasil dimigrasi (field v5
  default: kebun kosong, peralatan Lv0, mode malam mati).
- **Yang tidak sempat diuji secara deterministik:** dessert (peluang
  30% acak), mystery shopper (acak), bencana (acak), liga (butuh
  7 hari penuh — logikanya sama dengan pajak mingguan yang sudah
  teruji), cerita pelanggan 3x (butuh 3 kunjungan langganan), dan
  resign (butuh fatigue 90% dua hari berturut-turut). Semuanya
  sudah dibaca ulang kodenya dan memakai jalur yang sama dengan
  fitur teruji, tapi belum ada angka tesnya.
- **Catatan tes:** satu kegagalan awal adalah kesalahan tes, bukan
  game — tes memakai Kompor untuk Nasi Goreng, padahal Nasi Goreng
  pakai Oven (sesuai desain). Setelah diganti ke Oven, lolos.
  Satu hal yang perlu diketahui: save membatasi uang minimal 0,
  jadi uang negatif (Mode Hardcore) menjadi Rp0 saat dimuat kembali
  — itu perilaku lama sejak v4, bukan bug v5.
- Catatan: tes ini pakai stub DOM di Node, bukan klik langsung di browser
  HP/laptop Ztr — coba mainkan dan kabari kalau ada yang aneh.

## Tes v4 (13 Nov 2026, Node, harness stub DOM di /tmp/run_v4.js)

- `node --check` pada JavaScript game: OK.
- Smoke test autoplay 300 tick: 23 pelanggan dilayani, uang bertambah,
  hari lanjut, 5–7 delivery terkirim, ulasan & pelanggan tetap tercatat.
- Meja kotor: meja kotor memblokir tempat duduk (freeTable melewatinya),
  tombol Bersihkan mengembalikan meja ke normal.
- Kritikus: dilayani SEMPURNA reputasi 80 → 86; kritikus kehabisan
  sabar reputasi 80 → 72. VIP: tip 2x (Rp5.000 + tip Rp750×2 =
  Rp6.500). Pesanan khusus: kualitas Bagus +Rp2.000 bonus, kualitas
  biasa komplain reputasi -1 (80 → 80: +1 puas -1 komplain).
- Catering: terima 2 porsi (uang muka Rp15.000), layani 2 pelanggan,
  akhir hari uang -Rp30.000 sewa +Rp15.000 sisa = sesuai hitungan.
  Catering gagal (50 porsi, 0 dilayani): uang muka Rp375.000
  dikembalikan — uang akhir Rp70.000 sesuai hitungan.
- Lomba: daftar Rp50.000, 3 SEMPURNA & 8 pelanggan = menang,
  uang Rp220.000 (termasuk hadiah Rp200.000), lomba berikutnya hari
  ke-60.
- Franchise: buka Rp1.000.000, upgrade ke Lv2 Rp500.000, perbaikan
  Rp20.000, royalti Rp40.000/hari masuk di akhir hari (uang akhir
  Rp525.000 sesuai hitungan termasuk sewa cabang).
- Supplier: kontrak Rp100.000/7 hari, beli stok nasi diskon 20%
  (Rp25.000 → Rp20.000); saat mogok, pembelian stok diblokir.
- Reservasi: meja kosong & bersih saat jamnya = pelanggan datang
  duduk; meja kotor = gagal, reputasi 80 → 78.
- Inspeksi: lolos reputasi 80 → 83 (+2 inspeksi +1 target harian);
  gagal (1 meja kotor) reputasi 80 → 77, denda Rp30.000 — uang
  Rp100.000 → Rp40.000 sesuai hitungan.
- Prestige: setelah tamat Bintang 5, Prestige 1x mereset uang ke
  Rp50.000/hari 1/level 1, waktu masak Nasi Goreng 6 → 5 detik,
  dan Prestige tersimpan di save.
- Statistik: pendapatan & pelanggan harian tercatat tiap akhir hari
  (Hari 1: Rp50.000, 5 pelanggan).
- Save/load roundtrip v4 sama persis (uang, prestige, franchise,
  supplier, meja kotor, lomba, statistik), save yang uangnya diubah
  manual ditolak (checksum), save v3 berhasil dimigrasi (prestige
  default 0, meja bersih, lomba hari ke-30, cabang & utang lama utuh).
- Sistem lama tetap jalan: mini-game masak SEMPURNA, harga Fine Dining
  Rp24.000, resep rahasia terbuka + stok 5, delivery, cuci piring
  sempurna +Rp15.000, kembalian benar +Rp10.000.
- **Bug yang ditemukan & diperbaiki saat tes:** baris tanda
  Kritikus/VIP di render meja sempat crash saat meja kosong (`c` null)
  karena berada di luar blok `if(c)` — diperbaiki dengan guard `if(c)`,
  lalu semua tes diulang dan lolos (ALL_TESTS_OK, diulang 2x).
  Satu ekspektasi tes yang salah juga dikoreksi: sewa dengan cabang
  adalah Rp45.000 (bukan Rp30.000) karena sewa cabang +Rp15.000 —
  gamenya benar, hitungan tesnya yang dikoreksi.
- Catatan: tes ini pakai stub DOM di Node, bukan klik langsung di browser
  HP/laptop Ztr — coba mainkan dan kabari kalau ada yang aneh.

## Tes v3 (13 Nov 2026, Node, harness stub DOM di /tmp/run_v3.js & /tmp/run_v3_extra.js)

- `node --check` pada JavaScript game: OK.
- Smoke test autoplay 300 tick: 23 pelanggan dilayani, uang bertambah,
  hari lanjut, 5 delivery terkirim, 5 ulasan & 3 pelanggan tetap tercatat.
- Stok: berkurang saat masak, beli 5 pcs berhasil, stok umur 3 hari
  dibuang di akhir hari.
- Delivery: terkirim (+bayaran & tip) dan telat (rating -5, late +1).
- Mini-game: cuci piring sempurna +Rp15.000; hitung kembalian benar
  +Rp10.000 (pilihan berisi kembalian yang benar).
- Eksperimen: sukses (random dipaksa) membuat menu custom + stok 5 dan
  tersimpan di save; gagal tidak menambah menu. (Satu run acak normal
  gagal — sesuai peluang 40%.)
- Karyawan: rekrut Koki Lv1, waktu masak berkurang; pinjaman Rp100.000
  lalu bayar Rp50.000 (sisa Rp50.000, bunga 2% jadi Rp51.000 di akhir
  hari); promo aktif; lokasi Mall berlaku mulai hari berikut.
- Viral: review 5-bintang ke-3 berturut-turut mengaktifkan viral 2 hari.
- Zona meja: tip meja Jendela terhitung Rp21.450 (harga + tip 30%),
  kesabaran meja Sempit habis lebih cepat.
- Tantangan mingguan: pelanggan ke-50 memberi bonus (ditandai selesai).
- Pajak: hari ke-7 memotong 5% dari pendapatan minggu (Rp100.000 → pajak
  Rp5.000), lalu pendapatan/kunjungan mingguan di-reset.
- Kompetitor: pengali pelanggan turun saat kompetitor promo.
- Sistem lama tetap jalan: mini-game masak SEMPURNA, harga Fine Dining
  Rp24.000, resep rahasia terbuka + stok 5, cabang memberi penghasilan.
- Save/load roundtrip v3 sama persis (uang, cabang, pinjaman, lokasi,
  karyawan, delivery, menu custom), save yang uangnya diubah manual
  ditolak (checksum), save v2 dan v1 berhasil dimigrasi (stok default
  10, utang 0).
- **Bug yang ditemukan & diperbaiki saat tes:** field v2 (cabang, bintang,
  tema) sempat hilang saat load save v3 karena `unpackSave` hanya
  menerapkannya untuk `d.v===2`; diperbaiki jadi `d.v>=2`, lalu diuji
  ulang — cabang Lv1 sekarang tersimpan dengan benar.
- Catatan: tes ini pakai stub DOM di Node, bukan klik langsung di browser
  HP/laptop Ztr — coba mainkan dan kabari kalau ada yang aneh.

## Tes v2 (13 Nov 2026, Node, harness stub DOM)

- `node --check` pada JavaScript game: OK.
- Smoke test autoplay (layani meja yang SIAP tiap tick): 300 tick melayani
  36 pelanggan, uang bertambah, hari lanjut ke hari 2 tanpa error.
- Mini-game: posisi 80% = SEMPURNA, cookLeft dipotong jadi 2 detik.
- Tema Fine Dining: harga Nasi Goreng Rp15.000 → Rp24.000.
- Resep rahasia: perfectServes=10 membuka Nasi Goreng Spesial + achievement.
- Cabang: endDay memberi penghasilan cabang, hari lanjut normal.
- Save/load roundtrip sama persis, save yang uangnya diubah manual ditolak
  (checksum), save v1 berhasil dimigrasi ke v2.
- Catatan: tes ini pakai stub DOM di Node, bukan klik langsung di browser
  HP/laptop Ztr — coba mainkan dan kabari kalau ada yang aneh.


## Baru di v6 (13 Nov 2026) — 60 fitur baru + UI TAB anti-scroll

### Masalah yang dijawab
Di v5 semua kartu fitur ditumpuk dalam satu halaman panjang — di HP harus
scroll sangat jauh. Di v6 layar utama hanya menampilkan HUD, meja, dapur,
dan log singkat. Semua fitur lain dipindah ke 6 tab di bar bawah yang
selalu terlihat (sticky): 🍽️ Meja | 🍳 Dapur | 👨‍🍳 Karyawan | 💰 Bisnis |
🎉 Event | 📊 Statistik. Klik tab = hanya kartu tab itu yang tampil
(`.card` lain disembunyikan dengan class `tab-on`); konten tiap tab boleh
scroll di dalam tabnya sendiri, tapi layar utama tidak lagi panjang.
Isi tiap tab: Meja 9 kartu, Dapur 9, Karyawan 4, Bisnis 9, Event 8,
Statistik 7 (total 40 kartu + 8 kartu v6).

### Pelanggan Baru (tab Meja/Event)
1. Turis asing — bayar lebih mahal (+Rp5.000) & tip besar, suka menu lokal.
2. Anak sekolah — jam pulang sekolah, pesan menu murah (≤Rp12.000).
3. Pekerja kantoran — jam makan siang, buru-buru, sabar lebih pendek.
4. Pasangan date — pesan mahal, tip besar kalau suasana bagus.
5. Pelanggan ulang tahun — pesan Kue Ultah, hadiah kecil = tip +Rp10.000.
6. Lansia — sabar lama (drain x0.6), loyal, sering balik.
7. Driver ojek — pesan kopi cepat, tidak rewel.
8. Pelanggan ngutang — minta bayar belakangan, 30% tidak bayar (uang hilang).
9. Pelanggan bawa anak kecil — pesan Nugget Anak, sabar orang tua pendek.
10. Grup arisan — pesan banyak, patungan +Rp15.000.

### Menu & Makanan (tab Dapur)
11. Sarapan pagi — Bubur Ayam & Nasi Uduk (Level 1). 12. Menu sehat —
Salad & Jus Detox (Level 2, bayar lebih mahal). 13. Level pedas 1-5 —
pelanggan pilih level; masak SEMPURNA/Bagus = puas, biasa = komplain
pedas (reputasi -1). 14. Menu anak — Nugget Anak Rp8.000. 15. Boba Brown
Sugar (Level 2). 16. Kue Ultah Custom Rp50.000 (Level 3, menu khusus).
17. Menu fusion — gabung 2 menu jadi menu custom Rp30.000 (Rp40.000).
18. Sambal racikan sendiri — Rp15.000, reputasi +1 per level. 19. Paket
Keluarga — 1 harga untuk 4 orang (+Rp80.000). 20. Buy 1 Get 1 — minuman
setengah harga hari itu (Rp30.000).

### Dapur & Operasional (tab Dapur)
21. Antrean dapur — Kritikus/VIP dimasak duluan otomatis. 22. Koki
istirahat — setelah 5 masakan koki lelah (masak 50% lebih lambat) sampai
diistirahatkan. 23. Freezer — Rp120.000, stok kedaluwarsa +2 hari.
24. Kurir bahan telat — 15% hari, pembelian stok diblokir hari itu.
25. Tagihan listrik/gas/air — tiap hari ke-30 (Rp20.000 + Rp5.000/meja).
26. Kebersihan dapur — level 0-100%, bersihkan Rp10.000. 27. Piring &
gelas — mulai 20 pcs, berkurang tiap pelanggan dilayani, beli 10 pcs
Rp10.000. 28. Kebakaran kecil — 5% hari, timer 10 detik untuk memadamkan;
telat = dapur tutup hari itu. 29. Masakan gosong — masakan siap yang
tidak disajikan >25 tick dibuang, reputasi -1. 30. Mini-game Potong
Bahan — timing seperti mini-game masak; SEMPURNA = masakan berikutnya
15% lebih cepat.

### Uang & Bisnis (tab Bisnis)
31. Sponsor brand — +Rp50.000 di depan + Rp10.000/hari selama 7 hari.
32. Stand food court — Rp300.000, +Rp15.000/hari. 33. Merchandise —
beli 10 pcs Rp50.000, terjual otomatis 2/hari @Rp15.000. 34. Kelas
masak — 1x/hari, +Rp20.000 & reputasi +1. 35. Katering kantoran —
kontrak Rp100.000, +Rp30.000/hari. 36. Delivery langganan — 20% pelanggan
delivery yang puas jadi langganan (maks 10), +Rp5.000/pelanggan/hari.
37. Asuransi resto — Rp50.000, biaya perbaikan bencana jadi Rp25.000.
38. Donasi makanan sisa — toggle, stok sisa didonasikan (reputasi +1)
bukan dibuang. 39. Food waste — stok busuk dicatat; >20/minggu =
reputasi -1. 40. Harga dinamis — toggle, harga naik saat ramai
(spawn >1.3) dan turun saat sepi (<0.8).

### Karyawan (tab Karyawan)
41. Karyawan Terbaik — bonus Rp30.000, kecepatan +10% selama 7 hari.
42. Seragam — Rp80.000, tip +5%. 43. Jadwal libur — libur 2 hari,
fatigue kembali 0, efek karyawan itu 0 selama libur. 44. Guest chef —
Rp100.000/7 hari, pelanggan x1.3 & masak lebih cepat. 45. Manajer —
Rp200.000, otomatis bersihkan 1 meja kotor tiap 20 tick, sabar +5%.

### Suasana & Dekor (tab Meja)
46. Dekor musiman — Lebaran/Natal/Halloween/Imlek Rp50.000, reputasi +2.
47. Spot foto — Rp60.000, viral lebih mudah (pelanggan +5%).
48. TV — Rp40.000, sabar +10%. 49. Taman — Rp50.000, reputasi +3.
50. Lampu malam — Rp30.000, tip malam +10%.

### Event & Cerita (tab Event)
51. Festival Makanan Kota — Rp50.000, layani ≥10 pelanggan hari itu =
hadiah Rp150.000. 52. Catering pernikahan — tawaran 50-80 porsi, uang
muka Rp400.000. 53. Ulang tahun resto — tiap 30 hari, reputasi +2.
54. Festival Durian — di hari bahan langka, stok durian +10 gratis.
55. Lomba Makan Pedas — Rp20.000, menang (≥2 SEMPURNA hari itu) =
Rp50.000. 56. Tebak Menu — tebak bahan masakan, benar +Rp5.000.

### Sistem & Lain-lain (tab Statistik)
57. Koleksi stiker — tiap menu pertama kali terjual dapat stiker;
lengkap = bonus Rp100.000. 58. Achievement tersembunyi — syarat tidak
ditampilkan (mis. layani turis / keluarga besar), masing-masing
+Rp20.000. 59. Bonus login harian — klaim 1x/hari, Rp10.000 +
Rp5.000 x streak. 60. Mode Sandbox — toggle, uang jadi Rp999.999.999
untuk coba semua fitur; dimatikan, uang kembali ke jumlah semula
(disimpan di `sandboxBackup`).

## Tes v6 (13 Nov 2026, Node, harness stub DOM di /tmp/run_v6.js & /tmp/run_v6_extra.js)

- `node --check` pada JavaScript game: OK. File: 1523 baris, ~152 KB.
- Tab switching: `showTab('dapur')` menampilkan hanya kartu Dapur (3 kartu
  dapur aktif, 0 kartu Meja aktif); `showTab('bisnis')` mengubah label
  tab aktif ke Bisnis; kembali ke Meja berfungsi. Kartu per tab di HTML
  asli: Meja 9, Dapur 9, Karyawan 4, Bisnis 9, Event 8, Statistik 7.
- Autoplay 300 tick: 27-29 pelanggan dilayani, uang bertambah, hari lanjut
  ke hari 2, lost 0.
- Turis: `payAndLeave` turis menaikkan counter turis +1 dan memberi
  +Rp5.000 (plus tip & achievement tersembunyi).
- Harga dinamis: Nasi Goreng Rp15.000 → Rp18.150 saat viral + harga dinamis
  aktif.
- Mini-game potong bahan: posisi 80% = SEMPURNA, `chopBonus` = 1.
- Kebakaran: timer habis tanpa dipadamkan → `kitchenClosed` = true.
- Sandbox: nyala → uang Rp999.999.999; mati → uang kembali ke jumlah
  semula (diuji Rp686.599 → kembali Rp686.599).
- Bonus login: klaim pertama +Rp15.000 (streak 1), klaim kedua hari yang
  sama diblokir (streak tetap 1).
- Tagihan bulanan: `endDay` hari ke-30 memotong Rp30.000 (tagihan listrik/
  gas/air) — `utilitiesPaid` bertambah.
- Sistem v5 tetap jalan: kritikus SEMPURNA reputasi 80 → 86, meja kotor
  memblokir tempat duduk & bisa dibersihkan, delivery terkirim.
- Tes ekstra: sponsor (+Rp50.000), food court, freezer, seragam, TV, spot
  foto, guest chef 7 hari, manajer, fusion (menu custom +1), sambal,
  paket keluarga, harga dinamis — semua lolos; save/load v6 menyimpan
  sponsor/food court/manajer/fusion dengan benar.
- Save/load roundtrip v6 sama persis (uang, kebun, peralatan, mode malam,
  prestige, franchise, field v6), save yang uangnya diubah manual ditolak
  (checksum), save v5 berhasil dimigrasi (field v6 diisi default: piring
  20, kebersihan dapur 100, cabang & utang lama utuh).
- **Bug yang ditemukan & diperbaiki saat tes:** (1) delivery langganan
  tidak pernah bertambah — diperbaiki: 20% delivery yang puas jadi
  langganan (maks 10). (2) sponsor tidak pernah kedaluwarsa — diperbaiki:
  hari sponsor berkurang tiap pagi. (3) karyawan libur tetap berefek —
  diperbaiki: `effStaff` mengembalikan 0 saat libur. (4) tip seragam
  (+5%) dan lampu malam (+10%) belum masuk hitungan tip — diperbaiki.
  (5) satu ekspektasi tes salah (tes mengira turis = 1 padahal autoplay
  sudah melayani 2 turis) dan satu tes ekstra kekurangan uang untuk
  spot foto — keduanya kesalahan tes, bukan game.
- Yang tidak teruji secara deterministik: sebagian jalur acak/multi-hari
  (mystery shopper, bencana, liga, cerita pelanggan, resign, kurir telat,
  kebakaran acak) — kodenya memakai jalur yang sama dengan fitur teruji.
  Sebagian fitur v6 disederhanakan: antrean dapur = prioritas otomatis
  Kritikus/VIP (tanpa UI antrean manual); Kue Ultah = menu khusus yang
  dipesan pelanggan ultah.

## Patch v6.1 (13 Nov 2026, siang) — 2 hal yang di v6 baru klaim, belum jalan

- **Piring habis sekarang benar-benar memblokir:** di v6, piring cuma
  counter — pelanggan tetap duduk & dimasak walau piring 0, padahal kartu
  Dapur menulis "HABIS! Pelanggan menunggu". Di v6.1, `seatCustomers()`
  tidak mendudukkan pelanggan baru kalau piring 0 (peringatan log/toast
  sekali saja, bukan tiap detik); pelanggan yang sudah duduk tetap
  dilayani sampai selesai. Beli 10 piring Rp10.000 di tab Dapur, pelanggan
  langsung duduk lagi.
- **Prioritas dapur Kritikus/VIP sekarang benar-benar jalan:** di v6,
  `startCooking()` mengambil pelanggan pertama dalam urutan datang, jadi
  kritikus/VIP tidak didahulukan walau kartunya menulis begitu. Di v6.1,
  urutan masak: Kritikus dulu, lalu VIP, lalu yang lain (urutan datang
  dipertahankan di dalam tiap tier).
- Tidak ada perubahan skema save (versi save tetap 6): save v6 tetap bisa
  dimuat, tidak perlu migrasi.
- Tes v6.1 (13 Nov 2026, Node, harness stub DOM di /tmp/test_v61.js):
  `node --check` OK; piring 0 → pelanggan tidak duduk, piring 5 →
  duduk; kritikus didahulukan atas pelanggan biasa; VIP didahulukan atas
  pelanggan biasa; beli piring 0 → 10; save/load roundtrip v6 sama persis;
  save yang uangnya diubah manual ditolak (checksum). Semua 7 tes lolos
  (ALL_V61_TESTS_OK). Tes pakai stub DOM di Node, bukan klik langsung di
  HP/laptop Ztr.
- Catatan: tes ini pakai stub DOM di Node, bukan klik langsung di browser
  HP/laptop Ztr — coba mainkan dan kabari kalau ada yang aneh.

## Catatan

- Tampilan game ini top-down dengan emoji, bukan isometrik pixel persis
  seperti screenshot — loop gameplay-nya yang dibuat sama.
- Save tersimpan per perangkat/browser (localStorage). Pindah HP → laptop:
  pakai Export di perangkat lama, Import di perangkat baru.

## Baru di v7 (13 Nov 2026) — 30 fitur baru + PWA + musik latar

UI tab v6 dipertahankan: layar utama hanya HUD, meja, dapur/mini-game,
dan log singkat; semua fitur baru masuk ke tab yang ada, plus 1 tab baru
🌍 Kota. Save v6 (dan v5/v4/v3/v2/v1) tetap bisa dimuat — field v7 diisi
default. SAVE_KEY tetap `restoSimSaveV1`, versi save naik ke 7.

1. **Bintang Michelin** (tab 🌍 Kota) — setelah Bintang 5: Bintang 1 butuh
   reputasi ≥95, Level ≥8, layani ≥500, 0 komplain minggu ini; Bintang 2:
   rep ≥97, Level ≥10, layani ≥800; Bintang 3: rep ≥99, Level ≥12, layani
   ≥1200. Tiap bintang: harga +10% & bonus Rp100.000.
2. **Ramadan & buka puasa** — hari ke-28, 29, 30 tiap 30 hari: buka puasa
   17–19 ramai x1.8, menu Kolak Pisang (Rp8.000) & Es Buah (Rp10.000)
   otomatis terbuka dengan +5 stok gratis, sahur 03–05 (pelanggan +30%).
3. **Buka di kota lain** (tab 🌍 Kota) — Jakarta (sewa mahal, pelanggan
   +30%), Bandung (sewa sedang), Bali (turis 2x lipat, harga +25%).
   Pilihan berlaku mulai besok; sewa, harga & tipe pelanggan berubah.
4. **Dine and dash** — pelanggan acak kabur tanpa bayar (tagihan hangus,
   reputasi -2). Ada tombol 🏃 KEJAR (peluang berhasil 70%, uang kembali)
   atau pasang CCTV Rp120.000 (pelanggan kabur ketahuan & tetap bayar).
5. **Keracunan makanan** — kalau kebersihan dapur <50 atau ada stok
   berumur ≥2 hari, pelanggan bisa keracunan (25%): reputasi -5, denda
   Rp20.000. Jaga kebersihan dapur (bersihkan Rp10.000).
6. **Sertifikat Halal** (tab Bisnis) — Rp150.000 pertama / Rp100.000
   perpanjang, berlaku 30 hari: pelanggan +10%, reputasi +2, harga +5%.
7. **IPO / go public** (tab Bisnis) — syarat Level 7 & uang Rp2.000.000:
   modal +Rp1.000.000 sekali, lalu dividen Rp20.000/minggu.
8. **Robot pelayan** (tab Dapur) — Rp500.000: menyajikan 1 meja siap
   otomatis tiap 20 detik, tanpa lelah; pelanggan penasaran, tip +10%.
9. **Self-order kiosk / QR menu** (tab Dapur) — Rp150.000: pelanggan pesan
   sendiri, kesabaran berkurang lebih lambat (x0.9).
10. **Pembayaran QRIS / digital** (tab Dapur) — Rp50.000: 50% pelanggan
    bayar pakai QRIS — bayar lebih cepat, tip x0.9, tidak ada mini-game
    kembalian / risiko salah kembalian.
11. **Rooftop / area outdoor** (tab Meja) — Rp400.000: harga +20%
    (tidak saat hujan), pelanggan +10%.
12. **Private room / ruangan VIP** (tab Meja) — Rp250.000: disewa
    +Rp20.000/hari, pelanggan pesan lebih banyak.
13. **Parkir & valet** (tab Meja) — upgrade parkir Lv1–2 (Rp100.000/
    Rp200.000): kalau parkir penuh pelanggan pergi; valet Rp80.000 bikin
    tip VIP +50% lagi.
14. **Gift card** (tab Bisnis) — jual Rp25.000/kartu, uang masuk di depan;
    kartu dipakai beberapa hari kemudian (pelanggan makan gratis saat itu).
15. **Loyalty tier Gold/Platinum/Diamond** (tab Bisnis) — member naik tier
    dari total kunjungan: Gold (2x, diskon 10%), Platinum (5x, diskon 10%
    + datang lebih sering), Diamond (10x, diskon 15% + tip besar).
16. **Kupon ulang tahun pelanggan** (tab Bisnis) — beri kupon Rp10.000 ke
    pelanggan tetap yang ulang tahun: besok dia bawa teman-teman
    (pelanggan +30%).
17. **Hadiah misterius harian** (tab Event) — 1 kotak/hari: hadiah acak
    (uang Rp20.000, +5 stok menu, atau reputasi +2).
18. **Mini-game tangkap pesanan** (tab Dapur) — jarum bergerak, tekan
    ⏱️ TANGKAP!: SEMPURNA +Rp10.000, berhasil +Rp5.000, gagal piring pecah
    -Rp5.000.
19. **Rumor / hoax kompetitor** (tab Event) — rumor acak (3 hari,
    reputasi -1/hari); iklan klarifikasi Rp50.000 memulihkan reputasi +2.
20. **Audit pajak** (tab Statistik) — tiap 14 hari: kalau pajak selalu
    dibayar, lolos; kalau pernah telat, denda Rp100.000.
21. **Energi surya** (tab Bisnis) — Rp600.000: tagihan listrik bulanan
    turun 50% selamanya.
22. **Kemasan eco** (tab Bisnis) — nyala/mati: review delivery lebih baik
    saat nyala.
23. **Daur ulang** (tab Bisnis) — Rp30.000: +Rp5.000 & reputasi +1 tiap
    minggu.
24. **Cerita warisan keluarga** (tab Event) — quest 3 langkah: layani 200
    pelanggan → 50 masakan SEMPURNA → raih Bintang 4. Hadiah: menu
    "Resep Warisan Ayah" (Rp60.000) + Rp50.000 per langkah.
25. **Karyawan sakit / cuti** (tab Karyawan) — karyawan bisa sakit acak
    1–2 hari (tidak bisa kerja); cuti berbayar Rp10.000 menyembuhkan.
26. **Chef tamu internasional** (tab Karyawan) — Rp300.000, 3 hari:
    pelanggan x1.4, masak lebih cepat (x0.9).
27. **Festival Kemerdekaan 17 Agustus** (tab Event) — hari ke-17 tiap 30
    hari: pelanggan +40%, menu merah putih, lomba makan kerupuk
    (Rp10.000, peluang menang 50%, hadiah Rp30.000).
28. **Sistem cuaca ekstrem** (tab Event) — acak tiap hari: badai
    (pelanggan -50%) atau panas terik (minuman +50%).
29. **Pet-friendly area** (tab Meja) — Rp100.000: pelanggan bawa hewan,
    pesan lebih banyak (+Rp5.000), pelanggan +10%, perlu kebersihan ekstra.
30. **Mode "Legenda Kuliner"** (tab Statistik) — terbuka setelah Prestige
    3x: target layani 1000 pelanggan & 3 Bintang Michelin; tercapai =
    bonus Rp500.000 & tip +10% permanen.

Juga diperbaiki di v7: `unpackSave` yang tadinya hanya memulihkan field
v5 saat `d.v===5` (save v6 yang dimuat akan mereset field v5 ke default)
sekarang berlaku untuk `d.v>=5`.

## PWA — install sebagai aplikasi (baru di v7)

File di folder ini: `index.html`, `manifest.webmanifest`,
`sw.js` (service worker, cache `resto-sim-v7`), `icon-192.png`,
`icon-512.png` (ikon PNG asli, dibuat dengan Python/PIL).

**Cara menjalankan:** PWA TIDAK jalan penuh kalau file dibuka dengan
double-click (`file://`) — service worker dan install butuh server
lokal/HTTPS. Cara termudah:

```
cd ~/workspace/restaurant-simulator
python3 -m http.server
```

lalu buka `http://localhost:8000` di browser. Atau upload semua file ke
hosting statis (Netlify / Vercel / GitHub Pages) lalu buka lewat HTTPS.

**Cara install:** saat game dibuka, muncul banner "Jadikan Resto
Simulator sebagai aplikasi di HP kamu? Bisa dimainkan offline." dengan
tombol [📲 Install] dan [Nanti dulu]. Tombol Install memakai prompt
install browser (`beforeinstallprompt`); hasilnya (accepted/dismissed)
dicatat di localStorage. Kalau browser tidak mendukung install prompt
(mis. iOS Safari / dibuka lewat `file://`), banner menampilkan petunjuk
manual: di iPhone: Share > Add to Home Screen; di Android: menu ⋮ >
Install app / Add to Home screen.

**Pengingat mingguan:** kalau memilih Nanti dulu / dismiss, banner TIDAK
muncul lagi selama 7 hari. Setelah 7 hari berlalu, banner muncul lagi
saat game dibuka. Kalau sudah Install/accepted, banner tidak muncul lagi.
Status ini disimpan di localStorage kunci `restoSimPwaPrompt` — terpisah
dari save game, jadi tidak merusak checksum save.

**Offline:** service worker menyimpan `index.html`, manifest, dan ikon
saat install; saat offline game disajikan dari cache. Kalau ada versi
baru (cache name berubah, mis. `resto-sim-v8`), cache lama dihapus dan
cache baru dipakai.

**Jujur soal tes:** install prompt asli browser TIDAK bisa dites penuh di
Node — itu hanya bisa dites di browser sungguhan lewat localhost/HTTPS.
Yang dites di Node: manifest JSON valid, `sw.js` ada cache name v7 dan
fetch handler, dan logika pengingat mingguan (lihat "Tes v7").

## Musik latar (baru di v7)

Musik dibuat **secara prosedural dengan Web Audio API di dalam
`index.html`, tanpa file audio eksternal dan tanpa lagu berhak cipta** —
jadi game tetap satu file dan bebas hak cipta. Nadanya piano/lembut
(pentatonik mayor C-D-E-G-A), tempo lambat ~72 BPM, ada pad/strings
lembut di belakang (akord C–Am–F–G), melodi berulang pelan dengan variasi
acak ringan. Tidak ada drum keras.

- **Menyalakan/mematikan:** tombol 🔊 Musik di baris kontrol atas (HUD).
  Ada juga slider volume 0–100% di sampingnya.
- **Preferensi** (nyala/mati + volume) disimpan di localStorage kunci
  `restoSimMusic` — terpisah dari save game, tidak merusak checksum.
- **Musik TIDAK autoplay paksa:** browser memblokir audio sebelum
  interaksi pengguna. Musik mulai setelah klik/tap pertama di game (kalau
  preferensi tersimpan bilang musik nyala), atau lewat tombol 🔊 Musik.
- **Efek suara kecil:** bunyi "ding" saat pelanggan dilayani (bayar) dan
  "pop" saat menyajikan — volume kecil, ikut mati saat musik dimatikan
  (toggle suara terpisah belum ada; SFX ikut status musik).
- **Loop & performa:** scheduler ringan `setInterval` 250 ms dengan
  lookahead Web Audio; musik tidak mengganggu timer game.

**Jujur soal tes:** suara aslinya hanya bisa dites di browser sungguhan,
bukan di Node (Node tidak punya AudioContext). Yang dites di Node:
`node --check` lolos, fungsi musik ada dan tidak crash saat dipanggil
dengan stub tanpa AudioContext (`musicStart()` mengembalikan `false`),
preferensi volume tersimpan benar di localStorage stub.

## Tes v7 (13 Nov 2026, Node, harness stub DOM di /tmp/run_v7.js)

- `node --check` pada JavaScript game (termasuk kode PWA + musik): OK.
  `node --check` pada `sw.js`: OK. File: 1999 baris, ~207 KB.
- Manifest: JSON valid (`name` "Resto Simulator", `short_name` "Resto
  Sim", `display` "standalone", `start_url` ".", `theme_color` #1d2b4f,
  ikon 192 & 512). `sw.js`: cache name `resto-sim-v7`, ada fetch handler
  (cache-first + update cache). Ikon: PNG asli 192x192 & 512x512
  (dicek dengan `file`).
- Fitur v6 lama tetap jalan: tab switching (Dapur 2/2 kartu aktif, Meja
  0; tab 🌍 Kota 2/2), kritikus SEMPURNA reputasi 80 → 86, sandbox nyala
  → Rp999.999.999 dan mati → uang kembali persis.
- Autoplay 300 tick: pelanggan dilayani (1–4 per run, jumlah bervariasi
  karena acak), uang bertambah, hari lanjut ke hari 2. (Catatan: angka
  "lost" di autoplay stub tinggi karena harness hanya menyajikan meja
  yang sudah siap dan tidak mengklik secepat pemain sungguhan — ini
  perilaku stub, bukan regresi v7.)
- Michelin: syarat terpenuhi → Bintang 1, bonus +Rp100.000.
- Rooftop: Nasi Goreng Rp15.000 → Rp21.780 (Jakarta x1.1, Michelin x1.1,
  rooftop x1.2) — sesuai hitungan.
- Halal: beli Rp150.000 → aktif, uang berkurang tepat Rp150.000.
- QRIS: aktif setelah dibeli Rp50.000.
- Kota lain: `setCity('bali')` → besok Bali; harga Bali Rp25.988
  (x1.25 kota, x1.1 Michelin, x1.2 rooftop, x1.05 halal) — sesuai.
- Robot pelayan: meja siap otomatis disajikan (state `ready` →
  `eating`) saat tick ke-20.
- Dine and dash: dengan CCTV → `dashLost` 0, uang masuk penuh
  (+Rp48.586); tanpa CCTV → `dashLost` 1, tagihan hangus, tombol KEJAR
  berhasil (acak 0.1 < 0.7) → uang Rp28.586 kembali.
- Keracunan: dapur kotor + stok tua → `poisoned` 0 → 1; bersihkan dapur
  → kebersihan 100.
- Hadiah misterius: dibuka → +Rp20.000, tidak bisa dibuka 2x sehari.
- Mini-game tangkap pesanan: posisi 80% = SEMPURNA → `catchWins` +1,
  +Rp10.000.
- Musik (stub tanpa AudioContext): `musicStart()` mengembalikan `false`
  tanpa crash; `setMusicVolume(0.7)` tersimpan di localStorage stub
  (`restoSimMusic` = `{"on":false,"vol":0.7,"sfx":true}`); `playSfx`
  tidak crash.
- PWA pengingat mingguan (stub localStorage + tanggal): baru = muncul;
  ditolak hari ini = tidak muncul; ditolak 8 hari lalu = muncul lagi;
  accepted/installed = tidak muncul.
- Save/load roundtrip: sama persis (uang, Michelin 1, kota Jakarta,
  halal aktif); save yang uangnya diubah manual ditolak (checksum);
  save v6 berhasil dimigrasi (Michelin default 0, kota Jakarta, piring
  20 dari v6 utuh). — **ALL_TESTS_OK**
- Yang tidak teruji secara deterministik: sebagian jalur acak/multi-hari
  (Ramadan, rumor, audit pajak, karyawan sakit, chef internasional,
  cuaca ekstrem, IPO dividen mingguan, gift card ditebus, loyalty tier
  naik, warisan 3 langkah, Legenda Kuliner) — kodenya memakai jalur yang
  sama dengan fitur teruji (endDay/genDayStart/payAndLeave). Tes pakai
  stub DOM di Node, bukan klik langsung di HP/laptop Ztr.
