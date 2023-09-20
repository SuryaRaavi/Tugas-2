Nama: Surya Raavi Adiputra
NPM: 2206082404
Kelas: PBP-E

Tugas-3
1. Apa perbedaan antara form POST dan form GET dalam Django?
   POST:
   - Digunakan untuk mengirim data ke server untuk diproses.
   - Data dikirimkan dalam tubuh permintaan HTTP dan tidak terlihat di URL.
   - Lebih aman untuk mengirim data sensitif.
   - Tidak ada batasan ukuran data bawaan.
   GET:
   - Digunakan untuk mengambil data dari server.
   - Data dikirimkan dalam query string dan terlihat di URL.
   - Lebih cocok untuk pencarian atau tindakan yang tidak mengubah data di server.
   - Terdapat batasan ukuran data yang dapat dikirimkan karena batasan panjang URL.

2. Apa perbedaan utama antara XML, JSON, dan HTML dalam konteks pengiriman data?
   Perbedaan utama JSON dan XML terletak di formatnya dimana JSON menggunakan pasangan kunci-nilai untuk membuat struktur seperti peta, sedangkan XML menyimpan data dalam struktur pohon yang menyajikan lapisan informasi secara berurut. Dalam hal syntax, JSON memiliki syntax yang lebih sederhana dibandingkan XML yang terbilang kompleks. File JSON juga lebih cepat diuraikan dibandingkan file XML. Namun, XML memiliki tipe data yang lebih luas dibandingkan JSON. Tidak hanya itu, dalam hal keamanan, penggunaan JSON terbilang lebih aman dibandingkan XML. Lalu, perbedaan keduanya dengan HTML terletak di fungsinya dimana jika JSON dan XML berfungsi untuk mengirim dan bertukar data, HTML berfungsi untuk membuat halaman web dengan elemen-elemen markup yang mendefinisikan struktur dan tampilan konten web.

3. Mengapa JSON sering digunakan dalam pertukaran data antara aplikasi web modern?
   JSON lebih sering digunakan dalam pertukaran data karena beberapa hal, yaitu sintaksi yang sederhana dan mudah dibaca oleh manusia, format yang digunakan didukung oleh banyak bahasa pemrograman, mendukung data kompleks karena memiliki tipe data yang fleksibel, cenderung lebih ringan dalam hal kinerja dari pada format lain, memiliki dokumentasi yang luas dan beragam, dan memiliki tingkat keamanan tinggi sehingga dapat mencegah serangan injeksi kode.
   
4. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step
   Langkah paling awal yang harus dilakukan sebelum melakukan penambahan atau perubahan pada direktori proyek adalah membuat virtual environment untuk mencegah terjadinya konflik antar dua proyek atau lebih.
   - Membuat input forms dan menambahkan fungsi http pada views
     Tahap ini dilakukan dengan membuat skeleton atau templates untuk menjaga konsistensi kerangka views dalam aplikasi main dimana dilakukan dengan membuat folder templates pada main dan menambahkan file base.html sebagai template dasar. Setelah berhasil membuat skeleton, mendaftarkan templates sebagai direktori dasar dalam kerangka html dalam file settings.py bagian TEMPLATES pada sub direktori proyek. Lakukan juga modifikasi pada main.html yang terletak di direktori main/templates untuk mengaplikasikan base.html. Langkah selanjutnya adalah membuat file forms.py dengan melakukan import modul main.models untuk mengambil objek Item pada direktori main yang bertujuan untuk menyimpan data atau input dalam bentuk objek yang dalam hal ini objeknya adalah Item dan juga menambahkan fields yang dalam hal ini adalah atribut dari Item. Selanjutnya, modifikasi views.py dalam direktori main dengan menambahkan beberapa modul yang salah satunya adalah main.forms yang bertujuan untuk memproses request dari user. Dalam file views.py, menambahkan fungsi baru bernama create_product yang intinya berfungsi untuk memvalidasi dan mendata input dari user dengan mendefinisikannya menjadi ProductForm yang mana adalah objek yang diambil dari modul  main.forms, serta redirects setelah data berhasil dibuat dan disimpan. Tahap berikutnya adalah memodifikasi fungsi show_main dengan menambahkan suatu variabel products yang menyimpan informasi mengenai berbagai objek Item untuk ditampilkan nanti di main.html. Setelah melakukan modifikasi pada views.py, pada urls.py dalam direktori main, menambahkan objek baru untuk diimport, yaitu create_product dan mendaftarkan create_product pada path url agar nantinya bisa diakses. Langkah selanjutnya adalah membuat suatu file create_product.html yang intinya berfungsi untuk menampilkan fields forms yang sudah ditentukan sebelumnya dalam bentuk table dan mengirim request user ke views.
   - Menambahkan 4 fungsi views, yaitu XML, JSON, XML by ID, dan JSON by ID
     Tahap pertama dilakukan untuk menambahkan HttpResponse dari modul django.http dan serializers dari modul django.core. Lalu, menambahkan fungsi show_xml dan show_json. Pada kedua fungsi tersebut menambahkan suatu variabel untuk mengambil seluruh objek item, yaitu "data = Item.objects.all()" dan menambahkan return yang berisi function berupa HttpResponse yang berisi parameter data hasil query yang sudah diserialisasi menjadi XML dalam fungsi show_xml dan JSON dalam fungsi show_json dan parameter content_type="application/xml" dalam fungsi show_xml dan content_type="application/json" dalam fungsi show_json. Selanjutnya, membuat dua fungsi xml dan json untuk menampilkan data berdasarkan id, yaitu show_json_by_id dan show_xml_by_id. Isi dalam fungsi tersebut hampir sama dengan kedua fungsi show_xml dan show_json sebelumnya dimana yang membedakan hanya dengan memodifikasi variabel data menjadi "data = Item.objects.filter(pk=id)" agar nantinya url json dan xml bisa mengambil data berdasarkan id.
   - Membuat routing URL pada views
     Melakukan import fungsi modul main.views "from main.views import show_main, create_product, show_xml, show_json, show_xml_by_id, show_json_by_id" ke urls.py dalam direktori main dan menambahkan url patterns  "path('xml/', show_xml, name='show_xml'), path('json/', show_json, name='show_json'), path('xml/<int:id>/', show_xml_by_id, name='show_xml_by_id'), path('json/<int:id>/', show_json_by_id, name='show_json_by_id')" agar fungsi-fungsi tersebut bisa diakses oleh url.

