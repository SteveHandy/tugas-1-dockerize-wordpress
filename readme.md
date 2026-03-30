# WordPress Docker Orchestration with MySQL & Redis

## Dokumentasi (Screenshots)

### 1. Halaman Instalasi WordPress

Akses pertama kali di http://localhost:8000.

![Halaman Instalasi WordPress](images/install-page.png)

### 2. Dashboard WordPress

Tampilan admin panel setelah instalasi berhasil.

![Dashboard WordPress](images/wp-dashboard.png)

### 3. Docker Containers Running

Output dari perintah `docker ps`, menunjukkan 3 container (wordpress, mysql, redis) berjalan normal.

![Docker PS Output](images/docker-ps.png)

### 4. Redis CLI Ping Test

Uji koneksi ke Redis container menggunakan `redis-cli ping` yang menghasilkan balasan `PONG`.

![Redis Ping Test](images/redis-ping.png)

## Q&A

## 1. Kenapa perlu volume untuk MySQL?

Agar data database tetap **persisten** dan tidak hilang saat container dihapus atau restart.

---

## 2. Apa fungsi `depends_on`?

Mengatur **urutan startup container**, tapi **tidak menjamin service sudah siap digunakan**.

---

## 3. Bagaimana WordPress connect ke MySQL?

Menggunakan **Docker Internal DNS** dengan nama service sebagai hostname:

```env
WORDPRESS_DB_HOST=mysql:3306
```

---

## 4. Apa keuntungan pakai Redis?

Sebagai **object cache di RAM** untuk:

- Mengurangi query ke MySQL
- Mempercepat loading WordPress

---
