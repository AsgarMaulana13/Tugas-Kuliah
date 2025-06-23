# A Regiset
flowchart TD
    A[Start] --> B[Form Submitted]
    B --> C{Validasi Input?}
    C -- No --> D[Kembali ke Form dengan Error]
    C -- Yes --> E[Hash Password]
    E --> F[Simpan ke DB]
    F --> G[Login User Otomatis]
    G --> H[Redirect ke Dashboard]
    H --> I[End]

| Path | Jalur                                                              | Deskripsi                                |
|------|--------------------------------------------------------------------|------------------------------------------|
| R1   | Start → Submit → Validasi OK → Hash → Simpan DB → Login → Redirect | Jalur normal berhasil                    |
| R2   | Start → Submit → Validasi Gagal → Kembali ke Form                  | Gagal validasi input (e.g. email kosong) |

| TC    | Input                                                                         | Expected Output              | Path |
|-------|-------------------------------------------------------------------------------|------------------------------|------|
| TC-R1 | Nama: Asgar, Email: [asgar@mail.com](mailto:asgar@mail.com), Pass: 1234567890 | Redirect ke dashboard        | R1   |
| TC-R2 | Nama: "", Email: "", Pass: ""                                                 | Kembali ke form dengan error | R2   |

# B Login
flowchart TD
    A[Start] --> B[Form Submitted]
    B --> C{Validasi Input?}
    C -- No --> D[Kembali ke Form dengan Error]
    C -- Yes --> E{Cek Kredensial Valid?}
    E -- No --> F[Kembali ke Form dengan Error]
    E -- Yes --> G[Login Session]
    G --> H[Redirect ke Dashboard]
    H --> I[End]

| Path | Jalur                                                             | Deskripsi                               |
|------|-------------------------------------------------------------------|-----------------------------------------|
| L1   | Start → Submit → Validasi OK → Kredensial OK → Login → Redirect   | Login sukses                            |
| L2   | Start → Submit → Validasi Gagal → Kembali ke Form                 | Email/password tidak diisi atau invalid |
| L3   | Start → Submit → Validasi OK → Kredensial Gagal → Kembali ke Form | Email/password salah                    |

# C Cekou 
flowchart TD
    A[Start] --> B[Cek Trif Valid]
    B --> C{Validasi Input?}
    C -- No --> D[Kembali ke Form dengan Error]
    C -- Yes --> E{Cek Detail & Member Valid?}
    E -- No --> F[Kembali ke Form dengan Error]
    E -- Yes --> G[Tambah Member]
    G --> H{Validasi Input?}
    H -- No --> I[Kembali ke Form Hitung Total & Tampilkan Error]
    H -- Yes --> J{Cek Tambah Member?}
    J -- No --> K[Kembali ke Form Hitung Total & Tampilkan Error]
    J -- Yes --> L[Hitung Total Biaya]
    L --> M[Tampilkan Instruksi Bayar]
    M --> N[Klik "I Have Made Payment"]
    N --> O[Redirect ke Halaman Konfirmasi]
    O --> P[End]


| **TC**   | **Input**                                                                                         | **Expected Output**                                      | **Path / Deskripsi**                           |
|----------|---------------------------------------------------------------------------------------------------|-----------------------------------------------------------|------------------------------------------------|
| TC-C1    | Trif valid, input valid, detail & member valid, tambah member valid, bayar                       | Redirect ke halaman konfirmasi                            | Jalur normal berhasil                          |
| TC-C2    | Trif tidak valid                                                                                  | Kembali ke form dengan error                              | Gagal di tahap awal                            |
| TC-C3    | Input tidak valid (misal: field kosong)                                                           | Kembali ke form dengan error                              | Gagal validasi input                           |
| TC-C4    | Detail & member tidak valid                                                                       | Kembali ke form dengan error                              | Gagal pengecekan detail/member                 |
| TC-C5    | Tambah member gagal (misal: duplikat data atau input kosong)                                      | Kembali ke form hitung total & tampilkan error            | Gagal saat tambah member                       |

---
# D Metode Pembayaran
flowchart TD
    A[Start] --> B[Pilih Metode Pembayaran]
    B --> C[Validasi Metode]
    C --> D{Validasi Input?}
    D -- No --> E[Kembali ke Form dengan Error]
    D -- Yes --> F{Cek Detail & Member Valid?}
    F -- No --> G[Kembali ke Form dengan Error]
    F -- Yes --> H[Berhasil]
    H --> I{Validasi Input?}
    I -- No --> J[Kembali ke Form Transaksi Berhasil & Tampilkan Error]
    I -- Yes --> K{Cek Tambah Member?}
    K -- No --> L[Kembali ke Form Transaksi Berhasil & Tampilkan Error]
    K -- Yes --> M[Tampilkan Invoice]
    M --> N[End]



| **TC**   | **Input**                                                                                         | **Expected Output**                                      | **Path / Deskripsi**                           |
|----------|---------------------------------------------------------------------------------------------------|-----------------------------------------------------------|------------------------------------------------|
| TC-M1    | Metode dipilih, input valid, detail & member valid, tambah member valid                          | Tampilkan invoice                                          | Jalur normal berhasil                          |
| TC-M2    | Metode tidak dipilih atau invalid                                                                 | Kembali ke form dengan error                              | Gagal validasi metode                          |
| TC-M3    | Input tidak valid (misal: jumlah atau ID transaksi kosong)                                        | Kembali ke form dengan error                              | Gagal validasi input awal                      |
| TC-M4    | Detail & member tidak valid (misal: user tidak ditemukan atau expired)                            | Kembali ke form dengan error                              | Gagal pengecekan detail/member                 |
| TC-M5    | Tambah member gagal setelah transaksi berhasil (misal: koneksi error, data tidak ditemukan)      | Kembali ke form transaksi berhasil & tampilkan error      | Gagal saat validasi akhir tambah member        |
