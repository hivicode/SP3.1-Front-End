# UAS Project Perumahan - Backend API

Backend API server untuk aplikasi manajemen perumahan menggunakan Flask dan SQLite.

## 📋 Deskripsi

Backend API yang menyediakan RESTful endpoints untuk:
- Manajemen properti (CRUD)
- Upload dan management gambar properti
- Sistem booking properti
- Admin panel dengan authentication
- Customer management

## 🚀 Quick Start

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Jalankan Server

```bash
python app.py
```

Server akan berjalan di: `http://localhost:701`

## 📁 Struktur File

```
Backend/
├── app.py                 # Main Flask application
├── data.db                # SQLite database (auto-generated)
├── requirements.txt       # Python dependencies
├── templates/             # Admin panel HTML templates
│   ├── admin_base.html
│   ├── admin_index.html
│   ├── admin_customers.html
│   ├── admin_form.html
│   └── login.html
├── static/
│   └── uploads/           # Uploaded property images
└── README.md
```

## 🔌 API Endpoints

### Properti API

#### GET /api/properti
Mendapatkan daftar semua properti.

**Query Parameters:**
- `search` (optional) - Search by nama_rumah or alamat
- `kota` (optional) - Filter by kota
- `tipe` (optional) - Filter by tipe
- `min_harga` (optional) - Minimum harga
- `max_harga` (optional) - Maximum harga

**Response:**
```json
[
  {
    "kode_rumah": "R001",
    "nama_rumah": "Griya Sejahtera",
    "alamat": "Jl. Melati No. 12",
    "kota": "Bandung",
    "tipe": "Rumah",
    "harga": 850000000,
    "rating": 4.5,
    "kamar_tidur": 3,
    "kamar_mandi": 2,
    "luas_tanah": 120,
    "luas_bangunan": 90,
    "garasi": 1,
    "fitur": "AC, WiFi, Carport",
    "deskripsi": "Rumah nyaman dengan taman luas",
    "gambar": ["rumah1.jpg", "rumah2.jpg"]
  }
]
```

#### GET /api/properti/<kode>
Mendapatkan detail properti berdasarkan kode.

**Response:**
```json
{
  "kode_rumah": "R001",
  "nama_rumah": "Griya Sejahtera",
  ...
}
```

#### POST /api/properti
Menambah properti baru.

**Request Body (multipart/form-data):**
- `kode_rumah` (required)
- `nama_rumah` (required)
- `alamat` (required)
- `kota` (required)
- `tipe` (required)
- `harga` (required)
- `kamar_tidur` (required)
- `kamar_mandi` (required)
- `luas_tanah` (required)
- `luas_bangunan` (required)
- `garasi` (required)
- `fitur` (optional)
- `deskripsi` (optional)
- `gambar[]` (optional, multiple files)

#### PUT /api/properti/<kode>
Update properti yang sudah ada.

**Request Body:** Same as POST

#### DELETE /api/properti/<kode>
Menghapus properti dan semua gambar terkait.

### Booking API

#### GET /api/booking
Mendapatkan daftar semua booking.

**Response:**
```json
[
  {
    "id": 1,
    "kode_rumah": "R001",
    "nama_depan": "John",
    "nama_belakang": "Doe",
    "email": "john@example.com",
    "telepon": "081234567890",
    "metode_pembayaran": "Transfer Bank",
    "booking_fee": 5000000,
    "status": "pending",
    "dibuat_pada": "2024-01-15 10:30:00"
  }
]
```

#### POST /api/booking
Membuat booking baru.

**Request Body (JSON):**
```json
{
  "kode_rumah": "R001",
  "nama_depan": "John",
  "nama_belakang": "Doe",
  "email": "john@example.com",
  "telepon": "081234567890",
  "metode_pembayaran": "Transfer Bank",
  "booking_fee": 5000000
}
```

#### PATCH /api/booking/<id>/status
Update status booking.

**Request Body (JSON):**
```json
{
  "status": "approved"
}
```

Status yang valid: `pending`, `approved`, `rejected`

### Upload API

#### GET /uploads/<filename>
Download gambar properti.

## 🔐 Admin Panel

### Routes

- `GET /admin` - Dashboard admin (requires login)
- `GET /admin/customers` - Daftar customer/properti
- `GET /admin/add` - Form tambah properti
- `POST /admin/add` - Submit tambah properti
- `GET /admin/edit/<kode>` - Form edit properti
- `POST /admin/edit/<kode>` - Submit edit properti
- `POST /admin/delete/<kode>` - Hapus properti
- `GET /admin/booking/<id>/status` - Update status booking
- `GET /login` - Halaman login
- `POST /login` - Submit login
- `GET /logout` - Logout

