# Muhammad Madhani Putra
# PBP A - 2206028503

## Link Aplikasi 
Link Adaptable: [Madanshop](https://madanshop.adaptable.app/main/)
Link Deploy: (http://muhammad-madhani-tugas.pbp.cs.ui.ac.id/)

## Jawaban Soal Tugas 2

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).
1. Pertama, saya membuat project django baru dan menggunakan virtual environment
    1. Virtual environment django dapat dibuat dengan menjalankan command berikut di terminal
    ```
    python -m venv env
    ```
    - dan virtual environment django dapat diaktifkan dengan menjalankan command berikut di terminal 
    ```
    env\Scripts\activate.bat
    ```
    - Pada directory yang sama, saya membuat file txt baru yang berisi daftar dependencies yang akan diinstall(Hal ini dilakukan agar dapat mengautomatisasi penginstallan semua dependencies yang harus diinstall)
    - Lalu saya menjalankan pip install -r requirements.txt untuk menginstall semua dependencies yang terdaftar di requirements.txt
    - Saya juga menambahkan "*" pada bagian `ALLOWED_HOSTS` di file `settings.py`
    - Saya juga membuat file ".gitignore" agar file yang tidak perlu akan diabaikan nantinya

    2. Membuat aplikasi main
    - Kita harus menjalankan perintah berikut untuk membuat aplikasi main pada proyek kita
    ```
    python manage.py startapp main
    ```
    3. Membuat file html
    - Kita harus membuat folder baru di dalam app main dengan nama templates dan buat file 'main.html' di dalam directory templates
    4. Dalam folder madanshop, kita harus menambahkan `path('main/', include('main.urls'))` pada bagian `url_patterns` di dalam file `urls.py`. 
    5. Pada file `models.py` yang ada di directory `main`, saya menambahkan beberapa attribute yang dibutuhkan:
        - `name` dengan tipe CharField
        - `amount` dengan tipe IntegerField
        - `description` dengan tipe TextField
        - `date_added` dengan tipe DateField
        - `price` dengan tipe IntegerField
    6. Membuat sebuah function pada `views.py` yang akan mereturn nilai yang akan ditampilkan di file HTML nanti yang akan menampilkan nama app, nama, dan kelas.
    7. Melakukan add, commit, dan push ke github dan melakukan deploy di adaptable

### Buatlah bagan yang berisi request client ke web aplikasi berbasis Django beserta responnya dan jelaskan pada bagan tersebut kaitan antara `urls.py`, `views.py`, `models.py`, dan berkas html.
<img src='/Assets/Bagan.jpg'>

### Jelaskan mengapa kita menggunakan virtual environment? Apakah kita tetap dapat membuat aplikasi web berbasis Django tanpa menggunakan virtual environment?
Kita dapat membuat aplikasi web berbasis Django tanpa menggunakan virtual environment, tetapi hal tersebut tidaklah disarankan. Hal ini disebabkan karena jika kita tidak menggunakan virtual environment dapat menimbulkan konflik pada dependencies di sistem. Dengan menggunakan virtual environment juga kita dapat memastikan kestabilan dan portabilitas proyek kita di berbagai environment.

### Jelaskan apakah itu MVC, MVT, MVVM dan perbedaan dari ketiganya.
- `MVC` atau `Model-View-Controller` merupakan arsitektur yang membagi tiga komponennya menjadi model, view, dan controller.    
- `MVT` atau `Model-View-Template` merupakan arsitektur yang memisahkan komponen utama dari sebuah aplikasi.
- `MVVM` atau `Model-View-ViewModel` merupakan arsitektur yang memisahkan antara logika dan model melalui ViewModel.

Perbedaan antara MVC, MVT, dan MVVM terletak pada bagaimana mereka mengelola alur aplikasi. Dalam MVC, Controller mengendalikan alur aplikasi, sedangkan MVT menggantinya dengan Template untuk mengatur tampilan. MVVM memperkenalkan ViewModel yang memproses data dari Model dan memfasilitasi pengikatan data kuat antara Model dan View. Jadi, perbedaan utama adalah peran komponen tengah dalam mengelola logika dan alur aplikasi.


## Jawaban Soal Tugas 3

### Apa perbedaan antara form `POST` dan form `GET` dalam Django?
- Post lebih aman dibandingkna get, karena data tidak terlihat di URL atau tidak dapat dilihat oleh orang lain dengan mudah. Post melakukan pengiriman data melalui HTTP. Post dapat mengirim data dengan ukuran hampir tak terhingga.
- Get kurang aman, karena data dapat dilihat di URL dengan mudah. Get mengirim data melalui URL. Get mempunyai batasan pada jumlah data yang bisa dikirim(Sekitar 2.000 karakter).

### Apa perbedaan utama antara `XML`, `JSON`, dan `HTML` dalam konteks pengiriman data?
- XML menggunakan tag-tag yang bersifat lebih bebas dan fleksibel. Setiap elemen memiliki tag pembuka dan tag penutup. XML juga lebih sulit untuk dibaca dan ditulis oleh manusia karena memiliki sintaksis yang lebih rumit dan banyak tanda penghubung.
- JSON Menggunakan struktur data yang berbasis pasangan kunci-nilai (key-value pairs) dan lebih ringkas dibandingkan dengan XML. Lebih mudah untuk dibaca dan ditulis oleh manusia karena memiliki struktur data yang sederhana dan ringkas.
- Menggunakan tag-tag bawaan yang memiliki tujuan dan makna tertentu untuk membangun struktur halaman web. Dirancang untuk keperluan penampilan di browser, dan lebih mudah dibaca oleh manusia daripada XML tetapi tidak sejelas JSON dalam hal struktur data.

### Mengapa `JSON` sering digunakan dalam pertukaran data antara aplikasi web modern?
JSON sering digunakan dalam pertukaran data antara aplikasi web modern karena kesederhanaan dan keterbacaannya. Format ini memungkinkan data untuk diorganisir secara terstruktur dalam pasangan key-value, yang mudah dipahami oleh manusia dan juga mudah diurai oleh berbagai bahasa pemrograman. Selain itu, JSON dapat digunakan dengan berbagai bahasa pemrograman tanpa masalah kompatibilitas. Dukungan yang kuat dalam pengembangan web modern, kemampuan untuk mengatasi struktur data yang kompleks, serta efisiensi dalam penggunaan sumber daya juga merupakan alasan kenapa JSON menjadi pilihan yang sangat populer dalam komunikasi antara aplikasi web.

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).
1. Mengimplementasi Skeleton sebagai kerangka views
    - Membuat folder `templates` pada main folder dan buat sebuah file HTML baru yang bernama `base.html`.
    - Tambahkan pada TEMPLATES `'DIRS': [BASE_DIR / 'templates'], # Tambahkan kode ini'` pada file `setting.py` yang ada di subdirektori `Madanshop`.
    - Ubah file `main.html` yang ada pada direktori `main` agar dapat mengimplementasi base.html.
    ```
    {% extends 'base.html' %}

    {% block content %}
        <h1>{{ appname }}</h1>

        <h5>Name:</h5>
        <p>{{ name }}</p>

        <h5>Class:</h5>
        <p>{{ class }}</p>
    {% endblock content %}
    ```

