LAPORAN PRAKTIKUM 6 SISTEM OPERASI
JOB CONTROL
1. Eksekusi seluruh profil yang ada:
a. Edit file profil /etc/profile dan tampilkan pesan sebagai berikut:
echo “Profile dari /etc/profile”
![Screenshot 2024-09-26 113844](https://github.com/user-attachments/assets/66c8f7fb-bec0-4143-81eb-2881fd1e5f32)
![Screenshot 2024-09-26 114055](https://github.com/user-attachments/assets/ce2e70e6-5137-492a-9225-4ceb771d9a03)
b. Asumsi nama Anda stD02001, maka edit semua profil yang ada yaitu:
/home/stD02001/.bash_profile
/home/.stD02001/.bash_login
/home/mahasiswa/.profile
/home/mahasiswa/.bashrc
Ganti nama /home/mahasiswa dengan nama anda sendiri. Pada setiap file tersebut, cantumkan instruksi echo, misalnya pada /home/mahasiswa/.bash_profile :
echo “Profile dari .bash_profile”
Lakukan hal yang sama untuk file lainnya, sesuaikan tampilan dengan nama file yang bersangkutan.
![Screenshot 2024-09-26 114332](https://github.com/user-attachments/assets/cb423f9c-a3c6-45df-bfde-776fd9607164)
![Screenshot 2024-09-26 114514](https://github.com/user-attachments/assets/78e5a4bc-6cb5-417f-b15e-3cd06edccd38)
![Screenshot 2024-09-26 114524](https://github.com/user-attachments/assets/4767b2a4-4594-4796-b72a-3bb00933809e)
![Screenshot 2024-09-26 114542](https://github.com/user-attachments/assets/6985ae65-070d-4a87-a6de-85136d39ab3c)
![Screenshot 2024-09-26 114556](https://github.com/user-attachments/assets/d55e08e1-419c-49e3-b42b-001237d5dadf)
Jalankan instruksi substitute user, kemudian keluar dengan perintah exit sebagai berikut:
![Screenshot 2024-09-26 213259](https://github.com/user-attachments/assets/c227fbdd-8fa2-474e-9ce4-ec42fd0c15f0)
Perbedaan kedua utilitas tersebut:
1. su mahasiswa:
Perintah ini menjalankan su untuk beralih ke user mahasiswa. Saat menggunakan perintah ini tanpa opsi -, lingkungan (environment) dari user saat ini tetap dipertahankan. Artinya, hanya identitas pengguna yang berubah, tetapi variabel lingkungan seperti PATH tidak akan berubah. Jadi, variabel lingkungan dan direktori kerja yang sedang aktif tetap sama seperti sebelumnya.
2. su - mahasiswa:
Perintah ini menggunakan opsi - yang dikenal sebagai login shell. Opsi ini melakukan login penuh sebagai user mahasiswa, sehingga environment yang dimuat adalah environment milik mahasiswa secara lengkap. Ini termasuk mengubah direktori kerja ke home directory user mahasiswa dan memuat variabel lingkungan seperti yang didefinisikan dalam shell milik mahasiswa. Jadi, ini seperti memulai sesi baru sebagai user mahasiswa.
2. Prompt String (PS1)
A. Edit file .bash_profile, ganti prompt PS1 dengan > sebagai prompt. Instruksi export diperlukan dengan parameter nama variable tersebut, agar perubahan variable PS1 dikenali oleh semua shell yang berjalan.
![Screenshot 2024-09-26 215948](https://github.com/user-attachments/assets/7a097628-52cf-4a62-80fa-865890ad972d)
![Screenshot 2024-09-26 220026](https://github.com/user-attachments/assets/ad3641ea-f0c6-45e1-9b10-d44bb4963f18)
B. Eksperimen hasil PS1.
![Screenshot 2024-09-26 220834](https://github.com/user-attachments/assets/d3856320-c795-4c91-95b2-35522cfba601)
3. Logout
Edit file .bash_logout, tampilkan pesan dan tahan selama 5 detik, sebelum eksekusi logout
Echo “Terima kasih atas sesi yang diberikan”
Sleep 5
clear
![Screenshot 2024-09-26 222046](https://github.com/user-attachments/assets/0d79f187-8ba2-450b-980f-9aaddd6a904b)
4. Bash Script
Buat 3 buah script (p1.sh, p2.sh, p3.sh) dengan isi masing-masing:
p1.sh
#! /bin/bash
echo “Program p1”
ls –l
p2.sh
#! /bin/bash
echo “Program p2”
who
p3.sh
#! /bin/bash
echo “Program p3”
ps x
![Screenshot 2024-09-26 222941](https://github.com/user-attachments/assets/9966ff4e-c41a-4ed3-bad4-48493b083678)
![Screenshot 2024-09-26 223009](https://github.com/user-attachments/assets/181f866d-eaa4-4716-83cb-67779c14d76a)
![Screenshot 2024-09-26 223024](https://github.com/user-attachments/assets/c0b88df2-e8f8-4f8f-993b-60b240c46d62)
![Screenshot 2024-09-26 223031](https://github.com/user-attachments/assets/e5a7b622-5cf4-49bd-bcb8-2bf1332129be)
b. Jalankan script tersebut sebagai berikut :
$ ./p1.sh ; ./p3.sh ; ./p2.sh
$ ./p1.sh &
$ ./p1.sh $ ./p2.sh & ./p3.sh &
$ ( ./p1.sh ; ./p3.sh ) &
![Screenshot 2024-09-26 223548](https://github.com/user-attachments/assets/625f5484-e1c8-47a0-b017-0468c890aeae)
![Screenshot 2024-09-26 223619](https://github.com/user-attachments/assets/60e94764-dde6-4886-9ee6-da76379f2e7f)
![Screenshot 2024-09-26 223659](https://github.com/user-attachments/assets/f357db13-fb79-4767-850a-de4500d234f9)
![Screenshot 2024-09-26 224626](https://github.com/user-attachments/assets/d8cc552b-3da3-438b-baf8-c524389e91de)
![Screenshot 2024-09-26 224737](https://github.com/user-attachments/assets/7755b689-6abf-4ece-9004-58c840db1584)
![Screenshot 2024-09-26 224819](https://github.com/user-attachments/assets/0914dbdd-6966-4811-a36a-64e70d5e56d7)
![Screenshot 2024-09-26 224931](https://github.com/user-attachments/assets/00613322-c712-4ade-a11c-aebbc3c4fc4c)
5. Jobs
Buat sebuah script looping melakukan loop dengan nama pwaktu.sh.
Setiap 10 detik, kemudian menyimpan tanggal dan jam pada file hasil:
![Screenshot 2024-09-26 225527](https://github.com/user-attachments/assets/4be389d7-89c2-4661-b427-9b7237f746db)
![Screenshot 2024-09-26 225536](https://github.com/user-attachments/assets/39e254a2-941c-4600-8e6c-d4a4e3699ee1)
b. Jalankan sebagai background; kemudian jalankan satu program (utilitas find) di background sebagai berikut :
$ jobs
$ find / -print > files 2>/dev/null &
$ jobs
![Screenshot 2024-09-26 230255](https://github.com/user-attachments/assets/a71c3dea-da5d-4b65-a3a0-72a7fa14ffee)
c. Jadikan program ke 1 sebagai foreground, tekan ^Z dan kembalikan program tersebut ke background
$ fg %1
$ b
![Screenshot 2024-09-26 230651](https://github.com/user-attachments/assets/ff04a8c7-9b79-4b5e-bd0e-6e91a15a1f90)
d. Stop program background dengan utilitas kil
$ ps x
$ kill [Nomor PID]
![Screenshot 2024-09-26 231214](https://github.com/user-attachments/assets/f9af7ef8-5435-4a6b-b100-554be9d7e6ed)
![Screenshot 2024-09-26 231237](https://github.com/user-attachments/assets/699beadf-a3fc-4afd-a34f-3c8f89330f29)
![Screenshot 2024-09-26 231254](https://github.com/user-attachments/assets/7f3480bb-0666-4b58-8547-fccdc405ecc2)
6. History a. Ganti nilai HISTSIZE dari 1000 menjadi 20
$ HISTSIZE=20
$ h
![Screenshot 2024-09-26 231610](https://github.com/user-attachments/assets/ec69cf07-0a8c-4b0c-b128-801523bfc6e4)
b. Gunakan fasilitas history dengan mengedit instruksi baris ke 5 dari instruksi yang terakhir dilakukan
$ !-5
![Screenshot 2024-09-26 231823](https://github.com/user-attachments/assets/82e5c11d-265b-4649-8359-49ecf4691227)
c. Ulangi instruksi yang terakhir. Gunakan juga ^P dan ^N untuk bernavigasi pada history bufer
$ !!
![Screenshot 2024-09-26 232021](https://github.com/user-attachments/assets/4e00f4e4-bb7c-466d-ba78-ee8995353291)
d. Ulangi instruksi pada history bufer nomor 150
$ !150
![Screenshot 2024-09-26 232314](https://github.com/user-attachments/assets/ac4f00cc-a2bc-4c9e-9742-b2c00cd45967)
e. Ulangi instruksi dengan prefix “ls”
$ !ls
![Screenshot 2024-09-26 232807](https://github.com/user-attachments/assets/0ee2fd6f-bc69-4dca-9033-ce4b2a3b3727)

