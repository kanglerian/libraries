[Kembali](/)
# API with AXIOS

Axios adalah sebuah library yang digunakan untuk API. Disini saya akan mencoba untuk mendemonstrasikan cara menggunakan AXIOS API.

**Membuat Project Sederhana**

Disini kita siapkan sebuah body HTML dengan Data Mahasiswa dalam bentuk list. Tidak lupa untuk menyertakan id dengan value `hasil`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Coba sedot API</title>
</head>
<body>
    <h1>Data Mahasiswa</h1>
    <ul id="hasil"></ul>
</body>
</html>
```

**Gunakan Axios dan FetchAPI**

Disini kita telah memiliki data API yaitu data `anggota` yang di hosting melalui `vercel`.

```html
    <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
    <script>
        let hasil = '';
        axios({
            method:'get',
            url:'https://research-kanglerian.vercel.app/api/anggota',
            responseType: 'json'
        })
        .then((response)=> {
            const users = response.data;
            for(let i = 0; i < users.length; i++){
                hasil += `<li>Username: ${users[i].username}</li>`
            }
            document.getElementById('hasil').innerHTML = hasil;
        });
    </script>
```
