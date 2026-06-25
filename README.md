## Soal 
1. Apa yang dimaksud dengan State, Action, dan Reward dalam Reinforcement Learning?
2. Apa fungsi dari Learning Rate (α)?
3. Apa fungsi dari Discount Factor (γ)?
4. Mengapa digunakan metode Exploration dan Exploitation?
5. Bagaimana perubahan nilai reward setelah training 2000 episode?
## Jawab 
1. a. State adalah representasi dari situasi atau kondisi lingkungan (environment) pada suatu waktu tertentu. Ini adalah "potret" dari apa yang dilihat atau diketahui oleh agen tentang dunianya saat itu.
       1) Dalam permainan catur: posisi semua bidak di papan
       2) Dalam mobil otonom: posisi mobil, kecepatan, jarak ke kendaraan lain, kondisi lalu lintas
       3)Dalam game video: posisi pemain, skor, nyawa yang tersisa
   b. Action adalah pilihan atau keputusan yang dapat diambil oleh agen ketika berada dalam suatu state tertentu. Agen memilih aksi ini berdasarkan kebijakan (policy) yang dimilikinya.
       1) Dalam catur: menggerakkan bidak tertentu ke posisi tertentu
       2) Dalam mobil otonom: belok kiri, belok kanan, mempercepat, mengerem
       3) Dalam game: bergerak maju, melompat, menembak
   c. Reward adalah sinyal numerik (biasanya berupa angka) yang diberikan lingkungan kepada agen sebagai feedback atas aksi yang diambil pada state tertentu. Reward ini menunjukkan seberapa "baik" atau "buruk" aksi tersebut dalam konteks tujuan yang ingin dicapai.
       1) Dalam catur: +1 jika menang, -1 jika kalah, 0 untuk langkah biasa
       2) Dalam mobil otonom: reward negatif jika menabrak, reward positif jika sampai tujuan dengan aman
       3)Dalam game: poin yang didapat saat mengumpulkan item
   
2. Learning Rate (a) adalah parameter yang mengontrol seberapa besar pembaruan yang dilakukan pada estimasi nilai (value) setiap kali agen mendapatkan informasi atau pengalaman baru.
   a = 0:Tidak ada pembelajaran sama sekali (nilai Q tidak pernah berubah)
   a = 1:Nilai a lama benar-benar diabaikan, hanya bergantung pada pengalaman terbaru saja
   Secara matematis, Learning Rate alpha berfungsi sebagai faktor pengali terhadap nilai gradien (kemiringan) dalam proses pembaruan bobot model. Ketika model mendeteksi kesalahan prediksi melalui loss function, algoritma gradient descent akan menghitung arah perubahan bobot yang harus diambil. Di sinilah learning rate masuk untuk menentukan seberapa jauh model akan melangkah ke arah tersebut. Jika nilai alpha diatur terlalu besar, model akan mengambil langkah yang terlalu drastis, sehingga berisiko melompati titik optimal (minimum global) dan menyebabkan proses pelatihan menjadi tidak stabil atau gagal memusat (diverge). Sebaliknya, jika nilai alpha terlalu kecil, penyesuaian bobot akan berjalan sangat lambat dan memerlukan waktu komputasi yang jauh lebih lama, bahkan berisiko terjebak pada area landai yang salah (local minima atau saddle point) sebelum berhasil mencapai performa terbaiknya. Oleh karena itu, menentukan nilai learning rate yang pas sangat krusial untuk memastikan model dapat belajar dengan cepat namun tetap akurat.
   
3. Discount Factor (y) adalah parameter dengan rentang nilai 0 hingga 1 yang berfungsi menentukan seberapa besar bobot atau pentingnya reward di masa depan dibandingkan dengan reward saat ini dalam perhitungan nilai kumulatif (return).
   y mendekati 0: agen bersifat myopic (berpandangan sempit), hanya mempertimbangkan reward langsung/segera dan mengabaikan konsekuensi jangka panjang.
   y mendekati 1: agen bersifat farsighted (berpandangan jauh), mempertimbangkan reward di masa depan hampir sama pentingnya dengan reward saat ini
   y = 0: agen hanya mengoptimalkan reward sesaat tanpa memperhitungkan masa depan sama sekali
   y = 1: seluruh reward di masa depan dihitung penuh tanpa pengurangan (hanya valid untuk episodic task, karena pada continuing task nilai return bisa menjadi tidak terbatas)
   Dalam praktiknya, y biasanya dipilih cukup tinggi (misalnya 0.9 sampai 0.99) untuk tugas yang membutuhkan perencanaan jangka panjang, seperti permainan strategi atau navigasi robot

