# TUTORIAL 1
## Refleksi 1
#### You already implemented two new features using Spring Boot. Check again your source code and evaluate the coding standards that you have learned in this module. Write clean code principles and secure coding practices that have been applied to your code.  If you find any mistake in your source code, please explain how to improve your code. Please write your reflection inside the repository's README.md file.

Dalam implementasi fitur CRUD pada aplikasi menggunakan Spring Boot, saya berusaha menerapkan prinsip-prinsip clean code dan praktik coding yang aman. Sebagai contoh, saya telah menggunakan penamaan yang bermakna pada variabel, metode, dan kelas, seperti pada kelas ProductController, ProductService, dan ProductRepository, yang menggambarkan dengan jelas fungsinya. Penggunaan anotasi Spring seperti @Autowired, @Controller, dan @RequestMapping juga telah dilakukan dengan baik, memastikan kode dapat dipahami dengan mudah oleh pengembang lain.

Namun, ada beberapa area yang masih bisa ditingkatkan. Salah satunya adalah di bagian validasi input. Misalnya, pada saat membuat atau mengedit produk, tidak ada validasi untuk memastikan bahwa data yang dimasukkan (seperti nama produk atau jumlah produk) sudah benar atau tidak kosong. Penggunaan anotasi seperti @NotNull, @Size, atau @Min di kelas Product bisa diterapkan untuk meningkatkan validasi dan mencegah data yang tidak valid dimasukkan ke dalam sistem.

Selain itu, meskipun aplikasi ini berfungsi dengan baik secara teknis, penanganan error yang lebih mendalam dapat diterapkan pada tingkat service dan repository untuk mengatasi kasus-kasus seperti produk yang tidak ditemukan atau kesalahan saat melakukan operasi database.

Dari segi Git flow, saya menggunakan pendekatan feature branch dan memastikan bahwa setiap fitur dikembangkan secara terpisah sebelum digabungkan ke branch utama melalui pull request. Ini memastikan kode yang dikembangkan tetap bersih dan dapat diatur dengan baik, meminimalkan konflik penggabungan.

## Refleksi 2
#### After writing the unit test, how do you feel? How many unit tests should be made in a class? How to make sure that our unit tests are enough to verify our program? It would be good if you learned about code coverage. Code coverage is a metric that can help you understand how much of your source is tested. If you have 100% code coverage, does that mean your code has no bugs or errors? 
Setelah menulis unit test, saya merasa lebih percaya diri bahwa aplikasi ini berjalan dengan baik dan sesuai dengan yang diinginkan. Unit test memberikan keyakinan bahwa fitur-fitur yang telah dikembangkan berfungsi sesuai dengan yang diharapkan. Dalam sebuah class, jumlah unit test yang diperlukan bergantung pada jumlah fungsi yang ada dalam class tersebut. Sebagai aturan umum, setiap fungsi minimal harus memiliki satu unit test yang menguji skenario dasar atau fitur utamanya. Namun, praktik terbaik adalah menulis unit test untuk setiap kemungkinan skenario, baik yang positif maupun negatif. Sebagai contoh, pada fitur edit produk, unit test untuk kasus positif bisa menguji apakah produk berhasil diubah, sedangkan untuk kasus negatif, bisa menguji apakah sistem menangani situasi ketika produk yang ingin diedit tidak ditemukan.

Untuk memastikan bahwa unit test sudah cukup untuk memverifikasi program, kita perlu memastikan bahwa setiap cabang dan kondisi dalam fungsi sudah diuji

#### Suppose that after writing the CreateProductFunctionalTest.java along with the corresponding test case, you were asked to create another functional test suite that verifies the number of items in the product list. You decided to create a new Java class similar to the prior functional test suites with the same setup procedures and instance variables. What do you think about the cleanliness of the code of the new functional test suite? Will the new code reduce the code quality? Identify the potential clean code issues, explain the reasons, and suggest possible improvements to make the code cleaner!

Pembuatan kelas baru yang mirip dengan functional test sebelumnya dapat menurunkan kebersihan kode karena duplikasi kode pada setup seperti pengaturan port dan URL dasar. Untuk meningkatkan kebersihan kode, sebaiknya buatlah superclass atau abstract class yang menangani setup umum, lalu digunakan di kelas tes lainnya. Hal ini akan mengurangi redundansi, membuat kode lebih terorganisir, dan meningkatkan readability. Dengan pendekatan ini, kita dapat meminimalkan duplikasi, menjaga kualitas kode, dan memudahkan pemeliharaan.

# TUTORIAL 2:
## Refleksi 1
#### List the code quality issue(s) that you fixed during the exercise and explain your strategy on fixing them.
a. Saya menyelesaikan masalah `Unnecessary modifier 'public' on method 'delete': the method is declared in an interface type` dengan cara menghapus public pada interface-interface yang bermasalah.
b. Menghapus import yang tidak digunakan atau tidak diperlukan yakni import org.springframework.web.bind.annotation.*;, menjadi import hal-hal yang digunakan saja dari package tersebut.
c. Dan saya menyelesaikan masalah `This utility class has a non-private constructor` dengan cara menghapus public pada bagian yang dibutuhkan.

