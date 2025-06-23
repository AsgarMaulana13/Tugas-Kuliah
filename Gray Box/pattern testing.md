# 1. Register

| TC     | Internal Insight                              | Action                        | Expected Output                             |
|--------|-----------------------------------------------|-------------------------------|---------------------------------------------|
| GR-R1  | Password di-hash sebelum disimpan             | Submit data valid             | Login otomatis dan redirect ke dashboard    |
| GR-R2  | Validasi server-side `if field == ""`         | Submit form kosong            | Tampilkan error & kembali ke form           |

---

# 2. Login

| TC     | Internal Insight                                  | Action                         | Expected Output                          |
|--------|---------------------------------------------------|--------------------------------|------------------------------------------|
| GR-L1  | Cek hash password, aktifkan session/token         | Masukkan email & password valid| Login sukses & redirect ke dashboard     |
| GR-L2  | Validasi server untuk field kosong                | Kosongkan input                | Error validasi, tidak lanjut ke DB       |
| GR-L3  | Password mismatch (hash compare gagal)            | Masukkan password salah        | Tampilkan error "Kredensial salah"       |

---

# 3. Cek Trip

| TC     | Internal Insight                                  | Action                            | Expected Output                                  |
|--------|---------------------------------------------------|-----------------------------------|--------------------------------------------------|
| GR-C1  | Cek DB: validasi trif, detail & member            | Submit data valid                 | Redirect ke instruksi bayar                     |
| GR-C5  | Tambah member gagal (data duplikat/DB error)      | Tambah data dengan error          | Error di form hitung total                      |

---

# 4. Metode Pembayaran

| TC     | Internal Insight                                     | Action                              | Expected Output                                     |
|--------|------------------------------------------------------|-------------------------------------|-----------------------------------------------------|
| GR-M1  | Validasi metode & tambah anggota terakhir sebelum invoice | Input semua valid                  | Invoice tampil                                      |
| GR-M5  | Gagal saat validasi akhir tambah anggota (DB/koneksi) | Submit form dengan error            | Form transaksi berhasil tapi tampilkan error        |

