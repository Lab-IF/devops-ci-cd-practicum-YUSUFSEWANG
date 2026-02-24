# Commands – Task 1 Docker Basic
Berikut adalah daftar perintah (command) yang dijalankan pada Task 1 – Eksplorasi Docker Dasar.

## 1️ Pull Image Nginx
bash
docker pull nginx:alpine
## 2️ Menjalankan Container
bash
docker run -d --name web-praktikum -p 8080:80 nginx:alpine
Keterangan:
d` → menjalankan container di background
name` → memberi nama container
`-p 8080:80` → mapping port host ke container
## 3️ Mengecek Container Berjalan
bash
docker ps
## 4️ Melihat Logs Container
bash
docker logs web-praktikum
## 5️ Masuk ke Dalam Container
bash
docker exec -it web-praktikum sh
Perintah yang dijalankan di dalam container:
bash
ls -la /usr/share/nginx/html
cat /etc/nginx/nginx.conf
exit
## 6️ Menghentikan Container
bash
docker stop web-praktikum
## 7️ Menghapus Container
bash
docker rm web-praktikum
#  Ringkasan Lifecycle Container
bash
docker pull nginx:alpine
docker run -d --name web-praktikum -p 8080:80 nginx:alpine
docker ps
docker logs web-praktikum
docker exec -it web-praktikum sh
docker stop web-praktikum
docker rm web-praktikum

# Status
Semua perintah berhasil dijalankan tanpa error dan container dapat diakses melalui browser pada:
http://localhost:8080
