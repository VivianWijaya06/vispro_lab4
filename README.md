Repository ini berisi implementasi dua pendekatan state management di Flutter:
1. Ephemeral State Management (StatefulWidget)
Ephemeral state (juga disebut local state) adalah state yang hanya berlaku di dalam satu widget.  
Contohnya: form input, animasi, toggle UI.
Dalam codelab ini, CounterWidget menyimpan nilai _counter menggunakan setState().  
Dimana setiap kali tombol incrementnya ditekan, hanya widget itu sendiri yang direbuild.

2. App State Management (scoped_model)
App state adalah state yang dibutuhkan oleh banyak widget di seluruh aplikasi.  
Contohnya: login info, shopping cart, user preferences.
Dalam codelab ini, CounterModel menyimpan nilai _counter.  
Perubahan state dilakukan dengan increment() dan decrement(), lalu notifyListeners() memberi tahu semua widget yang mendengarkan (ScopedModelDescendant) agar otomatis update UI.

### Perbandingan 2 counter tersebut
1. Ephemeral State (StatefulWidget): 
  - Nilai counter hanya tersimpan di dalam CounterWidget.  
  - State hilang ketika widget dihancurkan atau aplikasi ditutup.  
  - Cocok untuk state sederhana dan lokal.

2. App State (scoped_model):
  - Nilai counter disimpan di CounterModel yang bisa diakses banyak widget.  
  - Perubahan state langsung disebarkan ke seluruh aplikasi.  
  - Cocok untuk aplikasi besar dengan banyak halaman atau komponen yang berbagi data yang sama.

### Observasi Scoped Model
- Scoped Model mempermudah manajemen app-wide state.  
- Tidak perlu mengoper data manual melalui constructor antar widget.  
- Efisien ketika ada banyak widget yang harus sinkron terhadap perubahan state.

## Perbedaan & Keuntungan dari App State Management di aplikasi flutter yang lebih besar
a. Perbedaan
Kalau di Ephemeral state management biasanya cuma dipakai di dalam satu widget, misalnya untuk buat form input, animasi, dan toggle UI. State ini sifatnya sementara, jadi kalau widget ditutup atau aplikasi direstart, nilainya akan hilang. Cocok dipakai kalau datanya memang cuma dibutuhkan di tempat itu saja. Perbedaan nya dengan App State itu kalau App State dipakai kalau data harus diakses oleh banyak widget di aplikasi. App State itu bisa menyimpan informasi yang sifatnya global dan penting. Contohnya itu login info, shopping cart, dan user preferences. Dengan menggunakan App State, data akan tetap konsisten di seluruh halaman aplikasi.

b. Keuntungan dari App State Management
1. Mudah untuk autentikasi pengguna: status login bisa dipakai di banyak halaman tanpa harus dioper manual.
2. Shopping carts lebih konsisten: item yang ditambahkan dari halaman produk otomatis muncul di halaman checkout.
3. Pengaturan aplikasi terpusat: misalnya kalau user ganti bahasa atau tema, semua halaman ikut berubah tanpa perlu atur satu-satu.
