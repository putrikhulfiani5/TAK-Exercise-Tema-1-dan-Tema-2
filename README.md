# API Testing - Authors

---

## Base URL
https://fakerestapi.azurewebsites.net

---

## Tools
1. Katalon Studio
2. API (Authors)

---

## Deskripsi
Project ini berisi automation testing API menggunakan Katalon Studio untuk endpoint Authors API.
Testing dilakukan untuk memastikan setiap endpoint (GET, POST, PUT, DELETE) berjalan dengan baik sesuai expected behavior. 

---

## Scope Testing
Endpoint yang diuji:
1. GET All Authors
2. GET Authors by idBook
3. GET Authors by ID
4. POST Authors
5. PUT Authors
6. Delete Authors

---

## Details Test Case
### TC01 - GET All Authors
- **Request:** /api/v1/Authors
- **Response:**
```json
[
  {
    "id":1,
    "idBook":1,
    "firstName":"First Name 1",
    "lastName":"Last Name 1"
  }
]
```
- **Tujuan:**
Memastikan API dapat mengambil seluruh data authors
- **Langkah:**
1. Kirim request GET ke endpoint /authors
2. Verifikasi status code = 200
3. Validasi response tidak kosong

### TC02 - GET Authors by idBook
- **Request:** /api/v1/Authors/authors/books/${idBook}
- **Response:**
```json
[
  {
    "id":1,
    "idBook":1,
    "firstName":"First Name 1",
    "lastName":"Last Name 1"
  },
  {
    "id":2,
    "idBook":1,
    "firstName":"First Name 2",
    "lastName":"Last Name 2"
  }
]
```
- **Tujuan:**
Memastikan API dapat mengambil data berdasarkan idBook
- **Langkah:**
1. Kirim request GET /authors?idBook=200
2. Verifikasi status code = 200
3. Validasi field idBook sesuai dengan request

### TC03 - GET Authors by ID
- **Request:** /api/v1/Authors/${id}
- **Response:** 
```json
{
  "id":200,
  "idBook":68,
  "firstName":"First Name 200",
  "lastName":"Last Name 200"
}
```
- **Tujuan:**
Memastikan API dapat mengambil data berdasarkan ID
- **Langkah:**
1. Kirim request GET /authors/{id}
2. Verifikasi status code = 200
3. Validasi id sesuai dengan request

### TC04 - POST Authors
- **Request:** /api/v1/Authors
- **Response:**
```json
{
  "id":999,
  "idBook":999,
  "firstName":"Putri",
  "lastName":"Malu"
}
```
- **Tujuan:**
Memastikan API dapat menambahkan data baru
- **Langkah:**
1. Kirim request POST dengan body JSON
2. Verifikasi status code (200/201)
3. Validasi data yang dikirim tersimpan dengan benar

### TC05 - PUT Authors
- **Request:** /api/v1/Authors/${id}
- **Response:** 
```json
{
  "id":1,
  "idBook":1,
  "firstName":"Putri",
  "lastName":"Update"
}
```
- **Tujuan:**
Memastikan API dapat mengupdate data
- **Langkah:**
1. Kirim request PUT ke /authors/{id}
2. Verifikasi status code = 200
3. Validasi data berhasil diupdate

### TC06 - DELETE Authors
- **Request:** /api/v1/Authors/${id}
- **Response:** 200 OK
- **Tujuan:**
Memastikan API dapat menghapus data
- **Langkah:**
1. Kirim request DELETE /authors/{id}
2. Verifikasi status code (200/204)
3. Validasi data sudah terhapus (GET -> 404)

---

## Cara Menjalankan Test
1. Buka project di Katalon Studio
2. Jalankan Test Suite: TS_Authors-API
3. Lihat hasil di tab Log Viewer

---

## Hasil Testing 
Semua test case berhasil dijalankan dengan status: 
- PASSED: 6
- FAILED: 0
- TOTAL: 6  

---

## Catatan
1. Status code POST dapat berupa 200 atau 201 tergantung API
2. Response DELETE bisa kosong (normal behavior)
