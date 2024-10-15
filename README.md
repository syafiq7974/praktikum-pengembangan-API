Praktikum: 
Interoperabilitas dengan JSON dan XML API

 

DOSEN PENGAMPU:
SEPYAN PURNAMA KRISTANTO, S.KOM.,M.KOM	



DIBUAT OLEH:
Syafiq Burhanuddin 
(362358302068)
2A TRPL


PRODI TEKNOLOGI REKAYASA PERANGKAT LUNAK
JURUSAN BISNIS DAN INFORMATIKA
POLITEKNIK NEGERI BANYUWANGI
2024
Bagian 1:
 Membuat API dengan JSON menggunakan Node.js 
1. Instalasi Node.js dan Express.js
 
2. Membuat Server Express.js
 
Tambahkan ke htdocs

 


const express = require('express');
const app = express();
const port = 3000;

app.use(express.json());

let items = [
  { id: 1, name: "Book 1", author: "Author A" },
  { id: 2, name: "Book 2", author: "Author B" }
];

// GET endpoint untuk mengambil daftar item
app.get('/items', (req, res) => {
  res.json(items);
});

// POST endpoint untuk menambahkan item baru
app.post('/items', (req, res) => {
  const newItem = req.body;
  newItem.id = items.length + 1;
  items.push(newItem);
  res.status(201).json(newItem);
});

app.listen(port, () => {
  console.log(`Server berjalan di http://localhost:${port}`);
});

Hasilnya 
 

Menggunakan post 
 





Delete
 
Bagian 2: 
Membuat API dengan JSON menggunakan PHP

2. Membuat File API
 
// Data dummy 
$persons = [ 
    [ 
        "id" => 1, 
        "nama" => "John Doe", 
        "umur" => 30, 
        "alamat" => [ 
            "jalan" => "Jalan ABC", 
            "kota" => "Jakarta" 
        ], 
        "hobi" => ["membaca", "bersepeda"] 
    ], 
    [ 
        "id" => 2, 
        "nama" => "Jane Doe", 
        "umur" => 25, 
        "alamat" => [ 
            "jalan" => "Jalan DEF", 
            "kota" => "Bandung" 
        ], 
        "hobi" => ["menulis", "berenang"] 
    ] 
]; 
 
// Mendapatkan metode HTTP yang digunakan (GET, POST, DELETE) 
$method = $_SERVER['REQUEST_METHOD']; 
 
// Mengatur respon berdasarkan metode HTTP 
switch ($method) { 
    case 'GET': 
        // Mengembalikan semua data persons 
        echo json_encode($persons); 
        break; 
 
    case 'POST': 
        // Mendapatkan data dari body request 
        $input = json_decode(file_get_contents('php://input'), true); 
        $input['id'] = end($persons)['id'] + 1; // Menambahkan ID baru 
        $persons[] = $input; // Menambahkan data baru ke array 
        echo json_encode($input); 
        break; 
 
    case 'DELETE': 
        // Mendapatkan ID dari URL 
        $url_parts = explode('/', $_SERVER['REQUEST_URI']); 
        $id = end($url_parts); 
        // Menghapus data berdasarkan ID 
        $persons = array_filter($persons, function ($person) use ($id) { 
            return $person['id'] != $id; 
        }); 
        echo json_encode(["message" => "Data dengan ID $id telah dihapus"]); 
        break; 
 
    default: 
        // Metode HTTP tidak didukung 
        http_response_code(405); 
        echo json_encode(["message" => "Metode HTTP tidak didukung"]); 
        break; 
} 
?>

 
Hasilnya 
 
Bagian 3:
 Membuat API dengan XML menggunakan PHP 
1. Instalasi PHP dan Server Web Instal PHP dan server web seperti Apache atau Nginx. Untuk kemudahan, Anda bisa menggunakan XAMPP atau WAMP. 
 
2. Membuat Endpoint XML
 

Hasilnya
 
 



Tugas 2: Pengujian Interoperabilitas : 
Buat skrip yang mengambil data dari API JSON dan mengubahnya menjadi XML.
buat file baru xml_api.php.
 


Tambahkan kode berikut ke dalam xml_api.php untuk membuat endpoint XML:
 
Hasilnya 
 

