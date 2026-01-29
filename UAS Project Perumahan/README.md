# UAS Project Perumahan

Aplikasi final project untuk sistem manajemen perumahan dengan arsitektur terpisah antara Backend API dan Frontend.

## Deskripsi

Aplikasi web lengkap untuk mengelola properti perumahan dengan fitur:
- **Manajemen Properti**: CRUD lengkap untuk data rumah/properti
- **Sistem Booking**: Pelanggan dapat melakukan booking properti
- **Admin Panel**: Dashboard admin untuk mengelola properti dan booking
- **Upload Gambar**: Multiple image upload untuk setiap properti
- **API RESTful**: Backend API terpisah dengan CORS support

## Arsitektur

Aplikasi ini menggunakan arsitektur terpisah (separated architecture):
- **Backend**: Flask API server dengan SQLite database (Port 701)
- **Frontend**: Static HTML/CSS/JS dengan Flask static server (Port 702)

## Struktur Folder

```
UAS Project Perumahan/
+-- README.md
+-- Backend/
   +-- app.py              # Flask API server
   +-- data.db             # SQLite database
   +-- requirements.txt    # Python dependencies
   +-- templates/          # Admin panel templates
   +-- static/
      +-- uploads/        # Uploaded property images
   +-- README.md
+-- Frontend/
    +-- app.py              # Flask static server
    +-- index.html          # Homepage
    +-- listing.html        # Property listing
    +-- property.html       # Property detail
    +-- checkout.html       # Booking form
    +-- contact.html        # Contact page
    +-- css/                # Stylesheets
    +-- js/                 # JavaScript files
    +-- components/         # Reusable HTML components
    +-- README.md
```

## Quick Start

### 1. Setup Backend

```bash
cd Backend
pip install -r requirements.txt
python app.py
```

Backend akan berjalan di: `http://localhost:701`

### 2. Setup Frontend

```bash
cd Frontend
python app.py
```

Frontend akan berjalan di: `http://localhost:702`

### 3. Akses Aplikasi

- **Frontend (Customer)**: http://localhost:702
- **Backend API**: http://localhost:701/api
- **Admin Panel**: http://localhost:701/admin

## Login Admin

Default credentials untuk admin panel:
- **Username**: `admin`
- **Password**: `admin`

 **PENTING**: Ganti credentials ini untuk production!

## API Endpoints

### Properti

- `GET /api/properti` - Daftar semua properti
- `GET /api/properti/<kode>` - Detail properti
- `POST /api/properti` - Tambah properti baru
- `PUT /api/properti/<kode>` - Update properti
- `DELETE /api/properti/<kode>` - Hapus properti

### Booking

- `GET /api/booking` - Daftar semua booking
- `POST /api/booking` - Buat booking baru
- `PATCH /api/booking/<id>/status` - Update status booking

### Upload

- `GET /uploads/<filename>` - Download gambar properti

## Database Schema

### Tabel `properti`
- `kode_rumah` (PRIMARY KEY)
- `nama_rumah`, `alamat`, `kota`, `tipe`
- `harga`, `rating`
- `kamar_tidur`, `kamar_mandi`
- `luas_tanah`, `luas_bangunan`, `garasi`
- `fitur`, `deskripsi`

### Tabel `properti_gambar`
- `id` (PRIMARY KEY)
- `kode_rumah` (FOREIGN KEY)
- `filename`

### Tabel `booking`
- `id` (PRIMARY KEY)
- `kode_rumah` (FOREIGN KEY)
- `nama_depan`, `nama_belakang`
- `email`, `telepon`
- `metode_pembayaran`, `booking_fee`
- `status` (pending/approved/rejected)
- `dibuat_pada`

## Teknologi

### Backend
- **Flask** 3.0.3 - Web framework
- **Flask-CORS** 6.0.2 - CORS support
- **SQLite3** - Database
- **Werkzeug** 3.0.3 - File upload handling

### Frontend
- **HTML5** - Markup
- **CSS3** - Styling
- **JavaScript (Vanilla)** - Interactivity
- **Bootstrap** - UI framework (via CDN)

## Fitur Utama

### Customer Features
-  Browse properti perumahan
-  Filter dan search properti
-  Detail properti dengan multiple images
-  Booking form dengan validasi
-  Contact page

### Admin Features
-  Login/Logout system
-  Dashboard overview
-  CRUD properti lengkap
-  Upload multiple images per properti
-  Kelola booking (approve/reject)
-  Customer management

## Konfigurasi

### Backend Configuration

Database SQLite akan dibuat otomatis di `Backend/data.db` saat pertama kali dijalankan.

Upload directory: `Backend/static/uploads/`

### Frontend Configuration

Frontend mengakses API di `http://localhost:701` (default). Jika backend berjalan di port berbeda, edit file JavaScript di folder `Frontend/js/`.

## Dependencies

### Backend
```
Flask==3.0.3
Flask-Cors==6.0.2
Werkzeug==3.0.3
```

### Frontend
Tidak ada dependencies Python, hanya static files.

## Cara Menggunakan

1. **Jalankan Backend terlebih dahulu**
   ```bash
   cd Backend
   python app.py
   ```

2. **Jalankan Frontend di terminal terpisah**
   ```bash
   cd Frontend
   python app.py
   ```

3. **Akses aplikasi**
   - Buka browser ke http://localhost:702 untuk customer view
   - Buka http://localhost:701/admin untuk admin panel

4. **Login sebagai admin**
   - Username: `admin`
   - Password: `admin`

## Catatan Penting

- Backend dan Frontend harus berjalan bersamaan
- Pastikan port 701 dan 702 tidak digunakan aplikasi lain
- Database SQLite akan dibuat otomatis saat pertama kali dijalankan
- File upload disimpan di `Backend/static/uploads/`
- Ganti secret key dan admin credentials untuk production

## Keamanan

Untuk production, pastikan:
-  Ganti `secret_key` di Backend
-  Ganti default admin credentials
-  Implementasi password hashing
-  Validasi input yang lebih ketat
-  Rate limiting untuk API
-  HTTPS untuk komunikasi

## Dokumentasi Lebih Lanjut

- [Backend README](Backend/README.md) - Dokumentasi detail Backend API
- [Frontend README](Frontend/README.md) - Dokumentasi detail Frontend

## Development

### Menambah Fitur Baru

1. **Backend API**: Tambah route di `Backend/app.py`
2. **Frontend**: Update JavaScript di `Frontend/js/` untuk consume API baru
3. **Database**: Update schema jika perlu di `init_db()` function

### Testing

- Test API endpoints menggunakan Postman atau curl
- Test Frontend dengan membuka di browser
- Test admin panel dengan login

## License

Project ini dibuat untuk keperluan pembelajaran UAS.