2. Membuat input form untuk menambahkan objek model pada app
    - Buat file bermana `forms.py` di folder `main` dan buat function dengan nama `ProductForm`. Di dalam function tersebut, terdapat dua variabel, yaitu `model` dan `fields`. `model` akan digunakan untuk menunjukkan model yang akan digunakan untuk form, sedangkna `fields` akan menunjukkan field dari model items yang kita punya.
    - Mengimport hal-hal berikut pada views.py yang ada pada direktori main.
    ```
    from django.http import HttpResponseRedirect
    from main.forms import ProductForm
    from django.urls import reverse
    ```
    - Membuat method yang bernama `create_product` pada views.py yang akan digunakan untuk mengelola input form. Dalam function ini, form ItemForm diisi dengan data dari request.POST dan akan dilakukan pengecekan. Jika valid, data akan disimpan dan pengguna akan diarahkan kembali ke halaman utama.
    - Import `Products` dari `models.py` ke file `views.py` dan tambahkan `Products` pada function `show_main` di file `views.py`.
    - Dalam berkas `views.py` kita harus menambahkan variabel items yang akan digunakan untuk mengambil semua item yang ada pada database.
    - Buka `urls.py` dan import function `create_product` yang berasal dari `views.py`
    - Tambahkan `path('create-product', create_product, name='create_product'),` pada `urlpatterns` yang ada di `urls.py` agar kita dapat mengakses function yang sudah diimport sebelumnya.
    - Selanjutnya kita perlu membuat file html `create_product.html` pada subdirektori `templates` yang ada pada direktori `main` dengan isi berikut.
    ```
    {% extends 'base.html' %} 

    {% block content %}
    <h1>Add New Product</h1>

    <form method="POST">
        {% csrf_token %}
        <table>
            {{ form.as_table }}
            <tr>
                <td></td>
                <td>
                    <input type="submit" value="Add Product"/>
                </td>
            </tr>
        </table>
    </form>

    {% endblock %}
    ```
    - Tambahkan juga kode berikut agar data produk dapat ditampilkan dalam bentuk table, serta menambahkan button `add product` yang akan mengarahkan kita ke halaman `forms`.
    ```
        ...
    <table>
        <tr>
            <th>Name</th>
            <th>Price</th>
            <th>Description</th>
            <th>Date Added</th>
        </tr>

        {% comment %} Berikut cara memperlihatkan data produk di bawah baris ini {% endcomment %}

        {% for product in products %}
            <tr>
                <td>{{product.name}}</td>
                <td>{{product.price}}</td>
                <td>{{product.description}}</td>
                <td>{{product.date_added}}</td>
            </tr>
        {% endfor %}
    </table>

    <br />

    <a href="{% url 'main:create_product' %}">
        <button>
            Add New Product
        </button>
    </a>

    {% endblock content %}
    ```

