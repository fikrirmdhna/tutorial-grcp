# Tutorial-9 
## Fikri Dhiya Ramadhana
## 2206819533
## AdvProg-C

### Reflection
1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?
    * Unary RPC:  
    satu request diikuti dengan satu respon. Hal ini cocok untuk discrete operations yang tidak membutuhkan continuous data transfer. 
    * Server Streaming RPC:  
    Klien mengirim request lalu akan direspon melalui server. Hal ini cocok untuk skenario dimana server butuh update data continually, seperti live data feeds. 
    * Bidirectional Streaming RPC:  
    Baik client maupun server dapat mengirimkan rangkaian pesan satu sama lain secara full duplex. Hal ini cocok untuk aplikasi waktu nyata seperti layanan obrolan atau sistem pemrosesan data waktu nyata di mana kedua ujung komunikasi mungkin perlu mengirim dan menerima data secara tidak teratur.

2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?  
    * Authentication and Authorization:  
    Menerapkan otentikasi berbasis token yang aman (seperti JWT) atau mengintegrasikan dengan sistem auth yang ada (OAuth2) untuk memvalidasi identitas pengguna.

    * Data Encryption:  
    Menggunakan TLS/SSL untuk mengenkripsi data yang ditransmisikan melalui jaringan, melindungi dari penyadapan dan manipulasi.

    * Input Validation:  
    Untuk mencegah injeksi dan bentuk serangan lainnya, sangat penting untuk memvalidasi dan membersihkan semua input.

3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?  
    * Error Handling:  
    Mengelola stream errors dan disconnections in real-time applications. 
    * Concurrency Management:  
    Menangani asynchronous streams dan memastikan keamanan thread yang cukup kompleks.
    * Resource Management:  
    Memastikan efisiensi alokasi resource dan cleanup agar tidak terjadi memory leaks yang berkepanjangan.

4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?  
    * Advantages:  
    Membantu dalam menjembatani gap yang ada di antara Tonic dan Tokio asychronous models.
    * Disadvantages:  
    Menambahkan lapisan abstraksi yang mungkin memperkenalkan overhead dan dapat mempersulit aliran kontrol, membuat debugging menjadi lebih sulit.

5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?  
    * Service Traits:  
    Mendefinisikan service traits yang jelas untuk setiap komponen untuk memfasilitasi pengujian dan substitusi yang mudah.
    * Perpustakaan Bersama:  
    Fungsionalitas umum seperti penanganan kesalahan, pencatatan, atau metrik dapat dikapsulkan dalam perpustakaan bersama.
    * Middleware/Interceptors:  
    Menggunakan middleware atau interceptors untuk masalah lintas potong seperti otentikasi atau pencatatan.

6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?  
    * Manajemen Transaksi: Menerapkan mekanisme transaksi database untuk memastikan integritas data.
    * Integrasi dengan Layanan Eksternal: Mengelola integrasi dengan API perbankan atau gateway pembayaran.
    * Penanganan Kesalahan dan Mekanisme Ulangi Otomatis: Menerapkan penanganan kesalahan yang kuat dan mungkin mekanisme pengulangan otomatis untuk transaksi yang gagal.

7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?
    * Interoperabilitas:  
    gRPC memfasilitasi antarmuka bahasa-agnostik dengan Protocol Buffers, mendukung sistem poliglot.
    * Kinerja:  
    Memanfaatkan HTTP/2 untuk kinerja yang dtingkatkan dengan fitur seperti kompresi header dan multiplexing.
    * Definisi Layanan:  
    Definisi layanan yang kuat meningkatkan ketangguhan tetapi memerlukan pengelolaan skema yang ketat.

8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?
    * Advantages:  
    HTTP/2 mendukung multiplexing, mengurangi overhead dalam koneksi dan latensi, dan kemampuan server push.
    * Disadvantages:  
    Kompleksitas dalam implementasi dan pemecahan masalah, dan tidak semua lingkungan mendukung HTTP/2 secara penuh.

9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?
    * API REST:  
    Cocok untuk operasi stateless dengan kompatibilitas luas tetapi dibatasi oleh model permintaan/respons.
    * gRPC:  
    Memungkinkan interaksi waktu nyata, stateful, menawarkan kinerja yang lebih tinggi untuk streaming data tetapi lebih kompleks dan kurang didukung luas dalam hal ekosistem klien.

10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?
    * gRPC dengan Protocol Buffers:  
    Memastikan kontrak yang jelas, keamanan tipe, dan efisiensi dalam serialisasi.
    * JSON dalam REST:  
    Menawarkan fleksibilitas dan debugging yang lebih mudah dengan biaya overhead dalam parsing dan kurangnya ketatnya pengetikan, yang dapat memperkenalkan kesalahan runtime.
