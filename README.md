# gRPC Polyglot Lab

## Analisis Pendekatan Kompilasi

Pada pendekatan static code generation (Go dan Python), file user.proto dikompilasi lebih dulu oleh protoc menjadi kode sumber (user.pb.go, user_grpc.pb.go, user_pb2.py, user_pb2_grpc.py) yang menjadi bagian dari proyek. Struktur pesan dan stub service sudah ada sebagai kode bahasa tersebut sebelum program dijalankan, sehingga tipe data lebih terjamin saat kompilasi dan performanya baik, tetapi setiap perubahan .proto mengharuskan kompilasi ulang. Pada dynamic runtime generation (Node.js), file .proto dibaca dan diurai saat program berjalan melalui @grpc/proto-loader, sehingga tidak ada file hasil generate dan perubahan skema langsung berlaku setelah program dijalankan ulang. Konsekuensinya, tidak ada pengecekan tipe saat kompilasi dan ada sedikit biaya parsing saat startup.
