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
   
3. Discount Factor (y) adalah parameter dengan rentang nilai 0 hingga 1 yang berfungsi menentukan seberapa besar bobot atau pentingnya reward di masa depan dibandingkan dengan reward saat ini dalam perhitungan nilai kumulatif (return).
   y mendekati 0: agen bersifat myopic (berpandangan sempit), hanya mempertimbangkan reward langsung/segera dan mengabaikan konsekuensi jangka panjang.
   y mendekati 1 → agen bersifat farsighted (berpandangan jauh), mempertimbangkan reward di masa depan hampir sama pentingnya dengan reward saat ini