## Refleksi 2
#### Look at your CI/CD workflows (GitHub)/pipelines (GitLab). Do you think the current implementation has met the definition of Continuous Integration and Continuous Deployment? Explain the reasons (minimum 3 sentences)!
Menurut saya, CI/CD workflow yang saya implementasikan sudah memenuhi definisi Continuous Integration dan Continuous Deployment. Pada bagian Continuous Integration, setiap kali ada push atau pull request, sistem otomatis menjalankan build dan unit test untuk memastikan kualitas kode. Selain itu, saya menggunakan tool seperti PMD untuk mendeteksi potensi masalah keamanan secara langsung. Untuk Continuous Deployment, saya menggunakan layanan otomatis untuk melakukan deployment ke lingkungan produksi setiap kali ada perubahan pada branch utama, memastikan aplikasi selalu up-to-date tanpa intervensi manual.

# TUTORIAL 3:
## Refleksi 1:
### Explain what principles you apply to your project!
a. Single Responsibility Principle (SRP) adalah salah satu prinsip dalam SOLID yang menyatakan bahwa sebuah kelas atau modul harus memiliki satu alasan untuk berubah, yang berarti setiap kelas hanya boleh memiliki satu tanggung jawab utama. Dalam proyek saya, saya sudah menerapkan SRP dengan cara memisahkan `CarController` dan `ProductController`. `CarController` hanya bertanggung jawab untuk menangani operasi yang berhubungan dengan Car, seperti  membuat, mengedit, menghapus, dan menampilkan daftar mobil. Sedangkan ProductController bertanggung jawab untuk menangani operasi pada produk secara umum.

b. Selain itu, saya juga sudah menerapkan prinsip DIP. Prinsip ini menyatakan bahwa kelas-kelas tingkat tinggi tidak boleh bergantung langsung pada kelas-kelas tingkat rendah, tetapi keduanya harus bergantung pada abstraksi. 
Pada proyek ini, saya telah menerapkan DIP dengan cara sebagai berikut:
- CarRepositoryInterface dibuat untuk mengabstraksi implementasi repository, yang sebelumnya langsung bergantung pada CarRepository konkret. Dengan ini, saya bisa mengganti implementasi penyimpanan data tanpa mempengaruhi logika yang ada di service.
- `CarServiceImpl` sekarang bergantung pada `CarRepositoryInterface`, yang memungkinkan saya untuk mengganti implementasi penyimpanan atau menambahkan penyimpanan baru tanpa merubah service.
- `CarController` juga tetap bergantung pada `CarService (interface)`, memastikan controller tidak terikat pada implementasi konkret dari service.

c. Open/Closed Principle (OCP) menyatakan bahwa kelas harus terbuka untuk ekstensi, tetapi tertutup untuk modifikasi. Saya sudah menerapkan ini dengan cara CarServiceImpl mengimplements CarService.

## Refleksi 2:
### Explain the advantages of applying SOLID principles to your project with examples.
- Pemeliharaan Kode yang Lebih Mudah (Single Responsibility Principle - SRP)
Dengan memisahkan tanggung jawab dalam berbagai kelas, seperti CarController yang hanya menangani operasi terkait car, dan ProductController yang menangani operasi terkait produk, kita dapat lebih mudah melakukan pemeliharaan kode. Misalnya, jika ada perubahan pada logika yang berhubungan dengan car, kita hanya perlu mengubah CarController tanpa memengaruhi bagian lain yang berhubungan dengan produk. 

- Penerapan DIP pada proyek ini memberikan fleksibilitas yang lebih tinggi dalam hal penggantian atau perbaikan implementasi kelas yang lebih rendah tanpa mengubah kelas tingkat tinggi. Misalnya, dengan menggunakan CarRepositoryInterface, ini dapat mengganti implementasi penyimpanan data, seperti beralih dari penyimpanan berbasis file ke database, tanpa perlu mengubah kode dalam CarServiceImpl.

- Dengan prinsip OCP, kelas seperti CarServiceImpl dapat diperluas dengan menambahkan fungsionalitas baru tanpa mengubah kode yang sudah ada. Sebagai contoh, jika ingin menambahkan fitur baru pada CarServiceImpl, seperti fitur pencarian mobil, bisa membuat subclass atau implementasi baru tanpa memodifikasi implementasi yang ada. Ini mengurangi risiko bug dan memastikan bahwa fitur yang ada tetap stabil saat pengembangan berlanjut.

## Refleksi 3:
### Explain the disadvantages of not applying SOLID principles to your project with examples.
- Jika satu kelas memiliki lebih dari satu tanggung jawab, seperti jika CarController juga mengelola logika produk atau fungsionalitas lainnya, kode menjadi lebih sulit dipahami dan dimodifikasi. Misalnya, jika ada perubahan pada logika terkait mobil dan produk, harus mengubah satu kelas yang sangat kompleks, yang berisiko menyebabkan bug dan memperlambat proses pemeliharaan. 

