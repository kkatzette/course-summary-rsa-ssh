# course-summary-rsa-ssh
sudah mencoba hands-on, memperbaiki error-error yang muncul selama percobaan
## pertanyaan-lain
Apa keuntungan RSA key dibanding password?
RSA key itu secara umum jauh lebih aman dibanding password biasa. Kalau pakai password, apalagi yang gampang ditebak atau sama di banyak tempat, itu rawan banget kena brute-force atau dicuri lewat phishing. Sementara RSA pakai sistem key pair — ada public dan private key — jadi autentikasinya bukan cuma berdasarkan teks yang kita ketik, tapi berdasar bukti matematis yang lebih susah dibobol. Selain itu, dengan RSA key jadi gak perlu ngetik password tiap login (kalau gak pakai passphrase), jadi selain aman, juga praktis.
Mengapa private key harus dirahasiakan?
Private key itu kayak kunci servernya. Kalau sampai orang lain pegang, bisa masuk ke server kapan aja tanpa kita tahu. Karena public key bisa dishare ke mana-mana, keamanannya sepenuhnya bergantung ke seberapa aman kita simpan private key-nya. Biasanya disimpan di ~/.ssh/id_rsa, dan idealnya dilindungi juga pakai passphrase. Jadi walaupun filenya ketahuan, tetep ada lapisan pengaman tambahan.
Bagaimana kriptografi RSA bekerja dalam proses login SSH?
Secara konsep, waktu kita login pakai SSH dan RSA key, server bakal kirim semacam “tantangan” (challenge) yang cuma bisa dijawab dengan benar kalau kita punya private key yang cocok sama public key yang sebelumnya udah dikasih ke server. Jadi bukan kayak kirim password, tapi kayak buktiin identitas kita dengan bisa "menandatangani" challenge itu. Kalau berhasil, berarti kita yang punya private key-nya, dan server kasih akses. Proses ini semua udah dienkripsi dan jalan otomatis di balik layar.
Apa risiko jika file id_rsa bocor?
Kalau file id_rsa bocor, itu kayak kita secara gak sengaja ngasih kunci rumah kita ke orang asing. Siapapun yang punya file itu bisa akses ke semua server yang udah kita daftarin public key-nya — tanpa perlu password. Makanya penting banget jaga file itu baik-baik, jangan disebar, dan idealnya dikasih passphrase juga. Kalau sampai bocor, solusi paling cepat adalah ganti key pair baru, dan update public key di server.