3. Tambahkan 5 fungsi views untuk melihat objek yang sudah ditambahkan dalam format HTML, XML, JSON, XML by ID, dan JSON by ID.
    - Buat fungsi `show_xml` dalam `views.py` dan menambahkan path URL. Fungsi ini akan mengambil data Item dan mengembalikannya dalam format XML.
    - Buat fungsi `show_json` dalam `views.py` dan menambahkan path URL. Fungsi ini mengambil data Item dan mengembalikannya dalam format JSON.
    - Buat fungsi `show_xml_by_id` dalam `views.py` dan menambahkan path URL. Fungsi ini mengambil data Item berdasarkan ID yang disediakan dan mengembalikannya dalam format XML.
    - Buat fungsi `show_json_by_id` dalam `views.py` dan menambahkan path URL. Fungsi ini mengambil data Item berdasarkan ID yang disediakan dan mengembalikannya dalam format JSON
    - Data produk yang ditampilkan menggunakan HTML sudah dijelaskan di atas bersamaan dengan pembuatan form.

4. Membuat routing URL untuk masing-masing views yang telah ditambahkan pada poin 2.
    - Import beberapa function ke `urls.py` yang ada di folder main yaitu `show_xml`, `show_json`, `show_xml_by_id`, `show_json_by_id`. 
    - Tambahkan path url ke dalam `urlpatterns` 
    ```
    path('xml/', show_xml, name='show_xml'), 
    path('json/', show_json, name='show_json'), 
    path('xml/<int:id>/', show_xml_by_id, name='show_xml_by_id'),
    path('json/<int:id>/', show_json_by_id, name='show_json_by_id'), 
    ```


