# Muhammad Madhani Putra
# PBP A - 2206028503

## Link Aplikasi 
Link Adaptable: -

## Jawaban Soal

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