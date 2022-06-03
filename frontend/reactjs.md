# Dzikir Counter Ver.1

Ini adalah sebuah aplikasi sederhana yaitu menghitung jumlah dzikir. Dzikir ba'da shalat dengan hitungan 33. Secara teknis, ketika angka sudah mencapai 33 maka nilai counter akan menjadi 1. Namun ketika kita reset maka nilai counter menjadi 0.

**Inisialisasi Project**

```console
$ npx create-react-app dzikirapps
$ cd dzikirapps
$ npm start
```

**Import useState**

useState digunakan untuk mengatur atau `set` sebuah variabel.

```js
import {useState} from 'react';
```

**Inisialiasi Counter**

useState digunakan disini. useState akan memberikan nilai default yaitu `0`. Function `ubah()` digunakan untuk menambah `number` dengan mengatur `setNumber`. Ketika nilai number sudah 33 maka `setNumber` mengubah nilai `number` menjadi `1`.

Begitu pula dengan function `reset()`. Function ini berfungsi untuk mengubah nilai number menjadi `0`.
```js
const [number, setNumber] = useState(0);
  
const ubah = () => {
    setNumber(number+1);
    if(number === 33){
      setNumber(1);
    }
}

const reset = () => {
    setNumber(0);
}
```

**Load Content**

Editlah file bernama `App.js` kemudian tulislah code dibawah ini di dalam function `App`.

```js
<div className="App">
    <header className="App-header">
        <img src={logo} alt='logo' className="App-logo" />
        <div className='container'>
          <h3>Hai, Lerian Febriana</h3>
          <h5 className='counter'>{number}</h5>
        </div>
        <div>
          <button type='button' className='button action' onClick={ubah}>click here!</button>
          <button type='button' className='button reset' onClick={reset}>reset</button>
        </div>
    </header>
</div>
```

**Load CSS**

Disini kita akan memuat `css` dengan file `App.css` yang sudah ada, namun kita modifikasi.

```css
.App-logo {
  height: 10vh;
  pointer-events: none;
}
.button {
  border: none;
  padding: 10px 30px;
  border-radius: 10px;
  font-weight: 700;
  margin-right: 10px;
  margin-left: 10px;
  color: white;
}

.action {
  background-color: #27c4f0;
}

.reset {
  background-color: #ff0000;
}

.button:active {
  transform: scale(0.95);
}

.counter {
  background-color: #3c4047;
  border-radius: 10px;
  padding: 20px;
  text-align: right;
  padding-right: 30px;
  font-family: 'Press Start 2P', cursive;
}
```

[Akses Aplikasi Disini](https://counter-react-app-ten.vercel.app)