### Mengakses kelima URL di poin 2 menggunakan Postman, membuat screenshot dari hasil akses URL pada Postman, dan menambahkannya ke dalam README.md.
<img src='/Assets/html.png'>
<img src='/Assets/xml.png'>
<img src='/Assets/json.png'>
<img src='/Assets/xml_id.png'>
<img src='/Assets/json_id.png'>


## Jawaban Soal Tugas 4

### Apa itu Django `UserCreationForm`, dan jelaskan apa kelebihan dan kekurangannya?

`UserCreationForm` adalah form bawaan dari Django yang dapat memudahkan kita dalam pembuatan form untuk pendaftaran pengguna dalam web app. Dengan menggunakan `UserCreationForm` pengguna dimungkinkan untuk mengisi informasi-informasi yang diperlukan, seperti username dan password.
- Kelebihan `UserCreationForm`:
    - Sangat Mudah untuk Digunakan: Para developer tidak perlu membuat form dari awal dan dapat membuat form register hanya dengan menggunakan form bawaan dari Django ini.
    - Validasi Otomatis: `UserCreationForm` memiliki ketentuan-ketentuannya sendiri untuk mengisi username dan password pengguna. Kita tidak perlu memvalidasi lagi apa username dan password yang diinput oleh pengguna.
    - Integrasi dengan Django Authentication System: Karena `UserCreationForm` adalah form bawaan dari Django itu sendiri, jadi `UserCreationForm` dapat digunakan bersamaan dengan Django Authentication System.

- Kekurangan `UserCreationForm`:
    - Kurang Fleksibel: `UserCreationForm` susah untuk dikustomisasi, sehingga jika kita memiliki persyaratan pendaftaran pengguna yang lebih khusus atau kompleks, maka Djang `UserCreationForm` tidak dapat memenuhi kebutuhan tersebut.
    - Tidak Ada Fungsi Tambahan: Form ini hanya berfokus pada pendaftara pengguna dan autentikasi awal. Sehingga jika membutuhkan logika pendaftaran lebih, hal itu harus kita implementasikan secara terpisah.
    - Kurangnya Keamanan: Form ini memberikan autentikasi dasar dan validasi, tetapi untuk keamanan lebih, kita harus menambahkan hal itu sendiri.

### Apa perbedaan antara autentikasi dan otorisasi dalam konteks Django, dan mengapa keduanya penting?

Autentikasi adalah proses dimana kita harus memverifikasi identitas pengguna. Dalam proses autentikasi, kita harus memvalidasi bahwa pengguna adalah orang yang sudah terdaftar pada web app kita. Biasanya, Autentiaksi dilakukan dengan memasukkan username dan password dari pengguna, lalu kita memvalidasi itu.

Otorisasi adlah proses menentukan hak akses dan izin pengguna yang sudah ter-autentikasi. Hal ini akan menentukan, apa-apa saja yang dapat dialkukan pengguna dan tidak bisa dilakukan. Contohnya, saat kita masuk di suatu aplikasi sebagai user, biasanya kita bisa mengubah-ubah username kita atau password kita, tetapi kita biasanya tidak bisa mengubah nomor telepon atau email yang sudah terverifikasi.

Autentikasi dan otorisasi ini sangat penting, karena keduanya akan memastikan keamanan dari web app kita. Kita juga dapat menjaga privasi data pengguna, dengan memastikan bahwa pengguna hanya dapat melihat atau memanipulasi data yang sesuai dengan hak mereka. Kita juga dapat kepentingan untuk banyak peran yang berbeda.

### Apa itu cookies dalam konteks aplikasi web, dan bagaimana Django menggunakan cookies untuk mengelola data sesi pengguna?

