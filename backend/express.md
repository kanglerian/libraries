# Express API ver.1

API ini hanyalah aktivitas testing, dimana ExpressJS berlaku sebagai BackEnd yaitu memuat data dari `database` kemudian mengirimkan data dengan format `json` melalui URL.

**Inisialisasi Project**

```console
$ mkdir my-project
$ npm init
```

**Install Dependencies**

Dependencies yang diperlukan antara lain:

- express
- cors

```console
$ npm i express
$ npm i cors
```

> Cors digunakan untuk mengatasi error ketika mengirimkan data JSON. Biasanya ada perintah harus `allow cors`


**Load Express JS**

Buatlah file bernama `index.js` kemudian tulislah code dibawah ini

```js
const express = require('express');
const app = express();
const port = 3000;

const cors = require('cors');
app.use(cors());

app.listen(port, () => console.log(`Apps run on http://localhost:${port}`));
```

**Membuat Data Dummy**

Kita akan mencoba untuk mengirimkan data dummy dalam bentuk sebuah `object` kemudian kita akan kirimkan menjadi API berformat `json`.

```js
const anggota = [
    {
        nama: 'Lerian',
        email: 'kanglerian@gmail.com'
    },
    {
        nama: 'Sopyan',
        email: 'kangsopyan@gmail.com'
    },
];
app.get('/api/anggota', (req, res) => {
    res.json(anggota);
});
```

**Mengambil Data MySQL**

Kita akan mencoba untuk memuat data dari database `mysql` ikuti langkah-langkah berikut ini:

1. Install Dependecies `mysql`

```console
$ npm i mysql
```

2. Inisialisasi `mysql`

```js
const mysql = require('mysql');
const con = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: '',
    database: 'yourdatabase',
    multipleStatements: true
});
app.use(express.urlencoded({extended:true}));
```

3. Memuat data dengan `query`

```js
app.get('/api/anggota', (req, res) => {
    const sql = `SELECT * FROM yourtable`;
    con.query(sql, (err, result) => {
        res.json(result);
    });
});
```