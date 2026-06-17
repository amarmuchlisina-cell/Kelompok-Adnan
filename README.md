# Kelompok-Adnan
# 🚀 Deployment WordPress Enterprise-Ready Berbasis Docker Container

## 👥 Kelompok Adnan

Proyek ini merupakan implementasi arsitektur cloud modern berbasis Docker Container dengan memisahkan setiap layanan ke dalam container yang berbeda sehingga lebih aman, scalable, dan mudah dikelola.

---

# 📌 Arsitektur Sistem

```text
User
  |
  v
+------------------+
|    WordPress     |
|    Port 8080     |
+------------------+
        |
        +-------------------+
        |                   |
        v                   v
+---------------+    +---------------+
|     Redis     |    |     MySQL     |
|  Cache Layer  |    | Database Layer|
+---------------+    +---------------+
        |
        v
+------------------+
|  Redis Insight   |
|    Monitoring    |
+------------------+

        |
        v

+------------------+
|      MinIO       |
| Object Storage   |
+------------------+
```

---

# 📅 Milestone Minggu 1
## Fondasi Arsitektur & Isolasi Jaringan

### 🎯 Target

- Membuat struktur project Docker
- Menyiapkan WordPress Container
- Menyiapkan MySQL Container
- Menggunakan Docker Volume untuk persistensi data
- Mengimplementasikan Docker Network Isolation

---

## Komponen yang Digunakan

| Komponen | Fungsi |
|-----------|---------|
| WordPress | Application Layer |
| MySQL | Database Layer |
| Docker Volume | Penyimpanan Persisten |
| Frontend Network | Akses User ke WordPress |
| Backend Network | Komunikasi Internal |

---

## Docker Network

### frontend-net

Digunakan untuk komunikasi antara pengguna dan WordPress.

### backend-net

Digunakan untuk komunikasi internal antara:

- WordPress
- MySQL

---

## Docker Volume

### db_data

Menyimpan data MySQL secara persisten.

### wordpress_data

Menyimpan data WordPress secara persisten.

---

## Hasil Implementasi Minggu 1

✅ WordPress berhasil berjalan menggunakan Docker

✅ MySQL berhasil berjalan menggunakan Docker

✅ Data database tersimpan menggunakan Docker Volume

✅ Network Isolation berhasil diterapkan

✅ WordPress berhasil terhubung ke MySQL

---

# 📅 Milestone Minggu 2
## Optimasi Performa & Object Storage

### 🎯 Target

- Menambahkan Redis Cache
- Menambahkan Redis Insight Monitoring
- Menambahkan MinIO Object Storage
- Menghubungkan WordPress dengan Object Storage

---

## Komponen Tambahan

| Komponen | Fungsi |
|-----------|---------|
| Redis | Cache Layer |
| Redis Insight | Monitoring Redis |
| MinIO | Object Storage |
| Bucket wordpress-media | Penyimpanan File Upload |

---

## Redis Cache Layer

Redis digunakan sebagai Object Cache untuk WordPress.

### Konfigurasi

```php
define('WP_REDIS_HOST', 'redis-cache');
define('WP_REDIS_PORT', 6379);
```

### Manfaat

- Mempercepat loading website
- Mengurangi query database
- Mengurangi beban MySQL

---

## Object Storage Layer (MinIO)

### Container

```text
minio-storage
```

### Dashboard

```text
http://localhost:9001
```

### Endpoint

```text
http://minio-storage:9000
```

### Bucket

```text
wordpress-media
```

---

## Alur Upload Media

```text
User Upload File
       |
       v
WordPress
       |
       v
Bucket wordpress-media
       |
       v
MinIO Storage
```

---

## Hasil Implementasi Minggu 2

✅ Redis Cache berhasil diintegrasikan dengan WordPress

✅ Redis Insight berhasil melakukan monitoring Redis

✅ MinIO berhasil berjalan sebagai Object Storage

✅ Bucket wordpress-media berhasil dibuat

✅ WordPress berhasil terhubung ke MinIO

✅ File media WordPress berhasil tersimpan di Object Storage

---

# 📦 Docker Services

| Service | Container |
|-----------|-----------|
| WordPress | wordpress-app |
| MySQL | mysql-db |
| Redis | redis-cache |
| Redis Insight | redis-insight |
| MinIO | minio-storage |

---

# 📂 Docker Volumes

| Volume | Fungsi |
|----------|---------|
| db_data | Data MySQL |
| wordpress_data | Data WordPress |
| minio_data | Data Object Storage |

---

# 🌐 Docker Networks

| Network | Fungsi |
|-----------|---------|
| frontend-net | Akses User ke WordPress |
| backend-net | Komunikasi Internal Service |
Layer, Cache Layer, Monitoring Layer, dan Object Storage Layer.

Arsitektur ini lebih aman, mudah dikelola, dan memiliki performa yang lebih baik dibandingkan deployment monolitik (all-in-one server).