Cookies di web app adalah bagian kecil dari data yang disimpan di perangkat pengguna itu. Data-data yang disimpan dapat diakses lagi saat pengguna kembali mengunjungi website itu di kemudian hari.

Django menggunakan cookies untuk mengelola data sesi pengguna dengan cara berikut: 
- Membuat sesi pengguna: Djangp akan menciptakan sesi pengguna dan ID sesi yang unik saat pengguna mencoba mengakses web app.
- Penyimpanan Data Sesi: Django akan menyimpan info sesi yang berjalan ke dalam cookies.
- Mengakses Data Sesi: Django akan membaca cookies pengguna pada permintaan-permintaan yang akan datang.
- Pembaruan Data Sesi: Django dapat mengubah data yang ada pada cookies menjadi data terbaru.
- Pengakhiran sesi: Django akan membersihkan data sesi saat pengguna keluar atau sesi dari pengguna sudah berakhir.

### Apakah penggunaan cookies aman secara default dalam pengembangan web, atau apakah ada risiko potensial yang harus diwaspadai?

Keamanan dari penggunaan cookies bergantung pada bagaimana cara kita mengimplementasikan cookies itu sendiri. Apbila kita mengimplementasikan dengan benar, penggunaan cookies secara default akan aman. Namun, penggunaan cookies dapat menimbulkan risiko yang banyak, seperti pelanggaran privasi, pencurian cookies, serta sangat rentan terhadap serangan.

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

- Mengimplenentasikan fungsi registrasi, login, dan logout.
    - REGISTER
        - Mengimport `redirect`, `UserCreationForm`, dan `messages` pada file views.py yang ada pada direktori main.
        - Membuat fungsi `register` pada `views.py` untuk form registrasi dan menghasilkan akun baru ketika data disubmit dari form.
        - Membuat file `register.html` pada `main/templates` untuk membuat interface saat ingin membuat akun.
        - Mengimport fungsi `register` ke `urls.py` yang ada di direktori main.
        - Menambahkan path URL untuk register pada `urls.py`

    - LOGIN
        - Mengimport `authenticate` dan `login` pada file views.py yang ada pada direktori main.
        - Membuat fungsi `login_user` pada `views.py` untuk mengautentikasi user yang akan login.
        - Membuat file `login.html` pada `main/templates` untuk membuat interface saat pengguna ingin login.
        - Mengimport fungsi `login_user` ke `urls.py` yang ada di direktori main.
        - Menambahkan path URL untuk login_user pada `urls.py`

    - LOGOUT
        - Import `logout` pada file `views.py` yang ada pada di direktori main.
        - Membuat fungsi `logout_user` pada `views.py` untuk mengautentikas user yang ingin melakukan logout.
        - Menambahkan button logout pada `templates/main.html`.
        - Mengimport fungsi `logout_user` ke `urls.py` yang ada di direktori main.
        - Menambahkan path URL untuk logout_user pada `urls.py`.

- Menghubungkan model `Item` dengan `User`.
    - Import `user` pada file `models.py`.
    - Menambahkan `ForeignKey` pada `Product` di file `models.py` untuk menghubungkan barang dengan user.
    - Ubah fungsi `create_product` yang ada pada `models.py`.
    - Menambahkan parameter `commit = False` pada variable `prodcuts` yang berfungsi agar Django tidak langsung menyimpan objek ke database.
    - Isi field `user` dengan objek `User` dari reeturn value `request.user` untuk menandakan bahwa objek tersebut dimiliki pengguna yang sedang login.

- Membuat dua akun pengguna dengan masing-masing tiga dummy data menggunakan model yang telah dibuat pada aplikasi sebelumnya untuk setiap akun di lokal.
<img src='/Assets/akun_1.png'>
<img src='/Assets/akun_2.png'>

- Menampilkan detail informasi pengguna yang sedang logged in seperti username dan menerapkan cookies seperti last login pada halaman utama aplikasi.

