# Muhammad Madhani Putra
# PBP A - 2206028503

## Link Aplikasi 
Link Adaptable: [Madanshop](https://madanshop.adaptable.app/main/)

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
