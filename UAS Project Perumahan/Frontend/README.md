# UAS Project Perumahan - Frontend

Frontend aplikasi manajemen perumahan dengan HTML, CSS, dan JavaScript vanilla.

## Deskripsi

Frontend static website untuk customer yang menampilkan:
- Homepage dengan hero section
- Property listing dengan filter
- Property detail page
- Booking form
- Contact page

## Quick Start

### 1. Pastikan Backend Berjalan

Backend harus berjalan di `http://localhost:701` sebelum menjalankan frontend.

### 2. Jalankan Frontend Server

```bash
python app.py
```

Frontend akan berjalan di: `http://localhost:702`

## Struktur File

```
Frontend/
+-- app.py                 # Flask static server
+-- index.html             # Homepage
+-- listing.html           # Property listing page
+-- property.html          # Property detail page
+-- checkout.html          # Booking form
+-- contact.html           # Contact page
+-- css/                   # Stylesheets
   +-- index.css
   +-- listing.css
   +-- rent.css
   +-- contact.css
+-- js/                    # JavaScript files
   +-- script.js          # Main JavaScript
   +-- properties.js      # Property listing logic
   +-- rent.js            # Booking logic
+-- components/            # Reusable HTML components
   +-- header.html
   +-- header-minimal.html
   +-- footer.html
+-- README.md
```

## Halaman

### 1. Homepage (`index.html`)
- Hero section dengan CTA
- Featured properties
- About section
- Contact information

### 2. Property Listing (`listing.html`)
- Daftar semua properti
- Filter by kota, tipe, harga
- Search functionality
- Responsive grid layout

### 3. Property Detail (`property.html`)
- Detail lengkap properti
- Image gallery
- Property specifications
- Booking button

### 4. Booking Form (`checkout.html`)
- Form booking dengan validasi
- Input customer data
- Payment method selection
- Submit booking ke API

### 5. Contact Page (`contact.html`)
- Contact information
- Contact form (optional)

## API Integration

Frontend mengonsumsi API dari Backend di `http://localhost:701/api`.

### Endpoints yang Digunakan

- `GET /api/properti` - Get all properties
- `GET /api/properti/<kode>` - Get property detail
- `POST /api/booking` - Create booking

### JavaScript Files

#### `script.js`
Main JavaScript file dengan utility functions.

#### `properties.js`
- Fetch properties from API
- Filter and search functionality
- Display properties in grid

#### `rent.js`
- Property detail page logic
- Booking form handling
- Form validation
- Submit booking to API

## Fitur

### Property Listing
-  Display all properties
-  Filter by kota
-  Filter by tipe
-  Filter by price range
-  Search by name/address
-  Responsive design

### Property Detail
-  Show property information
-  Image gallery
-  Property specifications
-  Booking button

### Booking
-  Form validation
-  Customer data input
-  Payment method selection
-  Submit to API
-  Success/error handling

## Teknologi

- **HTML5** - Markup
- **CSS3** - Styling
- **JavaScript (Vanilla)** - Interactivity
- **Bootstrap** - UI framework (via CDN)
- **Flask** - Static file server

## Konfigurasi

### API Base URL

Default API URL: `http://localhost:701`

Jika backend berjalan di URL/port berbeda, edit file JavaScript:
- `js/properties.js`
- `js/rent.js`
- `js/script.js`

### Port

Default port: `702`

Untuk mengubah port, edit `app.py`:
```python
app.run(port=702, debug=True)
```

## Cara Menggunakan

### 1. Jalankan Backend
```bash
cd ../Backend
python app.py
```

### 2. Jalankan Frontend
```bash
python app.py
```

### 3. Buka Browser
Akses: `http://localhost:702`

## Styling

### CSS Files

- `css/index.css` - Homepage styles
- `css/listing.css` - Listing page styles
- `css/rent.css` - Property detail & booking styles
- `css/contact.css` - Contact page styles

### Bootstrap

Bootstrap 5.3.0 digunakan via CDN untuk:
- Grid system
- Components (cards, buttons, forms)
- Responsive utilities

## Development

### Menambah Halaman Baru

1. Buat file HTML baru di root folder
2. Include components (header, footer)
3. Tambah CSS jika perlu
4. Tambah JavaScript jika perlu
5. Update navigation links

### Menambah Fitur JavaScript

1. Edit file JavaScript yang sesuai atau buat file baru
2. Include script tag di HTML
3. Test functionality

### Styling

1. Edit CSS file yang sesuai
2. Gunakan Bootstrap classes untuk consistency
3. Test responsive design

## Testing

### Manual Testing

1. **Property Listing**
   - Test filter functionality
   - Test search
   - Test responsive layout

2. **Property Detail**
   - Test image display
   - Test booking button

3. **Booking Form**
   - Test form validation
   - Test form submission
   - Test success/error messages

### Browser Compatibility

Test di browser:
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Catatan Penting

- Backend harus berjalan sebelum frontend
- Pastikan CORS diaktifkan di backend
- API URL harus sesuai dengan backend
- Test semua form validation
- Test responsive design di berbagai device

## Troubleshooting

### Properties tidak muncul
- Pastikan backend berjalan
- Check browser console untuk error
- Verify API URL di JavaScript

### Booking tidak submit
- Check form validation
- Check browser console untuk error
- Verify API endpoint di backend

### Styling tidak muncul
- Check CSS file paths
- Check Bootstrap CDN connection
- Clear browser cache

## Responsive Design

Frontend dirancang responsive untuk:
- Desktop (1920px+)
- Laptop (1024px - 1919px)
- Tablet (768px - 1023px)
- Mobile (< 768px)

## Future Improvements

- [ ] Add loading states
- [ ] Add error handling UI
- [ ] Add pagination for properties
- [ ] Add image lazy loading
- [ ] Add form autocomplete
- [ ] Add booking confirmation page
- [ ] Add user account system
- [ ] Add favorites/wishlist