- Mengimport `HttpResponseRedirect`, `reverse`, dan `datetime` pada file `models.py`.
- Menambahkan kode pada fungsi `login_user` untuk melihat status last_login.
    - Edit blok `if user is not None` dengan menambahkan kode berikut:
        - `login(request, user)`
        - `response = HttpResponseRedirect(reverse("main:show_main))`
        - `response.set_cookie('last_login', str(datetime.datetime.now()))`
        - `return response`
    - Pada fungsi `show_main` tambahkan `'last_login': request.COOKIES['last_login']` pada variabel `context`.
    - Ubah fungsi `logout_user` dengan menambahkan kode:
        - `response = HttpResponseRedirect(reverse('main:login'))`
        - `response.delete_cookie('last_login')`
        - `return response`
    - Pada file `main.html` tanmbahkan kode `<h5>Sesi terakhir login: {{ last_login }}</h5>` untuk menampilkan kapan user terakhir login.


## Jawaban dari Tugas 5

### Jelaskan manfaat dari setiap element selector dan kapan waktu yang tepat untuk menggunakannya.

- Universal Selector (*):

    - Manfaat: Memungkinkan Anda memilih semua elemen pada halaman.
    - Kapan Digunakan: Berguna untuk mengatur beberapa properti umum pada halaman.


- Type Selector (Element Selector):

    - Manfaat: Memilih semua elemen dengan jenis tertentu (seperti <div>, <p>, dll.).
    - Kapan Digunakan: Ketika Anda ingin mengatur properti umum untuk suatu jenis elemen.

- Class Selector (.classname):

    - Manfaat: Memilih elemen dengan atribut class tertentu.
    - Kapan Digunakan: Ketik Anda ingin menerapkan gaya yang sama pada beberapa elemen yang memiliki kelas yang sama.

