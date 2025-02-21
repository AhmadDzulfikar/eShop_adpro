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