### Authentication

Default credentials:
- **Username**: `admin`
- **Password**: `admin`

⚠️ Ganti credentials ini untuk production!

## 🗄️ Database Schema

### Tabel `properti`
```sql
CREATE TABLE properti (
    kode_rumah TEXT PRIMARY KEY,
    nama_rumah TEXT NOT NULL,
    alamat TEXT NOT NULL,
    kota TEXT NOT NULL,
    tipe TEXT NOT NULL,
    harga INTEGER NOT NULL,
    rating REAL DEFAULT 0,
    kamar_tidur INTEGER NOT NULL,
    kamar_mandi INTEGER NOT NULL,
    luas_tanah INTEGER NOT NULL,
    luas_bangunan INTEGER NOT NULL,
    garasi INTEGER NOT NULL,
    fitur TEXT,
    deskripsi TEXT
);
```

### Tabel `properti_gambar`
```sql
CREATE TABLE properti_gambar (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    kode_rumah TEXT NOT NULL,
    filename TEXT NOT NULL,
    FOREIGN KEY (kode_rumah) REFERENCES properti(kode_rumah) ON DELETE CASCADE
);
```

### Tabel `booking`
```sql
CREATE TABLE booking (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    kode_rumah TEXT NOT NULL,
    nama_depan TEXT NOT NULL,
    nama_belakang TEXT NOT NULL,
    email TEXT NOT NULL,
    telepon TEXT NOT NULL,
    metode_pembayaran TEXT NOT NULL,
    booking_fee INTEGER NOT NULL,
    status TEXT NOT NULL DEFAULT 'pending',
    dibuat_pada TEXT NOT NULL,
    FOREIGN KEY (kode_rumah) REFERENCES properti(kode_rumah) ON DELETE CASCADE
);
```

## ⚙️ Konfigurasi

### Database
Database SQLite akan dibuat otomatis di `data.db` saat pertama kali dijalankan.

### Upload Directory
File upload disimpan di `static/uploads/`. Folder akan dibuat otomatis jika belum ada.

### Allowed File Extensions
- jpg, jpeg, png, gif, webp

### CORS
CORS diaktifkan untuk semua origin. Untuk production, batasi origin yang diizinkan.

### Secret Key
Default secret key: `secret123`

⚠️ Ganti secret key untuk production!

## 📦 Dependencies

```
Flask==3.0.3
Flask-Cors==6.0.2
Werkzeug==3.0.3
```

## 🔧 Development

### Menambah Endpoint Baru

1. Tambah route di `app.py`:
```python
@app.route("/api/endpoint", methods=["GET"])
def new_endpoint():
    # Your code here
    return jsonify({"message": "Success"})
```

2. Test menggunakan Postman atau curl

### Database Migration

Untuk menambah kolom baru:
1. Update `init_db()` function
2. Tambah migration logic untuk existing database

## 🧪 Testing

### Test API dengan curl

```bash
# Get all properties
curl http://localhost:701/api/properti

# Get property by code
curl http://localhost:701/api/properti/R001

# Create booking
curl -X POST http://localhost:701/api/booking \
  -H "Content-Type: application/json" \
  -d '{
    "kode_rumah": "R001",
    "nama_depan": "John",
    "nama_belakang": "Doe",
    "email": "john@example.com",
    "telepon": "081234567890",
    "metode_pembayaran": "Transfer Bank",
    "booking_fee": 5000000
  }'
```

## ⚠️ Catatan Penting

- Database SQLite cocok untuk development, untuk production pertimbangkan PostgreSQL atau MySQL
- File upload tidak ada validasi ukuran file (tambahkan untuk production)
- Secret key harus diganti untuk production
- Admin credentials harus diganti untuk production
- Implementasi rate limiting untuk mencegah abuse

## 🔐 Security Best Practices

Untuk production:
- ✅ Ganti secret key dengan random string
- ✅ Implementasi password hashing (bcrypt)
- ✅ Validasi dan sanitasi semua input
- ✅ Rate limiting untuk API endpoints
- ✅ HTTPS untuk komunikasi
- ✅ Validasi file upload (size, type, content)
- ✅ SQL injection prevention (gunakan parameterized queries)
- ✅ CORS configuration yang lebih ketat
