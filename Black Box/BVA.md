# 1. Registrasi

| TC     | Input                                                  | Expected Output                     | Path |
|--------|--------------------------------------------------------|-------------------------------------|------|
| TC-R1  | Nama: Asgar, Email: asgar@mail.com, Password: 1234567890 | Redirect ke dashboard               | R1   |
| TC-R2  | Nama: "", Email: "", Password: ""                      | Kembali ke form dengan error        | R2   |

---
# 2. Login

| TC     | Input                                | Expected Output                      | Path |
|--------|--------------------------------------|--------------------------------------|------|
| TC-L1  | Email dan password valid             | Redirect ke dashboard                | L1   |
| TC-L2  | Email atau password kosong           | Error validasi, kembali ke form      | L2   |
| TC-L3  | Email dan password valid tapi salah  | Error kredensial, kembali ke form    | L3   |

---

# 3. Cek Trip

| TC     | Input                              | Expected Output                                  | Path             |
|--------|------------------------------------|--------------------------------------------------|------------------|
| TC-C1  | Semua input valid                  | Redirect ke halaman konfirmasi                   | Jalur normal     |
| TC-C2  | Trif tidak valid                   | Kembali ke form dengan error                     | Gagal awal       |
| TC-C3  | Input kosong                       | Kembali ke form dengan error                     | Validasi gagal   |
| TC-C4  | Detail/member tidak valid          | Kembali ke form dengan error                     | Gagal pengecekan |
| TC-C5  | Tambah member gagal                | Kembali ke form hitung total & tampilkan error   | Tambah gagal     |

---

# 4. Metode Pembayaran

| TC     | Input                                               | Expected Output                                     | Path                |
|--------|-----------------------------------------------------|-----------------------------------------------------|---------------------|
| TC-M1  | Semua input valid                                   | Tampilkan invoice                                   | Jalur normal        |
| TC-M2  | Metode tidak dipilih                                | Kembali ke form dengan error                        | Gagal validasi awal |
| TC-M3  | Jumlah/ID transaksi kosong                          | Kembali ke form dengan error                        | Gagal input         |
| TC-M4  | Detail/member tidak valid                           | Kembali ke form dengan error                        | Gagal pengecekan    |
| TC-M5  | Tambah anggota gagal setelah transaksi              | Kembali ke form transaksi berhasil & tampilkan error| Gagal validasi akhir|