- Tanpa penerapan DIP, kelas tingkat tinggi akan bergantung langsung pada kelas tingkat rendah, yang membuat kode menjadi sulit untuk diperbarui. Misalnya, jika CarServiceImpl langsung bergantung pada implementasi CarRepository yang konkret, perubahan pada cara penyimpanan data akan mengharuskan untuk mengubah kode di berbagai tempat, termasuk service dan controller, yang sangat berisiko mengganggu fungsionalitas yang ada. 

- Jika kode tidak mengikuti prinsip OCP, maka menambahkan fitur baru akan memerlukan perubahan langsung pada kelas yang sudah ada, bukannya cukup memperluasnya. Misalnya, jika ingin menambahkan fungsionalitas pencarian dalam CarServiceImpl, mungkin harus mengubah banyak bagian dari kode yang ada, yang berisiko menimbulkan bug atau merusak fungsionalitas yang sudah ada.



# TUTORIAL 4
## Refleksi 1:
Manfaat TDD
Pendekatan TDD memaksa saya untuk mendefinisikan ekspektasi dan perilaku kode sebelum implementasi. Dengan menulis pengujian terlebih dahulu, saya menjadi lebih fokus pada tujuan fungsi yang ingin dicapai, sehingga proses debugging pun menjadi lebih cepat karena setiap kegagalan pada test langsung menunjukkan area yang perlu diperbaiki. Secara keseluruhan, TDD sangat berguna dalam memberikan feedback instan dan menjaga agar kode selalu sesuai dengan spesifikasi yang diharapkan.

Tantangan dan Ruang Perbaikan
Meskipun TDD memberikan banyak manfaat, ada beberapa aspek yang perlu saya perbaiki di masa depan:

- Cakupan Kasus Uji: Terkadang, saya menyadari ada skenario atau edge case yang terlewat. Berdasarkan pertanyaan reflektif Percival (2017), saya perlu lebih sistematis dalam merancang test case agar dapat mencakup semua kondisi, termasuk skenario error atau kondisi tak terduga.
- Desain Pengujian: Sebagai pendatang baru dalam TDD, saya masih menghadapi kesulitan dalam menyusun desain test yang optimal. Ke depan, saya perlu mempelajari lebih lanjut teknik pembuatan test case yang lebih terstruktur agar setiap test benar-benar menggambarkan satu unit perilaku yang spesifik.

## Refleksi 2:
Fast (Cepat):
Pengujian saya umumnya berjalan dengan cepat karena tidak bergantung pada resource eksternal (misalnya, akses basis data atau jaringan). Hal ini mendukung workflow pengembangan yang efisien.

Independent (Mandiri):
Saya telah menerapkan anotasi seperti @BeforeEach untuk memastikan tiap test dijalankan dalam kondisi bersih dan tidak saling bergantung. Namun, perlu diwaspadai agar setiap test benar-benar tidak meninggalkan efek samping yang dapat memengaruhi test lain.

Repeatable (Dapat Diulang):
Tes saya dapat diulang dengan hasil yang konsisten di berbagai lingkungan (lokal maupun CI). Untuk lebih meningkatkan repeatability, saya akan memastikan semua data test disiapkan secara lokal di setiap test case.

Self-Validating (Mengautentikasi Diri):
Penggunaan assertion seperti assertEquals, assertNull, dan assertThrows telah membantu menjadikan tes saya pass/fail secara otomatis. Di masa depan, saya akan berupaya menambahkan validasi yang lebih detail untuk kondisi-kondisi error agar setiap aspek fungsi dapat diverifikasi secara menyeluruh.

Timely (Tepat Waktu):
Dengan menulis test terlebih dahulu sebelum implementasi, saya sudah cukup menerapkan prinsip timely. Pendekatan ini membuat saya lebih fokus dalam mengembangkan kode yang benar-benar modular dan mudah diuji. Meski demikian, saya menyadari bahwa menulis tes tambahan setelah refactoring juga penting untuk memastikan tidak ada fungsionalitas yang rusak.

Kesimpulan
Secara keseluruhan, saya menilai alur TDD yang saya gunakan sudah sangat membantu dalam mengarahkan pengembangan kode dan memberikan feedback cepat. Namun, saya perlu meningkatkan cakupan kasus uji dan menyempurnakan desain test untuk memastikan bahwa setiap kemungkinan (termasuk kondisi edge dan error) telah tertangani. Begitu pula, prinsip F.I.R.S.T sudah sebagian besar saya terapkan dengan baik, tetapi masih ada ruang perbaikan terutama dalam aspek independensi dan validasi yang lebih menyeluruh.

Dengan refleksi ini, saya berkomitmen untuk terus belajar dan mengadaptasi praktik terbaik dalam penulisan test, sehingga di iterasi pengembangan berikutnya, kualitas pengujian dan desain kode dapat semakin meningkat.
