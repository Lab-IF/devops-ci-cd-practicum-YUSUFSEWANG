#PERANGKAT PRAKTIKUM LAPORAN – PERTEMUAN 02  
## Praktikum Docker Dasar, Dockerfile, dan Docker Compose  
Nama : HASRIANA
NIM:105841107623  

# TUGAS 1 – Eksplorasi Docker Dasar
## Tujuan
Memahami siklus hidup kontainer Docker:
- Tarik gambar
- Menjalankan kontainer
- Melihat log
- Masuk ke kontainer
- Hentikan dan hapus wadah
## Langkah-Langkah
### Tarik Gambar
pesta
docker pull nginx : alpine
### Menjalankan Kontainer
pesta
docker run -d --name web-praktikum -p 8080:80 nginx : alpine
Cek kontainer berjalan:
pesta
docker ps
### Aplikasi Mengaksis
Buka browser:
http://localhost:8080
Hasil: Halaman default nginx berhasil ditampilkan.
### Melihat Log
pesta
docker logs web-praktikum
### Masuk ke Dalam Container
pesta
docker exec -it web-praktikum sh
Eksplorasi:
pesta
ls -la /usr/share/nginx/html
cat /etc/nginx/nginx.conf
KELUAR
###Hentikan dan Hapus Kontainer
pesta
docker stop web-praktikum
docker rm web-praktikum
## Kesimpulan Tugas 1
Siklus hidup kontainer Docker:
buat → jalankan → hentikan → hapus
Container lebih ringan dibandingkan Virtual Machine karena tidak memerlukan sistem operasi terpisah.

# TUGAS 2 – Membuat Image Docker Kustom
## Tujuan
Membuat image Docker sendiri menggunakan Dockerfile.
## Struktur Proyek
praktikum-docker/
│
├── Dockerfile
└── aplikasi/
    └── index.html
## Isi Dockerfile

dockerfile
DARI nginx : alpine
SALIN app/index.html /usr/share/nginx/html/index.html
EKSPOSISI 80
CMD [ "nginx", "-g", "daemon off;" ]
### Penjelasan
- FROM → menggunakan gambar dasar nginx alpine
- SALINAN → menyalin file HTML ke direktori nginx
- EXPOSE → mendeklarasikan port 80
- CMD → jalankan nginx di latar depan
## Membangun Gambar
pesta
docker build -t praktikum-docker : v1 .
Cek gambar:
pesta
gambar docker
## Menjalankan Kontainer
pesta
docker run -d -p 8080:80 --nama praktikum-web praktikum-buruh pelabuhan : v1
Akses:
http://localhost:8080
Hasil: Website custom dengan nama dan NIM berhasil ditampilkan.
## Kesimpulan Tugas 2
Saya berhasil:
- Membuat Dockerfile
- Membangun citra
- Batasi wadah dari gambar custom
Dockerfile memungkinkan pembuatan lingkungan aplikasi yang konsisten dan portabel.

# TUGAS 3 – Docker Compose Multi-Container
## Tujuan
Perbatasan beberapa container sekaligus dalam satu konfigurasi menggunakan Docker Compose.
## Layanan yang digunakan
- Web → nginx
- API → httpd
- Basis data → postgres
## 🔹 mengatur Docker Compose
pesta
docker compose up -d
Cek status:
pesta
docker compose ps
Melihat log:
pesta
docker compose logs -f
## Pengujian
Web:
http://localhost:8080
API:
http://localhost:8081
Servis kedua berhasil berjalan dengan baik.
## Pembersihan
pesta
docker compose down -v

# Perbedaan Kontainer vs Mesin Virtual
| Kontainer | Mesin Virtual |
| ------------ | ---------------- |
| Ringan | Lebih berat |
| Memulai dengan cepat | Startup lebih lama |
| Bagikan OS kernel | Memiliki OS sendiri |
| Cocok untuk layanan mikro | Cocok untuk isolasi penuh |

# Tangkapan layar
Screenshot yang dimasukkan ke dalam folder ` screenshots/ ` :
1. Output docker   ps
2. Tampilan nginx di   browser
3. Output dari docker build  
4. Gambar gagal dibuat  
5. Docker compose   ps
6 . Tampilan web & layanan api  

# Kesimpulan Akhir
Pada praktikum ini saya telah:
✅ Memahami siklus hidup kontainer Docker  
✅ Membatasi dan mengelola container  
✅ Membuat image Docker kustom menggunakan Dockerfile  
✅ Jangkar multi-kontainer menggunakan Docker Compose  
Docker membantu proses deployment aplikasi menjadi lebih cepat, ringan, dan konsisten.