- ID Selector (#id):

    - Manfaat: Memilih elemen dengan atribut id tertentu.
    - Kapan Digunakan: Jarang digunakan karena ID seharusnya unik di halaman.

- Descendant Selector (Space):
    - Manfaat: Memilih elemen yang adalah keturunan dari elemen lain.
    - Kapan Digunakan: Saat Anda ingin menargetkan elemen yang berada dalam elemen lain.

- Child Selector (>):
    - Manfaat: Memilih elemen yang merupakan anak langsung dari elemen lain.
    - Kapan Digunakan: Ketika Anda ingin menargetkan elemen yang langsung di dalam elemen lain.

- Adjacent Sibling Selector (+):

    - Manfaat: Memilih elemen yang menjadi saudara sejajar langsung dari elemen lain.
    - Kapan Digunakan: Ketika Anda ingin menargetkan elemen yang berada tepat setelah elemen lain.

- General Sibling Selector (~):

    - Manfaat: Memilih elemen yang menjadi saudara sejajar dari elemen lain.
    - Kapan Digunakan: Ketika Anda ingin menargetkan elemen yang berhubungan sejajar dari elemen lain, tidak peduli seberapa jauh mereka berada.


### Jelaskan HTML5 Tag yang kamu ketahui.
- `<head>`:
Fungsi: Mengandung informasi tentang dokumen, seperti judul, meta-data, dan tautan ke berkas CSS atau JavaScript.

- `<title>`:
Fungsi: Menentukan judul halaman web yang akan ditampilkan di jendela atau tab browser.

- `<a>`:
Fungsi: Menentukan tautan ke halaman atau sumber daya eksternal.

- `<div>`:
Fungsi: Membuat kontainer blok untuk mengelompokkan dan memformat elemen.

- `<form>`, `<input>`, `<button>`:

Fungsi: Membuat formulir untuk mengumpulkan data dari pengguna.

### Jelaskan perbedaan antara margin dan padding.

- Margin adalah ruang di luar elemen, yang mempengaruhi seberapa jauh elemen tersebut dari elemen lain.

- Padding adalah ruang di dalam elemen, yang mempengaruhi seberapa jauh konten dari tepi elemen.

### Jelaskan perbedaan antara framework CSS Tailwind dan Bootstrap. Kapan sebaiknya kita menggunakan Bootstrap daripada Tailwind, dan sebaliknya?

Tailwind adalah kerangka kerja yang menerapkan pendekatan "utility-first," di mana pengguna membangun desain dengan menggabungkan kelas utilitas ke dalam elemen HTML. Ini menyediakan fleksibilitas dan kemampuan kustomisasi yang tinggi, tetapi juga memerlukan pemahaman yang lebih dalam. Bootstrap, di sisi lain, menyediakan sejumlah besar kelas CSS dan komponen yang telah dirancang sebelumnya. Ini memberikan stabilitas dan kemudahan penggunaan, tetapi dapat memiliki keterbatasan dalam fleksibilitas desain yang unik. Tailwind digunakan saat kita memiliki design yang memerlukan kustomisasi yang banyak, sedangkan bootstrap digunakan ketika kita ingin membuat web yang simple.

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

- Kustomisasi Login Page
    - Membuat dua div baru untuk page login dan untuk form.
    - Membuat div untuk form menjadi center.
    - Menambahkan form-controll untuk password dan username.
    - Mengubah style dari button login dan link register menggunakan bootstrap.

- Kustomisasi Register Page
    - Membuat dua div baru untuk page register dan untuk form.
    - Membuat div untuk form menjadi center.
    - Mengubah style dari button register menggunakan bootstrap.

- Kustomisasi Create Product Page
    - Membuat dua div baru untuk page create product dan untuk form.
    - Membuat div untuk form menjadi center.
    - Menambahkan form control untuk semua product di file forms.py.
    - Menambahkan back button.
    - Mengubah style dari button dengan menggunakan bootstrap.

- Kustomisasi Main Page
    - Membuat Navbar menggunakan bootstrap.
    - Menambahkan logo dan dropdown ke navbar.
    - Memindahkan button logout ke dropdown.
    - Memindahkan tulisan last login ke tengah bawah halaman.
    - Membuat teks yang berbeda saat pengguna tidak memiliki produk untuk ditampilkan.
    - Mengkustomisasi table menggunakan bootstrap.
    - Menambahkan if else untuk kustomisasi last row table

## Jawaban Soal Tugas 6

### Jelaskan perbedaan antara asynchronous programming dengan synchronous programming.
1. Asynchronous Programming:
    - Respon lebih cepat
    - Menggubakan callback (await/async) untuk mengatur operasi asinkron
    - Operasi dilakukan secara independen
2. Synchronous Programming:
    - Respon lebih lambat (Harus menunggu operasi sebelumnya selesai)
    - Tidak membutuhkan setup khusus seperti callback
    - Operasi dilakukan dengan berurutan

### Dalam penerapan JavaScript dan AJAX, terdapat penerapan paradigma event-driven programming. Jelaskan maksud dari paradigma tersebut dan sebutkan salah satu contoh penerapannya pada tugas ini.
Paradigma event-driven programming adalah pendekatan dalam pemrograman di mana eksekusi program dipicu oleh berbagai peristiwa yang terjadi selama runtime. Program tidak berjalan secara linier, melainkan menunggu dan merespons peristiwa tertentu dengan menjalankan blok kode atau fungsi khusus. Contohnya, dalam kode saya, ketika pengguna mengklik tombol "Add Product", hal ini akan memicu fungsi addProduct() untuk dieksekusi. Begitu juga dengan fungsi-fungsi lain seperti tambahProduct(), kurangProduct(), editProduct(), dan deleteProduct(), yang dipicu oleh interaksi pengguna terhadap elemen-elemen tertentu dalam halaman web. Dengan paradigma ini, program Anda berfungsi secara responsif terhadap tindakan pengguna dan peristiwa lainnya, meningkatkan interaktivitas dan pengalaman pengguna pada aplikasi web Anda.

### Jelaskan penerapan asynchronous programming pada AJAX.
Asynchronous programming pada AJAX memungkinkan eksekusi operasi IO seperti pengambilan data dari server atau tindakan jaringan lainnya tanpa menghentikan eksekusi program utama. Dengan menggunakan async dan await, kita dapat menandai fungsi-fungsi yang terlibat dalam operasi asynchronous. Contoh, penggunaan fetch dalam fungsi getProducts memungkinkan program untuk menunggu respons dari server sebelum melanjutkan ke langkah selanjutnya. Hal serupa terjadi pada fungsi addProduct, di mana await digunakan untuk menunggu hasil dari pengiriman data sebelum melakukan pembaruan produk dengan memanggil fungsi refreshProducts. Dengan demikian, asynchronous programming pada AJAX memungkinkan aplikasi web untuk tetap responsif dan efisien dalam menanggapi tindakan pengguna atau operasi jaringan yang memakan waktu.

### Pada PBP kali ini, penerapan AJAX dilakukan dengan menggunakan Fetch API daripada library jQuery. Bandingkanlah kedua teknologi tersebut dan tuliskan pendapat kamu teknologi manakah yang lebih baik untuk digunakan.

1. Fetch API
    - Terfokus pada tugas-tugas jaringan, tidak menyediakan banyak fitur tambahan di luar itu.
    - Lebih cepat dalam pengambilan dan pengiriman data karena tidak memerlukan pemuatan pustaka tambahan.
    - Lebih baru dan mungkin memerlukan polyfill atau pengaturan khusus untuk mendukung browser lama.

2. jQuery
    - Menyediakan banyak fungsi tambahan untuk manipulasi DOM, animasi, event handling, dan banyak lagi, membuatnya lebih komprehensif.
    - Meskipun sangat dioptimalkan, bisa sedikit lebih lambat dibandingkan dengan Fetch API dalam pengambilan dan pengiriman data karena pemuatan pustaka tambahan.
    - Didesain untuk bekerja dengan baik di berbagai browser, termasuk versi lama. Ini mengatasi banyak perbedaan lintas browser.

Pilihan antara Fetch API dan jQuery tergantung pada kebutuhan proyek dan preferensi pembuat web. Fetch API adalah pendekatan modern dan bawaan dari JavaScript, yang menawarkan performa tinggi dan sintaksis yang bersih berbasis Promise. JQuery baik untuk proyek-proyek baru yang fokus pada efisiensi dan tidak memerlukan dukungan browser lama. Ini adalah pilihan yang solid jika Anda perlu mendukung berbagai browser atau memanfaatkan berbagai fitur tambahan di luar AJAX. Jadi, pemilihan antara keduanya akan sangat tergantung pada kebutuhan dan lingkungan pengembangan proyek tertentu.

### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

1. AJAX GET
    - Mengubah bentuk tampilan data menjadi cards
    - Membuat method get_item yang mereturn data dalam bentuk json
    - Membuat method getProducts yang mengubah data dalam bentuk json menjadi objek JavaScript
    - Membuat method refreshProduct untuk menampilkan product setiap ada method yang dilakukan

2. AJAX POST
    - Membuat form di main.html untuk tambah produk baru menggunakan ajax
    - Membuat button yang akan memanggil form yang sudah dibuat
    - Membuat method baru dengan menggunakan AJAX di views.py yang akan digunakan untuk menambahkan produk ke database
    - membuat path dan routing
    - Menghubungkan form yang dibuat dengan method add product

3. Melakukan perintah collectstatic
    - Menambahkan kode `STATIC_ROOT = os.path.join(BASE_DIR, 'static')` di `settings.py`
    - Menjalankan `python manage.py collectstatic` pada terminal
    