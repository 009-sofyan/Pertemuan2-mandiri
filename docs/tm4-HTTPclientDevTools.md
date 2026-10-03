# TM-4 — HTTP Client + DevTools

Entity: Mahasiswa

## Base API

BASE=https://silab.ft.unira.ac.id/api/v1

## A. Postman GET $BASE

### Request

```text
GET https://silab.ft.unira.ac.id/api/v1

Request menggunakan method GET ke endpoint $BASE.

Hasil Pengujian
HTTP/1.1 301 Moved Permanently
Location: /api/v1/

Status 301 Moved Permanently menunjukkan bahwa endpoint /api/v1 mengarahkan request ke /api/v1/.

Setelah diarahkan ke /api/v1/, response yang diterima berupa halaman HTML pemberitahuan dari Universitas Madura. Halaman tersebut menjelaskan bahwa SILAB telah berpindah ke ATLAS.

Isi response menunjukkan:

SILAB telah berpindah ke ATLAS

Layanan di silab.ft.unira.ac.id sudah dialihkan ke alamat baru
atlas.unira.ac.id.

Silakan perbarui bookmark Anda.

Alamat sistem baru yang ditampilkan pada response adalah:

https://atlas.unira.ac.id

Response HTML juga menyediakan tombol "Lanjut ke ATLAS Sekarang" dan pengalihan otomatis menuju ATLAS.

Pada Postman, bagian Pretty digunakan untuk melihat isi response HTML, sedangkan bagian Headers digunakan untuk melihat informasi header HTTP seperti status code, content type, server, dan informasi lainnya.

Kesimpulan A

Pengujian GET $BASE menunjukkan bahwa endpoint /api/v1 memberikan status 301 Moved Permanently dan mengarahkan request ke /api/v1/. Setelah diarahkan, halaman memberikan informasi bahwa layanan SILAB Universitas Madura telah berpindah ke sistem baru yaitu ATLAS pada https://atlas.unira.ac.id.

B. DevTools Network
## B. DevTools Network

Halaman yang digunakan:

```text
https://atlas.unira.ac.id/mahasiswa

Pengujian dilakukan menggunakan Chrome DevTools pada tab Network untuk melihat request API yang dikirim oleh halaman mahasiswa.

Pada Network, filter /api/v1 digunakan untuk menampilkan request yang menggunakan endpoint API. Salah satu request yang ditemukan adalah request GraphQL dengan hasil sebagai berikut:

Keterangan	Hasil
Request URL	https://silab.ft.unira.ac.id/api/v1/graphql
Request Method	POST
Status Code	200 OK
Type	XHR

Request tersebut menggunakan method POST menuju endpoint /api/v1/graphql dan mendapatkan status 200 OK. Status 200 OK menunjukkan bahwa request berhasil diproses oleh server.

Pada bagian Response Headers juga terlihat:

Access-Control-Allow-Origin: https://atlas.unira.ac.id
Access-Control-Allow-Credentials: true

Hal tersebut menunjukkan bahwa server mengizinkan request dari origin https://atlas.unira.ac.id.

Kesimpulan B

Berdasarkan pengujian DevTools Network, halaman mahasiswa melakukan request API menuju https://silab.ft.unira.ac.id/api/v1/graphql menggunakan method POST. Request tersebut mendapatkan status 200 OK, sehingga request berhasil diproses oleh server.

C. curl -i $BASE/salah-ketik
Request
curl.exe -i https://silab.ft.unira.ac.id/api/v1/salah-ketik
Hasil Pengujian
HTTP/1.1 404 Not Found
Server: nginx
Date: Sat, 03 Oct 2026 02:37:00 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 189
Connection: keep-alive
Vary: Accept-Encoding
X-Powered-By: Express
Vary: Origin
Access-Control-Allow-Credentials: true
ETag: W/"bd-WnupPZu2gyTpiwvrUHJ4L+OdxF0"
Response Body
{
  "jsonapi": {
    "version": "1.0"
  },
  "meta": {
    "authors": "Muhammad Umar Mansyur",
    "copyright": "2023 ~ Silab Informatika Universitas Madura"
  },
  "status": false,
  "message": "Api atau berkas tidak ditemukan"
}
Hasil Pengujian
Method: GET
Status Code: 404
Status: Not Found
Message: Api atau berkas tidak ditemukan
Server: nginx
Framework: Express

Hasil tersebut menunjukkan bahwa endpoint /api/v1/salah-ketik tidak ditemukan oleh server sehingga server memberikan status 404 Not Found.

Catatan: Instruksi tugas menyebutkan pengujian curl -i $BASE/salah-ketik dengan header 500. Namun, hasil pengujian aktual yang diperoleh adalah 404 Not Found, bukan 500 Internal Server Error. Oleh karena itu, status 500 tidak dibuat-buat atau dituliskan sebagai hasil pengujian.

Perbedaan curl -s dan curl -i

curl -s digunakan untuk menjalankan request dalam mode silent sehingga output tambahan seperti progress meter tidak ditampilkan.

curl -i digunakan untuk menampilkan HTTP response header bersama dengan response body.

Dengan demikian, curl -s lebih sederhana jika hanya ingin melihat hasil response, sedangkan curl -i lebih berguna untuk melihat status code dan informasi header HTTP.

Kesimpulan

TM-4 membahas penggunaan HTTP client melalui Postman, curl, dan DevTools. Pada pengujian GET $BASE, server memberikan status 301 Moved Permanently dan mengarahkan request dari /api/v1 ke /api/v1/. Response selanjutnya memberikan informasi bahwa layanan SILAB telah berpindah ke sistem ATLAS.

Pengujian menggunakan curl pada endpoint /api/v1/salah-ketik menghasilkan status 404 Not Found dengan message Api atau berkas tidak ditemukan. Hasil tersebut menunjukkan bahwa endpoint yang digunakan tidak ditemukan oleh server.

Pengujian DevTools belum dapat dilakukan karena DevTools pada browser yang digunakan tidak dapat dibuka. Oleh karena itu, request /api/v1/... dan status code pada bagian Network tidak dicatat berdasarkan perkiraan.

Semua pengujian menggunakan Base API:

https://silab.ft.unira.ac.id/api/v1