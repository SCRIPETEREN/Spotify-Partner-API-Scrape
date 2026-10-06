# Spotify Partner API Scraper - Search, Track, Album, Artist Metadata

> **GitHub Repository Title**
>
> ```text
> Spotify Partner API Scraper - Search, Track, Album, Artist Metadata
> ```
>
> **Repository Name**
>
> ```text
> spotify-partner-api-scraper
> ```
>
> **GitHub Repository Description**
>
> ```text
> Node.js ESM CLI scraper for Spotify public metadata. Search tracks, albums, and artists, retrieve track metadata, full album track lists, artist data, cover art, Spotify URLs, and available preview URLs in JSON format.
> ```

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-18%2B-339933?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js">
  <img src="https://img.shields.io/badge/JavaScript-ESM-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript ESM">
  <img src="https://img.shields.io/badge/Spotify-Metadata-1DB954?style=for-the-badge&logo=spotify&logoColor=white" alt="Spotify">
  <img src="https://img.shields.io/badge/Creator-SCRIPETEREN-181717?style=for-the-badge&logo=github&logoColor=white" alt="Creator">
</p>

<p align="center">
  <b>Node.js ESM CLI scraper untuk pencarian dan metadata Spotify.</b><br>
  Mengambil hasil search, detail track, full album track list, detail artist, cover art, Spotify URI, Spotify URL, informasi playability, dan preview URL apabila tersedia.
</p>

---

## Fitur

- Search track Spotify berdasarkan keyword
- Search album Spotify berdasarkan keyword
- Search artist Spotify berdasarkan keyword
- Mengambil top result pencarian Spotify
- Mengambil metadata track
- Mengambil metadata album
- Mengambil daftar lengkap track dalam album
- Mengambil metadata artist
- Mengambil track list artist jika tersedia pada Spotify embed entity
- Mengambil Spotify track ID
- Mengambil Spotify album ID
- Mengambil Spotify artist ID
- Mengambil Spotify URI
- Mengambil Spotify open URL
- Mengambil judul track
- Mengambil nama artist track
- Mengambil nama album
- Mengambil album ID
- Mengambil album cover
- Mengambil explicit status
- Mengambil durasi track
- Mengambil status playable track
- Mengambil playability reason
- Mengambil release date album
- Mengambil jumlah track album
- Mengambil avatar artist
- Mengambil subtitle artist jika tersedia
- Mengambil preview audio URL apabila disediakan Spotify
- Mendukung Spotify ID
- Mendukung Spotify URI
- Mendukung Spotify URL
- Mendukung pagination search dengan `--offset`
- Mendukung limit hasil dengan `--limit`
- Retry otomatis untuk temporary HTTP error
- Timeout request
- Rotasi User-Agent
- Anonymous session token cache
- Client token cache
- Refresh token saat session expired
- Fallback persisted GraphQL hash untuk search
- Verbose HTTP log
- Menyimpan hasil JSON melalui opsi `--out`
- Dapat digunakan sebagai CLI atau ESM module

---

## Teknologi

Project ini menggunakan:

- [Node.js](https://nodejs.org/) 18 atau lebih baru
- Native `fetch()` Node.js
- `node:fs/promises`
- `node:util`
- `AbortController`
- JavaScript ESM Module
- Spotify embed page
- Spotify metadata entity
- Spotify partner endpoint untuk pencarian

Node.js versi 18 atau lebih baru diperlukan karena script menggunakan global `fetch()` bawaan Node.js.

---

## Struktur Project

```text
spotify-partner-api-scraper/
├── spotify.js
├── package.json
├── .gitignore
├── README.md
└── LICENSE
```

---

## Instalasi

Clone repository:

```bash
git clone [https://github.com/SCRIPETEREN/spotify-partner-api-scraper.git](https://github.com/SCRIPETEREN/spotify-partner-api-scraper.git)
```

Masuk ke folder repository:

```bash
cd spotify-partner-api-scraper
```

Cek versi Node.js:

```bash
node -v
```

Gunakan Node.js minimal versi 18:

```text
v18.0.0
```

Versi yang direkomendasikan:

```text
v20.x.x
```

```text
v22.x.x
```

Project ini tidak memerlukan package eksternal untuk fungsi metadata dasar karena menggunakan module bawaan Node.js.

---

## package.json

Buat file `package.json` dengan isi berikut:

```json
{
  "name": "spotify-partner-api-scraper",
  "version": "1.0.0",
  "description": "Node.js ESM CLI scraper untuk pencarian dan metadata Spotify.",
  "type": "module",
  "main": "spotify.js",
  "scripts": {
    "start": "node spotify.js",
    "help": "node spotify.js"
  },
  "keywords": [
    "spotify",
    "spotify-search",
    "spotify-scraper",
    "spotify-metadata",
    "track-metadata",
    "album-metadata",
    "artist-metadata",
    "nodejs",
    "esm"
  ],
  "author": "SCRIPETEREN",
  "license": "MIT",
  "engines": {
    "node": ">=18.0.0"
  }
}
```

Menampilkan usage command:

```bash
npm start
```

Atau:

```bash
node spotify.js
```

---

## Cara Penggunaan

Format dasar:

```bash
node spotify.js <command> <id|uri|url|keyword> [options]
```

Command yang tersedia:

```text
search
track
album
artist
```

Format lengkap:

```bash
node spotify.js search <term> [--limit 10] [--offset 0] [--out file.json] [--verbose]
```

```bash
node spotify.js track <id|uri|url> [--out file.json] [--verbose]
```

```bash
node spotify.js album <id|uri|url> [--out file.json] [--verbose]
```

```bash
node spotify.js artist <id|uri|url> [--out file.json] [--verbose]
```

---

## Daftar Command

| Command | Fungsi | Contoh |
|---|---|---|
| `search <keyword>` | Mencari track, album, artist, dan top results | `node spotify.js search "Hindia"` |
| `track <id|uri|url>` | Mengambil metadata lengkap satu track | `node spotify.js track 4cOdK2wGLETKBW3PvgPWqT` |
| `album <id|uri|url>` | Mengambil metadata album dan seluruh track album | `node spotify.js album 2up3OPMp9Tb4dAKM2erWXQ` |
| `artist <id|uri|url>` | Mengambil metadata artist dan track yang tersedia | `node spotify.js artist 0TnOYISbd1XYRBk9myaseg` |

---

## Search Spotify

Gunakan command `search` untuk mencari track, album, artist, serta top results.

Format:

```bash
node spotify.js search "<keyword>"
```

Contoh:

```bash
node spotify.js search "Hindia"
```

```bash
node spotify.js search "Arctic Monkeys"
```

```bash
node spotify.js search "The Weeknd"
```

```bash
node spotify.js search "Lana Del Rey"
```

Membatasi jumlah hasil:

```bash
node spotify.js search "Hindia" --limit 5
```

Menggunakan offset untuk pagination:

```bash
node spotify.js search "Hindia" --limit 10 --offset 10
```

Menyimpan hasil search ke JSON:

```bash
node spotify.js search "Hindia" --limit 10 --out search-hindia.json
```

Menampilkan HTTP logs:

```bash
node spotify.js search "Hindia" --verbose
```

Atau:

```bash
node spotify.js search "Hindia" -v
```

---

## Output Search

Contoh output:

```json
{
  "term": "Hindia",
  "totalTracks": 100,
  "tracks": [
    {
      "id": "track_id",
      "spotifyUri": "spotify:track:track_id",
      "url": "[https://open.spotify.com/track/track_id](https://open.spotify.com/track/track_id)",
      "title": "Nama Lagu",
      "artists": [
        "Nama Artist"
      ],
      "album": "Nama Album",
      "albumId": "album_id",
      "albumCover": "[https://i.scdn.co/image/example](https://i.scdn.co/image/example)",
      "isExplicit": false,
      "durationMs": 210000,
      "isPlayable": true,
      "playabilityReason": null,
      "audioPreviewUrl": null
    }
  ],
  "albums": [
    {
      "id": "album_id",
      "name": "Nama Album",
      "artists": [
        "Nama Artist"
      ],
      "coverArt": "[https://i.scdn.co/image/example](https://i.scdn.co/image/example)",
      "year": 2025,
      "uri": "spotify:album:album_id"
    }
  ],
  "artists": [
    {
      "id": "artist_id",
      "name": "Nama Artist",
      "uri": "spotify:artist:artist_id",
      "avatar": "[https://i.scdn.co/image/example](https://i.scdn.co/image/example)"
    }
  ],
  "top": [],
  "raw_meta": null
}
```

---

## Metadata Track

Gunakan command `track` untuk mengambil metadata sebuah track.

Format:

```bash
node spotify.js track <id|uri|url>
```

Contoh menggunakan track ID:

```bash
node spotify.js track 4cOdK2wGLETKBW3PvgPWqT
```

Contoh menggunakan Spotify URI:

```bash
node spotify.js track spotify:track:4cOdK2wGLETKBW3PvgPWqT
```

Contoh menggunakan Spotify URL:

```bash
node spotify.js track [https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT](https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT)
```

Contoh menggunakan Spotify URL yang memiliki query parameter:

```bash
node spotify.js track "[https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT?si=example](https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT?si=example)"
```

Menyimpan hasil:

```bash
node spotify.js track 4cOdK2wGLETKBW3PvgPWqT --out track.json
```

Contoh output:

```json
{
  "id": "4cOdK2wGLETKBW3PvgPWqT",
  "spotifyUri": "spotify:track:4cOdK2wGLETKBW3PvgPWqT",
  "url": "[https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT](https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT)",
  "title": "Sweet Child O' Mine",
  "artists": [
    "Guns N' Roses"
  ],
  "album": "Appetite For Destruction",
  "albumId": "28yHV3Gdg30AiB8h8em1eW",
  "albumCover": "[https://i.scdn.co/image/example](https://i.scdn.co/image/example)",
  "isExplicit": false,
  "durationMs": 356000,
  "isPlayable": true,
  "playabilityReason": null,
  "audioPreviewUrl": null
}
```

---

## Metadata Album

Gunakan command `album` untuk mengambil metadata album beserta track list.

Format:

```bash
node spotify.js album <id|uri|url>
```

Contoh menggunakan album ID:

```bash
node spotify.js album 2up3OPMp9Tb4dAKM2erWXQ
```

Contoh menggunakan Spotify URI:

```bash
node spotify.js album spotify:album:2up3OPMp9Tb4dAKM2erWXQ
```

Contoh menggunakan Spotify URL:

```bash
node spotify.js album [https://open.spotify.com/album/2up3OPMp9Tb4dAKM2erWXQ](https://open.spotify.com/album/2up3OPMp9Tb4dAKM2erWXQ)
```

Menyimpan metadata album:

```bash
node spotify.js album 2up3OPMp9Tb4dAKM2erWXQ --out album.json
```

Contoh output:

```json
{
  "id": "2up3OPMp9Tb4dAKM2erWXQ",
  "name": "Nama Album",
  "artists": [
    "Nama Artist"
  ],
  "releaseDate": "2025-01-01",
  "totalTracks": 12,
  "tracks": [
    {
      "id": "track_id",
      "spotifyUri": "spotify:track:track_id",
      "url": "[https://open.spotify.com/track/track_id](https://open.spotify.com/track/track_id)",
      "title": "Track Pertama",
      "artists": [
        "Nama Artist"
      ],
      "album": "Nama Album",
      "albumId": "2up3OPMp9Tb4dAKM2erWXQ",
      "albumCover": "[https://i.scdn.co/image/example](https://i.scdn.co/image/example)",
      "isExplicit": false,
      "durationMs": 210000,
      "isPlayable": true,
      "playabilityReason": null,
      "audioPreviewUrl": null
    }
  ]
}
```

---

## Metadata Artist

Gunakan command `artist` untuk mengambil metadata artist.

Format:

```bash
node spotify.js artist <id|uri|url>
```

Contoh menggunakan artist ID:

```bash
node spotify.js artist 0TnOYISbd1XYRBk9myaseg
```

Contoh menggunakan Spotify URI:

```bash
node spotify.js artist spotify:artist:0TnOYISbd1XYRBk9myaseg
```

Contoh menggunakan Spotify URL:

```bash
node spotify.js artist [https://open.spotify.com/artist/0TnOYISbd1XYRBk9myaseg](https://open.spotify.com/artist/0TnOYISbd1XYRBk9myaseg)
```

Menyimpan hasil metadata artist:

```bash
node spotify.js artist 0TnOYISbd1XYRBk9myaseg --out artist.json
```

Contoh output:

```json
{
  "id": "0TnOYISbd1XYRBk9myaseg",
  "name": "Nama Artist",
  "subtitle": null,
  "relatedEntityUri": null,
  "tracks": [
    {
      "id": "track_id",
      "spotifyUri": "spotify:track:track_id",
      "url": "[https://open.spotify.com/track/track_id](https://open.spotify.com/track/track_id)",
      "title": "Nama Lagu",
      "artists": [
        "Nama Artist"
      ],
      "album": "Nama Album",
      "albumId": "album_id",
      "albumCover": "[https://i.scdn.co/image/example](https://i.scdn.co/image/example)",
      "isExplicit": false,
      "durationMs": 200000,
      "isPlayable": true,
      "playabilityReason": null,
      "audioPreviewUrl": null
    }
  ]
}
```

---

## Format Input Spotify

### Track

Spotify ID:

```text
4cOdK2wGLETKBW3PvgPWqT
```

Spotify URI:

```text
spotify:track:4cOdK2wGLETKBW3PvgPWqT
```

Spotify URL:

```text
[https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT](https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT)
```

### Album

Spotify ID:

```text
2up3OPMp9Tb4dAKM2erWXQ
```

Spotify URI:

```text
spotify:album:2up3OPMp9Tb4dAKM2erWXQ
```

Spotify URL:

```text
[https://open.spotify.com/album/2up3OPMp9Tb4dAKM2erWXQ](https://open.spotify.com/album/2up3OPMp9Tb4dAKM2erWXQ)
```

### Artist

Spotify ID:

```text
0TnOYISbd1XYRBk9myaseg
```

Spotify URI:

```text
spotify:artist:0TnOYISbd1XYRBk9myaseg
```

Spotify URL:

```text
[https://open.spotify.com/artist/0TnOYISbd1XYRBk9myaseg](https://open.spotify.com/artist/0TnOYISbd1XYRBk9myaseg)
```

---

## Opsi CLI

| Opsi | Default | Keterangan |
|---|---:|---|
| `--limit` | `10` | Jumlah track yang diminta saat search |
| `--offset` | `0` | Offset hasil pencarian |
| `--out` | Tidak ada | Menyimpan output JSON ke file |
| `--verbose` | `false` | Menampilkan log request HTTP |
| `-v` | `false` | Alias dari `--verbose` |

Contoh penggunaan semua opsi:

```bash
node spotify.js search "Hindia" --limit 20 --offset 0 --out hasil.json --verbose
```

---

## Audio Preview URL

Metadata track dapat memiliki field berikut:

```json
{
  "audioPreviewUrl": "[https://](https://)..."
}
```

Namun field tersebut dapat bernilai `null`:

```json
{
  "audioPreviewUrl": null
}
```

Audio preview bergantung pada data yang tersedia di Spotify embed page. Spotify mendokumentasikan preview sebagai klip audio hingga 30 detik yang bisa tidak tersedia, dan preview tidak boleh menjadi layanan mandiri. [13][19]

Jika project menampilkan preview audio, cover art, judul lagu, atau metadata Spotify, sertakan tautan ke halaman Spotify dari field berikut:

```json
{
  "url": "[https://open.spotify.com/track/track_id](https://open.spotify.com/track/track_id)"
}
```

Spotify mengharuskan penggunaan metadata, cover art, dan audio preview disertai branding serta tautan kembali ke konten Spotify. [15][22]

---

## Menyimpan Output JSON

Gunakan opsi `--out` untuk menyimpan response ke file JSON.

Contoh search:

```bash
node spotify.js search "Hindia" --limit 10 --out search-hindia.json
```

Contoh track:

```bash
node spotify.js track 4cOdK2wGLETKBW3PvgPWqT --out track.json
```

Contoh album:

```bash
node spotify.js album 2up3OPMp9Tb4dAKM2erWXQ --out album.json
```

Contoh artist:

```bash
node spotify.js artist 0TnOYISbd1XYRBk9myaseg --out artist.json
```

---

## Verbose Log

Gunakan `--verbose` atau `-v` untuk menampilkan log request HTTP.

```bash
node spotify.js search "Hindia" --limit 5 --verbose
```

Contoh log:

```text
 GET [https://embed.spotify.com/embed/track/4cOdK2wGLETKBW3PvgPWqT](https://embed.spotify.com/embed/track/4cOdK2wGLETKBW3PvgPWqT) (try 1)
 POST [https://clienttoken.spotify.com/v1/clienttoken](https://clienttoken.spotify.com/v1/clienttoken) (try 1)
 GET [https://api-partner.spotify.com/pathfinder/v1/query](https://api-partner.spotify.com/pathfinder/v1/query) (try 1)
```

Log ditulis ke `stderr`, sedangkan output JSON ditulis ke `stdout`.

Menyimpan hasil ke file menggunakan shell redirect:

```bash
node spotify.js search "Hindia" --limit 10 > result.json
```

Menyimpan JSON sambil menampilkan log:

```bash
node spotify.js search "Hindia" --limit 10 --verbose > result.json
```

---

## Retry, Token, dan Timeout

Konfigurasi request script:

```js
const TIMEOUT = 20_000
```

```js
const RETRIES = 3
```

Status HTTP yang akan dicoba ulang:

```text
403
408
425
429
500
502
503
504
```

Script menggunakan:

- Anonymous session token dari Spotify embed page
- Client token dari Spotify client token endpoint
- Cache token agar tidak request ulang sebelum token mendekati expired
- Refresh anonymous session ketika response memberi HTTP `401`
- Rotasi User-Agent di setiap request retry
- Exponential backoff dengan random jitter
- Fallback persisted GraphQL hash untuk command search

---

## Cara Kerja

### Search

1. Script membuka Spotify embed track untuk mengambil anonymous session token.
2. Script meminta client token.
3. Script mengirim persisted GraphQL query ke endpoint partner Spotify.
4. Script membaca track, album, artist, dan top results.
5. Script mengubah hasil menjadi format JSON yang lebih sederhana.

### Track

1. Script menerima Spotify ID, URI, atau URL.
2. Script mengubah input menjadi track ID.
3. Script membuka Spotify embed track page.
4. Script membaca entity dari tag `__NEXT_DATA__`.
5. Script mengembalikan metadata track.

### Album

1. Script menerima album ID, URI, atau URL.
2. Script membuka Spotify embed album page.
3. Script membaca entity album.
4. Script mengambil `trackList`.
5. Script mengembalikan metadata album beserta track list.

### Artist

1. Script menerima artist ID, URI, atau URL.
2. Script membuka Spotify embed artist page.
3. Script membaca entity artist.
4. Script mengembalikan metadata artist serta track list jika tersedia.

---

## Penggunaan Sebagai Module

Script menggunakan ESM export.

Buat file `app.js`:

```js
import {
  search,
  track,
  album,
  artist
} from "./spotify.js"

async function main() {
  try {
    const searchResult = await search("Hindia", {
      limit: 5,
      offset: 0,
      log: console.error
    })

    console.log(JSON.stringify(searchResult, null, 2))

    const trackData = await track("4cOdK2wGLETKBW3PvgPWqT")

    console.log(JSON.stringify(trackData, null, 2))

    const albumData = await album("2up3OPMp9Tb4dAKM2erWXQ")

    console.log(JSON.stringify(albumData, null, 2))

    const artistData = await artist("0TnOYISbd1XYRBk9myaseg")

    console.log(JSON.stringify(artistData, null, 2))
  } catch (error) {
    console.error(error.message)
  }
}

main()
```

Jalankan:

```bash
node app.js
```

Export yang tersedia:

```js
export async function search(...)
```

```js
export async function track(...)
```

```js
export async function album(...)
```

```js
export async function artist(...)
```

Default export:

```js
export default {
  search,
  track,
  album,
  artist
}
```

---

## Error Handling

Script menangani kondisi berikut:

- Keyword search kosong
- Track ID kosong
- Album ID kosong
- Artist ID kosong
- Anonymous session token tidak ditemukan
- Client token tidak dapat diambil
- `__NEXT_DATA__` tidak ditemukan
- Spotify entity tidak ditemukan
- Token expired
- Persisted GraphQL hash tidak valid
- HTTP error sementara
- Timeout request
- JSON response tidak valid
- Koneksi jaringan gagal

Contoh command search tanpa keyword:

```bash
node spotify.js search
```

Contoh error:

```text
Kata kunci wajib diisi.
```

Contoh command track tanpa ID:

```bash
node spotify.js track
```

Contoh error:

```text
--id wajib diisi.
```

Contoh error session:

```text
Session bootstrap gagal: __NEXT_DATA__ tidak ditemukan.
```

Contoh error client token:

```text
Client token gagal diambil.
```

Contoh error persisted query:

```text
Semua kandidat hash gagal untuk operation searchDesktop.
```

---

## Batasan

- Script bergantung pada halaman embed dan endpoint partner Spotify yang tidak ditujukan sebagai API publik stabil.
- Struktur HTML, JSON, session token, client token, persisted query hash, atau response dapat berubah kapan saja.
- Tidak semua track mempunyai audio preview URL.
- Hasil pencarian dapat dipengaruhi wilayah, katalog, market availability, dan pembatasan konten.
- Metadata yang tersedia dari embed dapat berbeda dari aplikasi Spotify.
- Jangan melakukan request besar atau paralel tanpa rate limit.
- Untuk aplikasi production, gunakan Spotify Web API resmi beserta authorization dan app credentials yang sesuai. Spotify Web API dirancang untuk mengambil metadata katalog serta membuat integrasi layanan Spotify secara resmi. [17][24]

---

## Kepatuhan Penggunaan

Repository ini hanya ditujukan untuk metadata, pencarian, dan integrasi yang mematuhi ketentuan platform.

Jangan gunakan atau dokumentasikan fitur yang memungkinkan pengguna menyimpan, mengunduh, atau melakukan ripping terhadap lagu, album art, maupun Spotify Content. Widget Terms Spotify melarang aplikasi menyediakan fungsi yang memungkinkan pengguna menyimpan atau mengunduh Spotify Content. [21]

Gunakan data dengan cara berikut:

- Tampilkan tautan kembali ke Spotify.
- Sertakan branding Spotify yang sesuai.
- Jangan menjadikan audio preview sebagai layanan mandiri.
- Jangan menghapus atribusi artist, album, atau Spotify.
- Patuhi Spotify Developer Terms, Developer Policy, dan hukum hak cipta. [14][15][22]

---

## .gitignore

Buat file `.gitignore`:

```gitignore
node_modules/
.env
*.log
result.json
results/
npm-debug.log*
yarn-debug.log*
yarn-error.log*
.DS_Store
```

---

## License

Project ini menggunakan lisensi MIT.

Buat file `LICENSE`:

```text
MIT License

Copyright (c) 2026 SCRIPETEREN

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files, to deal in the Software
without restriction, including without limitation the rights to use, copy,
modify, merge, publish, distribute, sublicense, and/or sell copies of the
Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## Creator

```text
SCRIPETEREN
```

```text
[https://github.com/SCRIPETEREN](https://github.com/SCRIPETEREN)
```

---

## Disclaimer

Repository ini dibuat untuk pembelajaran Node.js, ESM module, HTTP request, token cache, retry logic, JSON parsing, dan pengolahan metadata Spotify.

Gunakan script secara bertanggung jawab. Spotify Content meliputi rekaman suara, cover art, karya musik, metadata, dan materi lain yang tersedia melalui layanan Spotify. Patuhi Spotify Developer Terms, Developer Policy, Widget Terms, ketentuan lisensi, serta hukum dan hak cipta yang berlaku. [14][15]

<p align="center">
  Made by <a href="https://github.com/SCRIPETEREN">SCRIPETEREN</a>
</p>