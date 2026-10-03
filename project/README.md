# Windows Runner (GitHub Actions)

Workflow ini menjalankan GitHub-hosted runner `windows-2025`, menampilkan informasi runner di log, lalu menjaganya aktif dengan countdown sampai batas waktu. Setelah selesai (atau dihentikan manual), GitHub menghancurkan runner secara otomatis. Tidak ada RDP, kredensial, secret, atau layanan eksternal.

## Cara pakai

1. **Upload ke GitHub**: buat repository baru, lalu upload isi ZIP ini (folder `.github` dan `README.md`) ke branch default (`main`). Pastikan path `.github/workflows/windows-runner.yml` terjaga.
2. **Buka tab Actions** di repository.
3. **Pilih workflow** "Windows Runner" di sidebar kiri.
4. **Tekan Run workflow** (opsional isi durasi dalam menit, default 355), lalu klik tombol hijau **Run workflow**.
5. **Lihat status dan log**: klik run yang muncul, buka job `Windows Runner (windows-2025)`, lalu lihat:
   - Step *Tampilkan informasi runner*: computer name, edisi/versi Windows, OS build, runner image, waktu mulai/selesai.
   - Step *Runner aktif dengan countdown*: sisa waktu dicetak tiap 5 menit.
   - Ringkasan informasi juga muncul di halaman Summary run.

Untuk menghentikan lebih awal, klik **Cancel workflow** di halaman run.

## Catatan

- `timeout-minutes: 360` adalah batas maksimum job di GitHub-hosted runner (6 jam). Durasi default 355 menit agar workflow selesai rapi (status sukses) sebelum timeout memotongnya.
- Jika `windows-2025` tidak tersedia, ganti `runs-on` dengan `windows-2022` atau `windows-latest`.
- Repository privat memakai kuota menit Actions; runner Windows dihitung 2x lipat dari Linux. Repository publik gratis.
- Gunakan sesuai Ketentuan Layanan GitHub dan kebijakan penggunaan Actions, yang membatasi penggunaan yang tidak terkait pengembangan proyek.
