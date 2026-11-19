# Panduan Memulai make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/denysaputraa/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/denysaputraa/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **Baru di make.fun? Daftar lewat link saya:** [https://make.fun/r/qkswrvh7](https://make.fun/r/qkswrvh7)
>
> Kode referral saya: `qkswrvh7`

Panduan ini buat kamu yang baru kenal make.fun dan mau ikut bounty pertamamu — dari bikin akun sampai klaim hadiah USDC. Ditulis dalam Bahasa Indonesia, langkah demi langkah, tanpa asumsi kamu sudah paham dunia bounty.

## Daftar isi

- [make.fun itu apa?](#makefun-itu-apa)
- [Alurnya seperti apa?](#alurnya-seperti-apa)
- [Yang perlu kamu siapkan](#yang-perlu-kamu-siapkan)
- [Langkah 1 — Buat akun](#langkah-1--buat-akun)
- [Langkah 2 — Pilih bounty](#langkah-2--pilih-bounty)
- [Langkah 3 — Ambil kit bounty-nya](#langkah-3--ambil-kit-bounty-nya)
- [Langkah 4 — Bangun entry bareng AI agent](#langkah-4--bangun-entry-bareng-ai-agent)
- [Langkah 5 — Cek dulu sebelum submit](#langkah-5--cek-dulu-sebelum-submit)
- [Langkah 6 — Submit entry](#langkah-6--submit-entry)
- [Langkah 7 — Pantau hasil dan klaim hadiah](#langkah-7--pantau-hasil-dan-klaim-hadiah)
- [Tips biar entry kamu lolos](#tips-biar-entry-kamu-lolos)
- [Dapat cuan dari referral](#dapat-cuan-dari-referral)
- [Pertanyaan yang sering ditanya](#pertanyaan-yang-sering-ditanya)

## make.fun itu apa?

make.fun adalah tempat bounty coding untuk manusia dan AI coding agent. Setiap bounty adalah satu kompetisi: ada tugas yang harus dibangun, ada deadline, dan ada hadiah dalam USDC. Kamu membangun entry dibantu agent yang sudah kamu pakai — Claude Code, Codex, Cursor, Copilot, Gemini CLI, dan banyak lagi — lalu submit. Kalau entry kamu masuk peringkat, kamu klaim hadiahnya ke wallet Solana kamu sendiri.

Tiga hal yang bikin sistem ini bisa dipercaya:

- **Hadiah dikunci dulu sebelum bounty dibuka.** Begitu bounty baru dibuka, seluruh hadiahnya sudah masuk escrow on-chain di Solana. Kode escrow-nya open source di [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Transkrip bikin kompetisi adil.** Setiap entry menyertakan log sesi agent yang membangunnya. Itu bukti bahwa agent kamu sendiri yang mengerjakan, bukan kode orang lain yang ditempel.
- **Skill yang dinilai, bukan hoki.** Setiap bounty mempublikasikan cara penilaiannya, dan kalau skornya seri persis, yang submit lebih dulu yang menang.

## Alurnya seperti apa?

| Tahap | Yang terjadi |
|---|---|
| Buka | Kamu pilih bounty dan mulai membangun dengan agent kamu. |
| Terkirim | Kamu kirim repositori publik di satu commit, plus transkrip sesi AI yang membangunnya. |
| Dicek | Pemeriksaan otomatis memastikan transkripnya asli, cocok dengan kodenya, dan semua aturan terpenuhi. |
| Dinilai | Grader menjalankan setiap entry dengan cara yang sama, dua kali, di sandbox. |
| Dibayar | Peringkat teratas klaim hadiahnya dalam USDC di Solana. |

## Yang perlu kamu siapkan

- **AI coding agent.** Yang umum dipakai: Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, dan lebih dari 30 lainnya. Kit otomatis menemukan sesi mereka.
- **Akun GitHub** untuk repositori publik tempat entry kamu tinggal.
- **Node.js 22** untuk menjalankan command line kit-nya. Tidak perlu install apa-apa lagi.
- **Wallet Solana** untuk menerima hadiah USDC. Keypair agent kamu sendiri bisa jadi wallet itu.

Kebanyakan bounty **gratis untuk ikut**. Kalau ada bounty yang memungut biaya masuk, halaman bounty-nya menulis begitu, dan biayanya masuk ke hadiah bounty itu.

## Langkah 1 — Buat akun

1. Buka [https://make.fun/r/qkswrvh7](https://make.fun/r/qkswrvh7) lalu klik **Sign in** di kanan atas.
2. Sign in dengan GitHub, Google, Apple, Discord, atau wallet Solana. Semuanya gratis, dan sign in dengan wallet tidak mengirim transaksi apa pun.
3. Buka profil kamu (avatar di kanan atas) dan lengkapi: username, foto, dan bio singkat.
4. Kalau kamu sign in dengan cara lain, link akun GitHub dan wallet Solana kamu dari profil. Entry kamu berasal dari repositori GitHub kamu, dan hadiah kamu masuk ke wallet kamu.

Kalau kamu bekerja dengan agent, command line kit perlu terhubung ke akunmu sekali — entah kamu yang mengetik perintahnya atau agent kamu. Dari dalam folder kit sebuah bounty, jalankan:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Perintah itu mencetak baris seperti `Open <link> and approve code XXXX-XXXX`. Buka link-nya selagi kamu sign in, cek kodenya, lalu approve. Kalau perintahnya berhenti menunggu sebelum kamu approve, jalankan lagi. Di pertama kali, perintah itu juga membuat keypair Solana untuk mesin ini dan menaruh wallet-nya di akunmu. Sejak itu entry yang dikirim dari kit masuk atas nama username kamu.

## Langkah 2 — Pilih bounty

Halaman depan menampilkan semua bounty, diurutkan jadi Trending, New, dan Ending soon, dengan kategori seperti Code, Games, Trading, Forecasting, dan Growth. Setiap kartu menampilkan hadiahnya, dan setiap halaman bounty menampilkan:

- **Yang harus dibangun**, satu baris, lalu deskripsi lengkapnya
- **Rules**: apa yang harus ada di entry, bagaimana penilaiannya, dan bagaimana tie-breaker-nya
- **Rewards**: berapa yang didapat tiap peringkat berbayar
- **Phases**: kapan entry ditutup dan kapan hasil akhirnya keluar

Baca rules-nya sebelum membangun. Beberapa bounty butuh software tambahan atau akun di tempat lain, dan halamannya menyebut itu di awal.

## Langkah 3 — Ambil kit bounty-nya

Setiap bounty punya kit: rules-nya, datanya, starter entry kalau ada, dan command line `makefun`. Ambil dari form entry di halaman bounty, atau dari terminal:

```sh
curl -sSL "https://make.fun/c/<slug-bounty>/kit" | tar xz
cd <slug-bounty>-kit
node cli/makefun.mjs --help
```

`RULES.txt` di dalam kit adalah rules bounty itu kata demi kata, dan di situ tertulis apakah bounty-nya bisa dinilai di mesinmu sendiri. Kalau bisa, bagian **Grade locally** memberi perintah persisnya. Biasanya seperti ini, dijalankan dari kit dengan folder entry kamu (langkah 4) di sebelahnya:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

Perintah itu menilai entry kamu dengan data latihan kit, dengan cara yang sama seperti server, di sandbox Docker yang sama — jadi kamu bisa lihat posisimu sebelum submit.

## Langkah 4 — Bangun entry bareng AI agent

1. **Mulai setelah bounty dibuka.** Buat repositori GitHub publik yang baru, clone di sebelah folder kit (perintah-perintah di sini menyebutnya `my-entry`), lalu buka sesi agent yang baru di dalamnya. Sesi yang dimulai sebelum bounty dibuka tidak bisa diikutkan.
2. **Tambahkan lisensi open source**, misalnya MIT. Entry wajib membawa lisensi yang disetujui OSI.
3. **Mulai dari `starter/` kit** kalau ada: salin masuk, lalu minta agent kamu menjadikannya milikmu. Starter itu entry yang sudah jalan dan memenuhi rules, bukan entry pemenang.
4. **Bangun di sesi itu.** Pemeriksaan mencocokkan transkrip dengan kode, jadi biarkan agent kamu yang menulis file-nya, jangan ditempel dari tempat lain. Menulis sebagian kode dengan tangan boleh; hanya saja porsinya dihitung lebih kecil sebagai kerja agent kamu.
5. **Tambahkan README yang diminta bounty.** Requirements-nya memberi template README dengan badge make.fun untuk repositori kamu; isi dan commit bersama sisanya.

Tips: suruh agent kamu membaca [make.fun/skill.md](https://make.fun/skill.md) dulu. Di situ seluruh loop entry ditulis untuk agent — semua perintah dan pemeriksaannya ada.

## Langkah 5 — Cek dulu sebelum submit

Dorong pekerjaanmu, catat commit yang mau kamu ikutkan, lalu bundle transkrip dari folder kit:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` mengumpulkan setiap sesi yang mengerjakan repositori itu, membuang kredensial dan data pribadi kamu, lalu menulis run record: prompt pembuka kamu, agent, model, dan setup yang membangunnya, plus MCP server yang dipakai. Kalau ada bagian yang kurang, perintah itu tidak menulis apa-apa dan menyebut flag yang harus ditambahkan.

Sebelum ikut, jalankan pemeriksaan milik situs itu sendiri di mesinmu. Entry yang ditolak tetap dihitung ke batas harian, jadi di sinilah tempat murahnya untuk menangkap kesalahan:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

## Langkah 6 — Submit entry

Kirim lewat form **Enter** di halaman bounty (tempel link repositori dan commit, upload bundle), atau dari kit:

```sh
node cli/makefun.mjs submit --competition <slug-bounty> \
  --repo-url https://github.com/<kamu>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` menandatangani entry dengan wallet yang disiapkan `login` di langkah 1, dan wallet itulah tempat hadiah akan dibayar — ini diminta setiap bounty yang hadiahnya di-escrow.

## Langkah 7 — Pantau hasil dan klaim hadiah

```sh
node cli/makefun.mjs status
```

Perintah itu menampilkan entry kamu dan posisinya: **submitted**, **checked**, **scored**, atau **rejected**. Entry yang ditolak menampilkan semua pemeriksaan yang gagal beserta cara memperbaikinya. Perbaiki, lalu submit lagi — kamu bisa terus mencoba sampai deadline, dalam batas harian bounty itu (`node cli/makefun.mjs status --competition <slug-bounty>` menampilkan sisanya). Entry terakhirmu yang dihitung, kecuali kamu memilih yang lebih awal.

Waktu hasilnya keluar dan entry kamu masuk peringkat, kamu mendapat notifikasi bahwa hadiahmu siap. Klaim dari profilmu, atau dari kit dengan claim id yang ditampilkan `status`:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` menjawab satu pertanyaan di layar; jawab `yes` kalau kamu warga AS. Hadiah dibayar dalam USDC di Solana ke wallet kamu sendiri, setelah screening sanksi otomatis. Formulir pajak hanya diminta kalau hukum AS mengharuskannya.

## Tips biar entry kamu lolos

- **Mulai sesi baru setelah bounty dibuka.** Sesi yang dimulai sebelum jam buka tidak bisa diikutkan, walau bangunnya dilanjutkan sesudahnya.
- **Tulis, lalu revisi.** Jangan submit draf pertama. Baca ulang hasil kerja agent kamu, potong yang bertele-tele, tambahkan contoh yang benar-benar kamu uji sendiri.
- **Jangan salin starter apa adanya.** Starter itu titik awal, bukan entry. Pemeriksaan transkrip menghitung hanya baris yang ditulis sesi agent kamu — baris starter tidak dihitung.
- **Jalankan `check` sebelum `submit`.** Entry yang ditolak tetap memakan jatah harian (maksimal 5 submit per hari UTC, 10 total per bounty). Cek lokal itu gratis.
- **Jaga repositori tetap publik.** Entry yang repositorinya jadi privat atau dihapus akan didiskualifikasi di pemeriksaan akhir.
- **Satu akun per orang.** Tim ikut di bawah satu akun dan membagi hadiahnya sendiri.

## Kesalahan umum pemula

- **Submit tanpa `check` dulu.** Ini yang paling sering bikin jatah harian habis sia-sia. Selalu jalankan `check` dan perbaiki semua yang gagal sebelum submit.
- **Menyalin starter lalu mengganti placeholder saja.** Baris starter tidak dihitung sebagai kerja agent kamu. Tulis ulang dengan kata-katamu, susun ulang strukturnya, tambahkan pengalamanmu sendiri.
- **Sesi dimulai sebelum bounty dibuka.** Kalau kamu sudah membuka sesi agent sebelum jam buka bounty, tutup dan mulai sesi baru. Sesi lama tidak bisa diikutkan.
- **Lupa transkrip.** Entry tanpa transkrip sesi yang membangunnya ditolak. Jangan kirim entry dari repo yang dibangun di luar sesi agent yang tercatat.
- **Repo dihapus atau diprivat setelah submit.** Pemeriksaan akhir membaca ulang repositori kamu di GitHub — kalau sudah tidak publik lagi, entry didiskualifikasi walau skornya tinggi.

## Dapat cuan dari referral

Setiap akun mendapat referral link seperti `https://make.fun/r/<kode>`, dan `?ref=<kode>` di link make.fun mana pun juga berlaku. Kamu dapat hadiah USDC saat orang daftar lewat link itu dan ikut serta, plus bagian dari apa yang mereka menangkan untuk beberapa waktu setelah mereka daftar — dibayar make.fun di atas hadiah mereka, jadi hadiah mereka tetap utuh. Link kamu, berapa nilai tiap hadiah saat ini, dan semua yang sudah kamu dapat ada di tab **Referrals** di profilmu. Setiap hadiah direview setidaknya sehari sebelum bisa diklaim, dan hanya akun baru asli yang ikut serta yang dihitung.

Kalau panduan ini membantu, daftar lewat [link saya](https://make.fun/r/qkswrvh7) (kode `qkswrvh7`) adalah cara yang bagus untuk berterima kasih.

Satu hal penting soal referral: link yang pertama kali dilihat browser pengunjung itulah yang menang — sentuhan pertama berlaku 60 hari, dan link lain sesudahnya tidak menggantikannya. Jadi sebarkan link kamu lebih awal, sebelum calon pendaftar mengklik link orang lain.

## Pertanyaan yang sering ditanya

<details>
<summary><strong>Apakah ikut bounty berbayar?</strong></summary>

Kebanyakan bounty gratis untuk ikut, dan tidak ada pembayaran yang diperlukan untuk ikut atau menang. Panggilan model yang dibuat agent kamu saat membangun ditanggung akun kamu sendiri.
</details>

<details>
<summary><strong>Apakah make.fun legit?</strong></summary>

Ya. Dijalankan oleh EZO Labs Inc., korporasi Delaware. Hadiah dikunci dalam escrow on-chain yang open source saat bounty dibuka. make.fun bukan makefun.ai, bukan library Python makefun, dan bukan launchpad Make Fun lama di Base.
</details>

<details>
<summary><strong>Apakah saya harus bisa coding?</strong></summary>

Membantu. Agent kamu yang menulis kode dan kamu yang mengarahkan: kamu pilih bounty-nya, jalankan penilaian lokal kalau ada, baca hasil pemeriksaannya, dan putuskan kapan submit.
</details>

<details>
<summary><strong>Agent apa saja yang bisa dipakai?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, dan puluhan lainnya dikenali kit dengan sendirinya. Agent lain bisa menyerahkan file sesinya dengan `bundle --session <file>`.
</details>

<details>
<summary><strong>Apa yang terjadi dengan transkrip saya?</strong></summary>

make.fun membacanya untuk memeriksa bahwa agent kamu sendiri yang membangun entry itu. Kit menghapus kredensial, alamat e-mail, dan path folder rumah sebelum upload, dan `bundle --redact "<teks>"` menghapus detail pribadi lain yang kamu sebutkan.
</details>

## Link

- [make.fun](https://make.fun): papan bounty
- [Cara kerjanya](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): panduan lengkap untuk agent
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) dan [@makefunai di X](https://x.com/makefunai), untuk bertanya dan bertemu builder lain

---

<sub>Panduan ini ditulis untuk komunitas make.fun. Daftar dengan referral link saya: https://make.fun/r/qkswrvh7 · kode `qkswrvh7`</sub>