4. Exploration tindakan agen mencoba aksi baru atau yang belum banyak diketahui untuk mendapatkan informasi lebih lanjut tentang lingkungan
   Exploitation tindakan agen memilih aksi yang sudah diketahui memberikan reward terbaik berdasarkan pengetahuan yang dimiliki saat ini
   Dalam bidang Machine Learning, khususnya Reinforcement Learning (RL), metode Exploration (eksplorasi) dan Exploitation (eksploitasi) digunakan bersama untuk memecahkan dilema mendasar dalam proses pengambilan keputusan. Tujuan utama dari kedua metode ini adalah untuk menemukan strategi atau kebijakan terbaik (optimal policy) guna memaksimalkan keuntungan atau imbalan (reward) jangka panjang.
   Keseimbangan antara keduanya (Exploration-Exploitation Trade-off) sangat krusial karena model tidak bisa melakukan keduanya secara bersamaan dalam satu langkah. Jika model terlalu fokus pada eksplorasi, ia akan membuang-buang waktu dan sumber daya untuk mencoba opsi yang buruk. Namun, jika model terlalu fokus pada eksploitasi, ia akan terjebak pada pilihan yang "cukup baik" saat itu (sub-optimal) dan melewatkan pilihan terbaik yang sebenarnya. Oleh karena itu, kombinasi kedua metode ini digunakan secara dinamis—biasanya memperbanyak eksplorasi di awal pelatihan dan perlahan beralih ke eksploitasi saat model mulai cerdas—agar proses belajar berjalan efektif dan menghasilkan keputusan yang paling optimal.

5. Sebagai gambaran umum, secara teori, pola perubahan reward selama training RL biasanya mengikuti tren seperti ini:
   1) Episode awal (0–500-an) → reward cenderung rendah dan fluktuatif, karena agen masih banyak melakukan exploration dan policy belum terbentuk dengan baik
   2) Episode pertengahan (500–1500-an) → reward mulai meningkat secara bertahap seiring agen mempelajari pola lingkungan, meskipun masih ada fluktuasi akibat noise atau sisa eksplorasi
   3) Episode akhir (mendekati 2000) → reward cenderung stabil di nilai yang lebih tinggi (atau mendekati optimal), karena ε (epsilon) sudah mengecil sehingga agen lebih banyak melakukan exploitation dari policy yang sudah dipelajari
   Setelah melewati 2000 episode pelatihan, nilai reward idealnya akan melonjak naik secara signifikan dan mulai stabil (konvergen) di titik tertinggi. Pada awal episode, reward biasanya sangat rendah atau bernilai negatif karena model masih aktif bereksplorasi secara acak dan sering membuat kesalahan. Namun, seiring berjalannya waktu, model mulai mengeksploitasi tindakan yang benar sehingga grafik reward meningkat tajam hingga akhirnya mendatar di sekitar episode ke-2000, yang menandakan agen telah berhasil menemukan strategi optimal. Jika setelah 2000 episode nilai reward masih rendah atau terus naik-turun secara drastis, artinya proses pelatihan mengalami kegagalan akibat masalah pada algoritma atau lingkungan yang terlalu kompleks.


## Tugas Lanjutan 
Modifikasi Program Sehingga:
Menggunakan environment Taxi-v3 Menampilkan rata-rata reward setiap 100 episode Membandingkan Hasil training 1000,2000,5000 episode

hasil 100
<img width="1041" height="783" alt="image" src="https://github.com/user-attachments/assets/1a850777-bfce-4175-905f-4b326d3ff15d" />

hasil 1000
<img width="1076" height="780" alt="image" src="https://github.com/user-attachments/assets/17efb9eb-fde2-4b73-92d9-8424b3fc01ba" />

hasil 2000 
<img width="1067" height="774" alt="image" src="https://github.com/user-attachments/assets/694dde4e-b1a8-4bf1-b7d7-42f35c98f68e" />

hasil 5000
<img width="1084" height="792" alt="image" src="https://github.com/user-attachments/assets/2149f918-1de1-4aac-afad-36c07c5dcaef" />


