# TM-1 — Peta Routing Pribadi

Entity: Mahasiswa

## Base API

BASE=https://silab.ft.unira.ac.id/api/v1

## Peta Routing

| METHOD + API | SvelteKit File | ATLAS SPA | Flutter name + args | US |
|---|---|---|---|---|
| GET /api/v1/mahasiswa | routes/mahasiswa/+page.svelte | /mahasiswa | getMahasiswa() | US-01 |
| GET /api/v1/mahasiswa/:id | routes/mahasiswa/[id]/+page.svelte | /mahasiswa/:id | getMahasiswaDetail(id) | US-02 |
| POST /api/v1/mahasiswa | routes/mahasiswa/baru/+page.svelte | /mahasiswa/baru | createMahasiswa(data) | US-03 |
| PUT /api/v1/mahasiswa/:id | routes/mahasiswa/[id]/edit/+page.svelte | /mahasiswa/:id/edit | updateMahasiswa(id, data) | US-04 |
| DELETE /api/v1/mahasiswa/:id | routes/mahasiswa/[id]/+page.svelte | /mahasiswa/:id | deleteMahasiswa(id) | US-05 |

## Authorization

- US-01: authorize(Kaprodi, Tendik)
- US-02: canAccess()
- US-03: authorize(Tendik)
- US-04: authorize(Tendik)
- US-05: authorize(Tendik)

## Keterangan

- `[id]` digunakan untuk route data mahasiswa berdasarkan ID.
- `baru` digunakan untuk route penambahan mahasiswa baru.
- `GET` digunakan untuk mengambil data mahasiswa.
- `POST` digunakan untuk menambahkan data mahasiswa.
- `PUT` digunakan untuk mengubah data mahasiswa.
- `DELETE` digunakan untuk menghapus data mahasiswa.
- Semua endpoint menggunakan prefix `/api/v1`.
- ID mahasiswa yang digunakan pada route `[id]` masih berupa parameter dan belum menggunakan ID asli.