# Belajar pasal gRPC

## Kenapa belajar pasal gRPC?

Dalam persediaan untuk interview dengan sebuah syarikat startup ni, recruiter suruh aku baca pasal gRPC. Mungkin dalam syarikat startup ni, gRPC digunakan

## Apa itu gRPC?

Ia sebuah framework untuk komunikasi antara microservice yang berlainan bahasa.
Selama ni aku hanya pernah guna REST API untuk menghubungkan
microservice dengan microserice, atau
microservice dengan frontend.
Rupanya, gRPC ini dianggap sebagai cara perhubungan baru yang sedikit demi sedikit akan menggantikan REST API.

# Jap, hang belum cerita lagi apa mende gRPC ni

gRPC ni singkatan untuk Google Remote Procedure Call.
Daripada namanya kita tahu, ia adalah versi Google untuk Remote Procedure Call. RPC ni rupanya sebuah framework yang dah lama dicipta, malah sebelum REST API lagi, iaitu pada tahun 1970an. REST API dicipta pada 1997. gRPC pula pada 2015.
RPC dianggap sudah tak digunapakai pada masa sekarang. gRPC dikatakan lebih pantas daripada REST API. Namun, gRPC belum digunapakai secara meluas kerana ia mengambil lebih banyak masa untuk diimplementasi ke dalam kod. Menurut penulis [blog ini](https://blog.dreamfactory.com/grpc-vs-rest-how-does-grpc-compare-with-traditional-rest-apis/) , beliau cuma perlukan 10 minit untuk mengimplementasi REST API ke dalam kodnya, berbanding 45 minit untuk gRPC.

## Apa yang membuat gRPC lebih baik?

gRPC membolehkan sesebuah data dalam microservice diubah ke dalam bentuk byte sebelum dihantar ke microservice yang lain. Hal ini berbeza dengan REST API yang memanfaatkan JSON, sebuah format berbentuk teks yang tentunya bersaiz lebih besar berbanding data berbentuk byte.
Bagaimana gRPC mengubah data microservice ke dalam bentuk byte?

gRPC dilengkapi sebuat compiler bernama protoc yang bertanggungjawab mengubah data dalam microservice ke dalam bentuk byte dan sebaliknya.
Mungkin sedikit sukar untuk dijelaskan dalam beberapa ayat, tapi saya cuba juga.
Begini, gRPC memanfaatkan apa yang dipanggil format Protocol buffer, di mana sesebuah unit data diisytiharkan dalam bentuk service dan message. Pengisytiharan ini dibuat dalam sebuah fail teks yang berakhir dengan nama .proto. Fail ini diletakkan di dalam projek microservice. Kemudian, menggunakan protoc, kita akan hasilkan fail dalam bahasa yang sama dengan microservice kita, yang membolehkan kita memanipulasi data tersebut di dalam projek kita. Ok, selesai sudah bahagian menghubungkaitkan data gRPC dengan data dalam microservice.

Untuk bahagian penghantaran/penerimaan data dari sebuah microservice yang mengimplementasi gRPC kepada sebuah microservice lain yang juga mengimplementasi gRPC, ia dijalankan sama seperti client dan server dalam kes REST API. (Tidaklah 100% sama, kerana gRPC juga membolehkan pemulaan penghantaran dua hala, manakala REST API hanya membolehkan pemulaaan penghantaran data dibuat oleh client sahaja).
Oleh kerana data yang dihantar melalui gRPC ini berbentuk byte, ia boleh dimampatkan supaya data penghantaran lebih ringan dan cepat. Sebut pasal kecepatan penghantaran, gRPC dikendali di bawah protokol HTTP2. Berbanding HTTP1.1 yang digunakan untuk REST API, HTTP2 menyebabkan data dihantar dalam bentuk binari, dan bukan teks. Ini malah menyumbang kepada kelajuan gRPC lagi.

## Rumusan

Ada banyak perkara yang saya belum sentuh mengenai gRPC dalam entri ini. Mungkin dalam kupasan berikut, saya akan terangkan lebih lanjut, misalnya tentang bagaimana implementasi gRPC berbanding REST API.

## Rujukan

- https://grpc.io/about/
- https://developers.google.com/protocol-buffers/docs/overview
- https://blog.dreamfactory.com/grpc-vs-rest-how-does-grpc-compare-with-traditional-rest-apis/
- https://grpc.io/blog/wireshark/
