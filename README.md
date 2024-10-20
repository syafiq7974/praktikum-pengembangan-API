Praktikum: 
Interoperabilitas dengan JSON dan XML API
![image](https://github.com/user-attachments/assets/c9a7125a-5281-4614-bec5-21a5475a2793)
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
 ![image](https://github.com/user-attachments/assets/b98ae9e0-8415-4383-8389-64a3684b8a25)

2. Membuat Server Express.js
 ![image](https://github.com/user-attachments/assets/5c53b94d-25ce-4705-84c3-56dfe30b2585)

Tambahkan ke htdocs
![image](https://github.com/user-attachments/assets/c092e296-ad0b-42a9-921c-d5ae4894c3d9)

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
menggunakan browse 
![image](https://github.com/user-attachments/assets/0e15d74b-fbac-4b83-a97f-0d1d775f1f40)
Hasilnya 
 ![image](https://github.com/user-attachments/assets/fff021a0-2b42-4d03-848c-3c5d1bdaf663)
Menggunakan post 
![image](https://github.com/user-attachments/assets/d5b3c11f-2ca2-45d6-a9f7-408cdb19e29f)
Delete
![image](https://github.com/user-attachments/assets/09e4ac28-8e4c-4abf-8409-f5b95ecaec25)
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
 ![image](https://github.com/user-attachments/assets/300238d4-b7a0-4ca1-abfc-7c89481fb9ed)
Bagian 3:
 Membuat API dengan XML menggunakan PHP 
1. Instalasi PHP dan Server Web Instal PHP dan server web seperti Apache atau Nginx. Untuk kemudahan, Anda bisa menggunakan XAMPP atau WAMP. 
 ![image](https://github.com/user-attachments/assets/1579f154-4ffb-4ebb-9f20-90811abce87b)
2. Membuat Endpoint XML
 Hasilnya
 ![image](https://github.com/user-attachments/assets/7149850f-4ff8-4986-b3cf-f3e28da1d516)
