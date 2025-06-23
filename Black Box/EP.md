# 1. Registrasi

| TC     | Kelas Equivalence                   | Input                                              | Expected Output                         |
|--------|-------------------------------------|----------------------------------------------------|------------------------------------------|
| EP-R1  | Nama, email, dan password valid     | Nama: Asgar, Email: asgar@mail.com, Pass: 12345678 | Redirect ke dashboard                    |
| EP-R2  | Nama kosong (invalid)               | Nama: "", Email: user@mail.com, Pass: 12345678     | Error: Nama wajib diisi                 |
| EP-R3  | Email kosong (invalid)              | Nama: Asgar, Email: "", Pass: 12345678             | Error: Email wajib diisi                |
| EP-R4  | Password < 6 karakter (invalid)     | Nama: Asgar, Email: user@mail.com, Pass: 123       | Error: Password terlalu pendek          |
| EP-R5  | Email tidak sesuai format (invalid) | Nama: Asgar, Email: usermail.com, Pass: 12345678   | Error: Format email tidak valid         |

---

# 2. Login 

| TC     | Kelas Equivalence                      | Input                                          | Expected Output                          |
|--------|----------------------------------------|------------------------------------------------|-------------------------------------------|
| EP-L1  | Kredensial valid                       | Email: user@mail.com, Pass: benar123           | Redirect ke dashboard                     |
| EP-L2  | Email kosong                           | Email: "", Pass: benar123                      | Error: Email wajib diisi                  |
| EP-L3  | Password kosong                        | Email: user@mail.com, Pass: ""                 | Error: Password wajib diisi               |
| EP-L4  | Email tidak terdaftar (invalid)        | Email: tidakada@mail.com, Pass: salah123       | Error: Kredensial salah                   |
| EP-L5  | Password salah (invalid)               | Email: user@mail.com, Pass: salah123           | Error: Kredensial salah                   |

---

# 3. Cek Trip

| TC     | Kelas Equivalence                          | Input (disederhanakan)                         | Expected Output                          |
|--------|--------------------------------------------|------------------------------------------------|-------------------------------------------|
| EP-C1  | Semua input valid                          | Trif valid, data lengkap                       | Redirect ke halaman konfirmasi            |
| EP-C2  | Trif tidak valid                           | Trif: tidak aktif                              | Error: Trif tidak valid                   |
| EP-C3  | Data member kosong                         | Field anggota kosong                           | Error: Data anggota wajib diisi           |
| EP-C4  | Tambah anggota gagal (duplikat)            | Nama anggota sudah ada                         | Error: Duplikasi anggota                  |
| EP-C5  | Coba lanjut tanpa klik "Saya Sudah Bayar"  | Tidak klik tombol konfirmasi                   | Tidak lanjut ke konfirmasi                |

---

# 4. Metode Pembayaran

| TC     | Kelas Equivalence                              | Input                                          | Expected Output                                |
|--------|------------------------------------------------|------------------------------------------------|-------------------------------------------------|
| EP-M1  | Semua data valid                                | Metode: Transfer Bank, ID transaksi: 123456    | Tampilkan invoice                               |
| EP-M2  | Metode tidak dipilih (invalid)                 | Metode: "", ID transaksi: 123456               | Error: Metode wajib dipilih                     |
| EP-M3  | ID transaksi kosong (invalid)                  | Metode: Transfer, ID transaksi: ""             | Error: ID transaksi wajib diisi                 |
| EP-M4  | Tambah anggota gagal (DB error)                | Tambah anggota setelah transaksi, terjadi error| Error saat validasi akhir                       |