5. Hasil screenshot akses link di Postman terlampir di link drive berikut
   https://drive.google.com/drive/folders/1tkPnrIuyEzhl3u2BvTAUGQnA7o7HULxG?usp=sharing





Tugas-2

1. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step
   - Membuat proyek django
     Sebelum menginisiasi proyek django, saya melakukan instalasi django pada direktori utama dari proyek yang ingin saya buat. Setelah instalasi selesai, menginisiasi dan mengonfigurasikan proyek django untuk bisa diakses oleh siapa saja dan melakukan pengecekan apakah aplikasi django saya berhasil berjalan. Terakhir, menambahkan .gitigonore pada direktori utama dan menghubungkan serta menambahkan isi direktori utama (lokal) dengan repository di github.
   - Membuat aplikasi main pada direktori utama proyek
     Menginisiasi direktori main sebagai struktur awal untuk menentukan MVT dan menghubungkannya dengan direktori proyek dengan mengatur file settings.py untuk ditambahkan direktori main pada daftar aplikasi.
   - Membuat model pada aplikasi main dengan nama Item dan memiliki atribut wajib name, amount, description.
     Mengakses file models.py untuk dimodifikasi. Modifikasi dilakukan dengan mengimport models pada modul django.db dan membuat class Item berparameter models.Model dengan atribut name dengan tipe CharField, amount dengan tipe IntegerField, dan description dengan tipe TextField.
   - Membuat sebuah fungsi pada views.py untuk dikembalikan ke dalam sebuah template HTML
     Sebelum memodifikasi fungsi views.py, membuat direktori template di dalam direktori aplikasi main dan menambahkan file main.html yang berisi nama dan kelas sebagai tampilan dasar HTML. Lalu, melakukan modifikasi fungsi views.py yang terletak di direktori aplikasi main dengan mengimport render dari modul django.shortcuts dan membuat suatu fungsi dengan suatu parameter request yang mengatur permintaan HTTP serta menambahkan dictionary context yang berisi nama dan kelas untuk nanti dikembalikan oleh fungsi render yang memiliki parameter request, "main.html", dan context.
   - Membuat sebuah routing pada urls.py aplikasi main untuk memetakan fungsi yang telah dibuat pada views.py
     Membuat file urls.py yang intinya bertugas mendefinisikan pola URL terkait untuk mengakses aplikasi main yang nantinya menampilkan modul main.views yang berisi tampilan html. Lalu, mengakses urls.py dan memodifikasi direktori proyek untuk mengatur rute URL tingkat proyek dan mangatur akses atau rute URL tingkat proyek ke rute URL aplikasi main. Terakhir, melakukan pengecekan dengan mengakses http://localhost:8000/main/ apakah tampilan HTML sudah sesuai.
   - Melakukan deployment ke Adaptable terhadap aplikasi yang sudah dibuat
     Sebelum melakukan deploy, terlebih dahulu melakukan add, commit, dan push perubahan yang terjadi pada direktori utama proyek. Setelah itu, melakukan deployment ke Adaptable dengan memilih Python App Template sebagai template deployment dan memilih PostgreSQL untuk basis data yang digunakan. Lalu, mengatur versi python yang digunakan dan mengatur start command dengan perintah python manage.py migrate && gunicorn nama-repositori.wsgi. Terakhir, menamai aplikasi yang juga sebagai nama domain situs, mencentang HTTP Listener on PORT, dan melakukan deploy.

2. Buatlah bagan yang berisi request client ke web aplikasi berbasis Django beserta responnya dan jelaskan pada bagan tersebut kaitan antara urls.py, views.py, models.py, dan berkas html.
   Bagan bisa dilihat pada link berikut:
   https://drive.google.com/drive/folders/1n-50pnGqKg_KgJssIoI6x6LkdcVjhvu9?usp=sharing
   Proses request client dimulai ketika http melakukan request dengan mendefinisikan pola URL sehingga request client bisa diterima oleh views.py. views.py kemudian melakukan pencarian data atau informasi yang direquest oleh client pada database melalui ORM atau models.py. Sementara itu, pada dasarnya, models.py berperan sebagai basis data yang direpresentasikan dalam tabel terstruktur. Data atau informasi yang diproses oleh models.py melalui operasi CRUD (Create, Read, Update, Delete) nantinya akan diakses oleh views.py. Data atau informasi yang diatur oleh views.py akan diakses oleh berkas html pada direktori template sebagai respon http dimana respon tersebut dalam bentuk tampilan interface yang berisi data atau informasi dari views.py sesuai yang di request oleh client.

3. Jelaskan mengapa kita menggunakan virtual environment? Apakah kita tetap dapat membuat aplikasi web berbasis Django tanpa menggunakan virtual environment?
	Aktivasi virtual environment memiliki peran utama untuk mengisolasi paket atau dependensi yang berbeda untuk setiap proyek yang dibuat sehingga mencegah terjadinya konflik dan masalah yang mungkin muncul ketika dua proyek berbeda memerlukan versi yang berbeda dari paket yang sama. Tidak hanya itu, penggunaan virtual environment juga bertujuan untuk mengatur instalasi paket dan dependensi secara lokal dalam lingkungan proyek, mempermudah akses untuk berbagi dengan orang lain, menjaga instalasi python tetap bersih, dan mencegah kerusakan dan perubahan yang tak terduga pada proyek karena perubahan yang tidak disengaja pada instalasi sistem python. Lalu, pembuatan aplikasi web berbasis django tetap dapat dilakukan tanpa adanya aktivasi virtual environment, namun hal ini berpotensi menyebabkan konflik dan masalah dalam manajemen dependensi dan versi paket dan bisa mengganggu aplikasi lain yang dijalankan dalam instalasi python global.

4. Jelaskan apakah itu MVC, MVT, MVVM dan perbedaan dari ketiganya.
   - MVC
    MVC adalah sebuah pola yang membagi kode menjadi 3 bagian, yaitu
    a. Model: Tujuan utama komponen ini adalah untuk menyimpan data aplikasi dan menangani logika domain (real-world business rules) dan komunikasi dengan database dan lapisan jaringan.
    b. View: Bertujuan untuk menyediakan visualisasi data yang disimpan dalam Model dan menawarkan interaksi kepada pengguna.
    c. Controller: Berperan untuk menyimpan logika inti aplikasi, mengakses informasi tentang respons pengguna, dan memperbarui Model sesuai kebutuhan.
  - MVT
    MVT adalah sebuah pola atau konsep arsitektur yang membagi komponen-komponen utama suatu aplikasi menjadi tiga bagian, yaitu:
    a. Model: Model mewakili struktur data dan logika aplikasi yang berada di belakang tampilan serta menghubungkan aplikasi dengan basis data dan mengatur interaksi dengan data tersebut.
    b. View: View memiliki peran untuk mengatur bagaimana data atau informasi yang didapat dari Model bisa ditampilkan atau diakses sesuai request user pada interface nantinya. 
    c. Template: Komponen ini berperan sebagai interface pengguna untuk menampilkan data atau informasi dari View.
  - MVVM
    MVVM adalah suatu konsep arsitektur untuk memisahkan logika presentasi (View atau UI) dari logika bisnis utama suatu aplikasi. MVVM terbagi menjadi tiga komponen, yaitu:
    a. Model: Komponen ini akan bekerja sama dengan ViewModel untuk mengakses dan menyimpan data.
    b. View: Komponen ini tidak mengandung logika aplikasi apapun dan berperan untuk menginformasikan ViewModel tentang tindakan pengguna.
    c. ViewModel: Komponen ini bertugas untuk mengatur aliran data yang relevan dengan View dan menghubungkan antara Model dan View.
      