<h2 id="getting-started">Memulai</h2>

<p>Baik Anda memakai layanan dengan penyedia masternode atau melakukannya sendiri, pastikan Anda memiliki <a href="https://github.com/Kiirocoin/kiiro/tree/main/" target="_blank" terbaru >Dompet Kiiro</a> dan Anda telah mendapatkan <strong>2500 KIIRO</strong> (sebaiknya sedikit lebih untuk menutupi biaya saat Anda melakukan transfer). <strong>Langkah 1 dan 2 masih diperlukan</strong> meskipun Anda menggunakan penyedia masternode.</p>



<h3 id="step-1-encrypt-and-backup-your-wallet-on-your-desktop-wallet">Langkah 1: Enkripsi dan Cadangkan dompet Anda di dompet Desktop Anda</h3>



<p>Jika Anda belum melakukannya, pastikan Anda mengenkripsi dompet Anda di <strong>dompet desktop lokal</strong> (PC/Mac/Linux).</p>



<p>Buka <strong>Pengaturan &gt; Enkripsi Dompet.</strong></p>


<p>Setelah Anda mengenkripsi dompet Anda, disarankan juga untuk melakukan pencadangan melalui <strong>File &gt; Dompet Cadangan</strong>. Disarankan untuk menyimpan dompet ini di drive fisik atau pen drive terpisah. Wallet.dat dienkripsi sehingga meskipun wallet.dat terekspos, sandi Anda cukup panjang akan aman.</p>



<p><strong>Harap jangan lupa kata sandi Anda! Tidak ada yang bisa membantu Anda jika Anda kehilangan sandi.</strong></p>



<h3 id="step-2-collateral-your-2500-kiiro-on-your-desktop-wallet">Langkah 2: jaminankan 2500 KIIRO Anda di dompet Desktop Anda</h3>



<p>Alamat jaminan Anda adalah tempat Anda menyimpan 2500 KIIRO Anda.</p>



<p>Anda dapat membuat alamat jaminan dengan dua cara: menggunakan tab Terima, ATAU di Jendela Debug</p>



<h4 id="receive-tab">Tab terima:</h4>



<p>Klik pada tab Terima. Masukkan label untuk alamat agunan Anda di bidang Label dan klik Minta Pembayaran. Sebuah jendela akan muncul dengan alamat Kiiro.</p>



<h4 id="debug-window">Jendela Debug:</h4>



<p>Buka Bantuan &gt; Jendela Debug &gt; Konsol dan ketik</p>



<p><code class="language-plaintext highlighter-rouge">getnewaddress</code></p>



<p>Dalam satu transaksi, kirim <strong>tepatnya 2500 KIIRO</strong> ke alamat jaminan masternode yang Anda buat. Jangan kirim 500 lalu kirim 500 lagi. <strong>Harus dalam satu transaksi. Jangan centang kurangi biaya dari jumlah.</strong></p>


<p>Tidak disarankan untuk mengirimkannya langsung dari bursa karena mereka mungkin mengurangi biaya penarikan tertentu yang mengakibatkan kurang dari 2500 KIIRO dalam transfer tersebut.</p>



<p>Tunggu <strong>1 konfirmasi</strong> agar transaksi ini valid sebagai jaminan masternode Anda. Jika dilakukan dengan benar, id transaksi dan indeks transaksi akan muncul saat Anda menjalankan perintah ini di Konsol Debug:</p>



<p><code class="language-plaintext highlighter-rouge">evoznode outputs</code></p>



<h4 id="special-notes-only-for-those-who-are-creating-more-than-one-masternode">Catatan Khusus hanya untuk mereka yang membuat lebih dari satu masternode:</h4>



<p>Jika Anda mengerjakan lebih dari satu masternode, perhatian khusus diperlukan untuk memastikan bahwa Anda membuat jaminan dengan benar. Anda tidak ingin merusak agunan 2500 KIIRO yang baru saja Anda buat dengan mengambil dana dari agunan tersebut.</p>



<p>Untuk melakukannya, di <strong>dompet desktop lokal</strong> Anda, aktifkan kontrol koin dengan membuka <strong>Setelan &gt; Pilihan &gt; Dompet</strong> dan klik <strong>Aktifkan fitur kontrol koin.</strong> Ini akan memungkinkan kontrol atas dana yang Anda gunakan saat membuat jaminan 2500 KIIRO berikutnya.</p>







<p>Kemudian buka tab Kirim, dan Anda akan melihat <strong>Fitur Kontrol Koin</strong>. Klik pada <strong>Masukan</strong>. Anda akan melihat jaminan 2500 KIIRO Anda di sana. Klik kanan dan klik <strong>Kunci Belum Dipakai</strong>. Artinya, saat Anda membuat jaminan baru, dompet Anda tidak akan menyentuh dana tersebut.</p>







<p>Setelah Anda melakukan ini, Anda dapat membuat jaminan 2500 KIIRO berikutnya untuk masternode Anda berikutnya. Ulangi ini setiap kali Anda membuat masternode baru.</p>



<p>Anda selalu dapat memverifikasi bahwa Anda melakukan ini dengan benar dengan membuka <strong>Bantuan &gt; Debug Window</strong> dan ketik <strong>evoznode outputs</strong> yang akan menampilkan semua jaminan yang mendukung masternode.</p>



<h3 id="step-3-creating-owneraddress-payoutaddress-feesourceaddress-and-operatorkeyoperatorpubkey">Langkah 3: Membuat ownerAddress, payoutAddress, feeSourceAddress, dan operatorKey/operatorPubKey</h3>



<p><em>a, b, dan c dapat dihasilkan melalui tab Terima atau Jendela Debug, seperti alamat jaminan di atas.</em></p>



<h4 id="a-owneraddress">a. alamat pemilik</h4>



<p>Bukti bahwa Anda pemilik masternode. Harus berada di dompet yang sama dengan jaminan. <strong>JANGAN GUNAKAN ALAMAT JAMINAN SEBAGAI ALAMAT PEMILIK.</strong></p>



<p><strong>JANGAN KIRIM KOIN KE ALAMAT PEMILIK. JANGAN GUNAKAN INI SEBAGAI ALAMAT PEMBAYARAN. JANGAN GUNAKAN ALAMAT INI UNTUK TUJUAN LAINNYA.</strong></p>



<h4 id="b-alamat pembayaran">b. alamat pembayaran</h4>



<p>Alamat tujuan pembayaran masternode. Bisa di dalam dompet yang sama atau alamat eksternal.</p>



<h4 id="c-feesourceaddress">c. feeSourceAddress</h4>



<p>Alamat dengan dana untuk membayar biaya transaksi untuk mendaftarkan masternode Anda. Untuk mendapatkan daftar alamat dengan dana, masukkan perintah berikut di Jendela Debug:</p>



<p><code class="lingual-plaintext highlighter-rouge">listaddressbalances 0,01</code></p>



<p>Jika Anda tidak memilikinya, Anda dapat membuat alamat dan mengirim beberapa Kiiro ke sana. Anda kemudian dapat menggunakan alamat tersebut sebagai feeSourceAddress.</p>



<h4 id="d-operatorkeyoperatorpubkey">d. operatorKey/operatorPubKey</h4>



<p>Di Konsol Debug, masukkan bls generate. Outputnya akan seperti ini:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>{

    "secret": "2e551176c4cd5a2e26f3a1c61f151487e013f7095ffbc0f62b5c2b251e7bd84c",

    "public": "89d395bc75e99527e80d3bbd408a5b41bbf37e7e1e26c5924da734008d1aa4a3f5e42a968bef541cb1c9a0899280d29b"

}

</code></pre></div></div>



<p><strong>rahasia</strong>: Ini adalah operatorKey Anda (untuk protx) dan juga znodeblsprivkey untuk digunakan pada Langkah 6.</p>



<p><strong>publik</strong>: Ini adalah operatorPubKey Anda (untuk protx)</p>



<p>Anda tidak dapat <strong>membuat ulang pasangan kunci yang sama,</strong> namun Anda dapat membuat kunci publik dari kunci rahasia jika Anda kehilangan kunci publik.</p>



<h3 id="step-4-get-a-vps">Langkah 4: Dapatkan VPS</h3>



<p>Ada banyak penyedia yang dapat dipilih.</p>





<p> <a href="https://hetzner.cloud/?ref=mPIIBRuHJtB4" target="_blank">Hetzner "mulai dari 4,2 euro"</a></p>

<p> <a href="https://www.vpsag.com/?aff=36435" target="_blank">Vpsag "mulai dari 3,66euro"</a></b>

<p> <a href="https://panel.dedimax.com/register/28273" target="_blank">Dedimax "mulai dari 3,9euro"</a></b>

<p> <a href="https://www.mvps.net/?aff=37549" target="_blank">Mvps.net "mulai dari 4,88 euro"</a></b>





<p>Pilih paket VPS yang memenuhi persyaratan minimum:</p>



<ul>

   <li>RAM 1,5 GB (direkomendasikan 2 GB dengan swap aktif)</li>

   <li>Ruang disk 25 GB </li>

</ul>



<p><strong>Catatan:</strong> Dengan KiiroPoW, blockchain tumbuh dengan kecepatan sekitar 1 GB per tahun. Pastikan Anda memilih VPS dengan ruang disk yang memadai.</p>



<p>Saat memilih server, harap diingat keandalan lebih penting daripada harga. Jika masternode Anda offline, Anda berpotensi kehilangan pembayaran yang melebihi biaya VPS Anda.</p>



<p>Pilih <strong>Ubuntu 20.04 64-bit</strong> dan instal.</p>



<p>Setelah selesai, penyedia VPS akan memberi Anda nama pengguna (biasanya root) dan kata sandi. Gunakan klien SSH seperti <a href="https://www.putty.org/">Putty</a> atau jika penyedia VPS menyediakannya, jendela konsol akan terbuka.</p>



<h3 id="step-5-configuring-your-vps">Langkah 5: Mengonfigurasi VPS Anda</h3>



<h4 id="creating-a-new-user">Creating a New User</h4>



<p>Selalu merupakan praktik yang baik untuk membuat pengguna baru untuk menjalankan masternode sehingga aplikasi masternode tidak berjalan dengan akses root.</p>



<p>Pada <strong>VPS</strong> yang baru Anda buat, Masuklah <strong>sebagai root.</strong></p>



<p>Buat pengguna baru dengan perintah berikut, ganti <username> dengan nama pengguna pilihan Anda.</username></p>



<p><code class="language-plaintext highlighter-rouge">adduser &lt;username&gt;</code></p>



<p>Anda akan dimintai kata sandi. Masukkan dan konfirmasi menggunakan kata sandi baru (berbeda dengan kata sandi root Anda) dan simpan di tempat yang aman.</p>



<p>Anda juga akan melihat permintaan informasi pengguna, namun dapat dikosongkan.</p>



<p>Setelah pengguna dibuat, kami akan menambahkannya ke grup sudo sehingga mereka dapat menjalankan perintah sebagai root. Hanya perintah/aplikasi yang dijalankan dengan sudo yang akan dijalankan dengan hak akses root, sementara yang lain akan dijalankan dengan hak istimewa reguler</p>



<p><code class="language-plaintext highlighter-rouge">usermod -aG sudo &lt;username&gt;</code></p>



<p>Sekarang, saat masih sebagai root, kami akan memperbarui sistem dari repositori paket Ubuntu.</p>



<p><code class="language-plaintext highlighter-rouge">apt update</code></p>



<p><code class="language-plaintext highlighter-rouge">apt upgrade</code></p>



<h4 id="installing-a-firewall">Memasang Firewall</h4>



<p>Kami memasang <strong>UFW</strong> (firewall sederhana) untuk lebih mengamankan server VPS Anda. Ini opsional tetapi sangat disarankan.</p>



<p>Saat masih dalam pengguna root di VPS Anda (atau alternatifnya, Anda dapat sudo dalam pengguna yang baru Anda buat).</p>



<p><code class="language-plaintext highlighter-rouge">apt install ufw</code></p>



<p>(tekan Y dan Enter untuk mengonfirmasi)</p>



<p>Langkah selanjutnya membuka port 8999 yang diperlukan masternode Anda untuk berkomunikasi.</p>



<p><code class="language-plaintext highlighter-rouge">ufw allow ssh/tcp</code></p>



<p><code class="language-plaintext highlighter-rouge">ufw limit ssh/tcp</code></p>



<p><code class="language-plaintext highlighter-rouge">ufw allow 8999/tcp</code></p>



<p><code class="language-plaintext highlighter-rouge">ufw logging on</code></p>



<p><code class="language-plaintext highlighter-rouge">ufw enable</code></p>



<p>(tekan Y dan Enter untuk mengonfirmasi) Anda sekarang memiliki pengaturan firewall!</p>



<h4 id="allocating-a-swap-file">Mengalokasikan File Swap</h4>



<p><em>Anda dapat melewati langkah ini jika penyedia VPS Anda secara otomatis mengalokasikan swap untuk Anda. Gunakan perintah <strong>gratis</strong> untuk memeriksa apakah ada pertukaran.</em></p>


<p><code class="language-plaintext highlighter-rouge">fallocate -l 4G /swapfile</code></p>



<p><code class="language-plaintext highlighter-rouge">chmod 600 /swapfile</code></p>



<p><code class="language-plaintext highlighter-rouge">mkswap /swapfile</code></p>



<p><code class="language-plaintext highlighter-rouge">swapon /swapfile</code></p>



<p><code class="language-plaintext highlighter-rouge">nano /etc/fstab</code></p>



<p>Tambahkan baris berikut di akhir file (tekan tab untuk memisahkan setiap kata/angka</p>



<p><code class="language-plaintext highlighter-rouge">/swapfile none swap sw 0 0</code></p>


<p>lalu tekan Ctrl + X untuk menutup editor, lalu Y dan Enter untuk menyimpan file. Kemudian reboot server.</p>



<p><code class="language-plaintext highlighter-rouge">reboot now</code></p>



<p>VPS Anda sekarang siap dioperasikan.</p>



<h3 id="step-6-installing-kiiro-in-your-vps">Langkah 6: Menginstal Kiiro di VPS Anda</h3>



<p>Setelah <strong>masuk ke pengguna baru</strong> di <strong>VPS</strong> yang Anda buat pada Langkah 5, ketikkan perintah berikut untuk <strong>mengunduh paket Kiiro Linux terbaru</strong>. </p>



<p><code class="bahasa-plaintext highlighter-rouge">cd ~</code></p>


<p><code class="language-plaintext highlighter-rouge">wget https://github.com/Kiirocoin/kiiro/releases/download/v1.0.0.4/kiirocoin-1.0.0.4-linux-20.04.zip</code></p>

<p><code>apt install unzip  </code>
<p><code>cd root </code></p>
<p><code>unzip kiirocoin-1.0.0.4-linux-20.04.zip</code></p>
<p><code>cd kiirocoin-1.0.0.4-linux-20.04.zip</code></p>
<p><code>sudo mv kiirocoind /usr/bin</code></p>
<p><code>sudo mv kiirocoin-cli /usr/bin</code></p>
<p><code>sudo cd /usr/bin </code></p>
<p><code>chmod +x kiirocoin-cli</code></p>
<p><code>chmod +x kiirocoind</code></p>
<p><code>back to root typing cd</code></p>



<p>Buat file konfigurasi baru untuk masternode Anda. Ketik</p>


<p><code class="lingual-plaintext highlighter-rouge">mkdir .kiirocoin</code></p>



<p><code class="lingual-plaintext highlighter-rouge">nano /.kiirocoin/kiirocoin.conf</code></p>



<p>Ini akan membuat direktori baru dan juga membuka file teks baru bernama kiirocoin.conf di editor teks bernama nano.</p>



<p>Dalam file baru tersebut, ketikkan perintah berikut dan <strong>ubah bagian yang menggunakan huruf kapital</strong> agar sesuai dengan detail Anda yang sebenarnya. Nama pengguna dan sandi rpc bisa apa saja yang Anda inginkan (usahakan membuatnya sedikit lebih panjang).</p>


<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>#----

<p style="color: yellow;">
		   rpcuser=ANYUSERNAME<br>
		   rpcpassword=ANYPASSWORD<br>
		   rpcallowip=127.0.0.1<br>
		   #----<br>
		   listen=1<br>
		   server=1<br>
		   daemon=1<br>
		   logtimestamps=1<br>
		   txindex=1<br>
		   #----<br>
		   znode=1<br>
		   externalip=YOUR MASTERNODE IP:8999<br>
		   znodeblsprivkey=YOUR SECRET OUTPUT FROM STEP 3 HERE
		</p>


</code></pre></div></div>



<p>Tekan <strong>Ctrl-X</strong> untuk menyimpan dan tekan <strong>Y</strong> untuk mengonfirmasinya.</p>



<p>Ketik perintah berikut untuk memulai daemon kiirod Anda dan biarkan disinkronkan. Ini akan memakan waktu beberapa jam.</p>



<p><code class="bahasa-plaintext highlighter-rouge">cd root </code></p>
<p><code class="lingual-plaintext highlighter-rouge">kiirocoind -daemon</code></p>







<p>Anda selalu dapat memeriksa status sinkronisasi dengan mengetik</p>



<p><code class="lingual-plaintext highlighter-rouge">kiirocoin-cli getinfo</code></p>





<h3 id="step-7-registering-your-masternode">Langkah 7: Mendaftarkan masternode Anda</h3>



<p><em><strong>Proses pendaftaran harus dilakukan di dompet lokal Anda, bukan di VPS/masternode Anda</strong></em></p>



<p>Setelah Anda melakukan semua hal di atas, kini Anda dapat mendaftarkan masternode Anda dengan perintah berikut:</p>



<p><code class="lingual-plaintext highlighter-rouge">protx register collateralHash collateralIndex ipAndPort ownerAddress operatorPubKey votingAddress operatorReward payoutAddress feeSourceAddress</code></p>



<p>di mana</p>


<div class="lingual-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>collateralHash: ID transaksi jaminan 1000 KIIRO Anda (dari "output evoznode")

collateralIndex: indeks transaksi agunan 2500 KIIRO Anda (dari "output evoznode")

ipAndPort: alamat IP dan port masternode Anda

ownerAddress: ownerAddress, dihasilkan pada Langkah 3

operatorPubKey: bagian "publik" dari keluaran "bls generate", yang dihasilkan pada Langkah 3

votingAddress: "" (default pada ownerAddress)

operatorHadiah: 0

payoutAddress: Alamat Kiiro yang valid untuk pembayaran masternode Anda, dihasilkan pada Langkah 3

feeSourceAddress: Alamat Kiiro yang valid dengan dana di dalamnya untuk mendanai pendaftaran masternode, dari Langkah 3
</code></pre></div></div>



<p>Before you are able to enter the command, you must first unlock your wallet:</p>



<p><code class="language-plaintext highlighter-rouge">walletpassphrase YOURPASSWORD 60</code></p>



<p>This command will unlock your wallet for 60 seconds and returns a (null) message when successfully executed.</p>



<p>If everything is correct, you should get a transaction ID.</p>



<h4 id="example"><strong>Example</strong></h4>



<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>protx register 4950f88867b69760d3cd7c1f53531340f6723eb8f7d7f00730abfa12c5fe10e0 0 207.148.122.12:8999 KRVDAxJwaZYFfmti4aTeKCByz1jbMq8Jy4 995b3e1e2a65ce960a8cc7d305c5914b7f60e888c338c1f3317efbdcac58e82ecc110315ce03f49d9d387ff35c2796ad "" 0 KEZ8M8Fgp8h4HvUjXtjz3krYraRtySiXdw KQGmCxUQHK2xKGYNyeqGdSYQqfEAB2hjtd` 

</code></pre></div></div>



<p>Details:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>collateralHash: 4950f88867b69760d3cd7c1f53531340f6723eb8f7d7f00730abfa12c5fe10e0 

collateralIndex: 0 

ipAndPort: 207.148.122.12:8999 

ownerAddress: KRVDAxJwaZYFfmti4aTeKCByz1jbMq8Jy4 

operatorPubKey: 995b3e1e2a65ce960a8cc7d305c5914b7f60e888c338c1f3317efbdcac58e82ecc110315ce03f49d9d387ff35c2796ad 

votingAddress: "" 

operatorReward: 0 

payoutAddress: KEZ8M8Fgp8h4HvUjXtjz3krYraRtySiXdw 

feeSourceAddress: KQGmCxUQHK2xKGYNyeqGdSYQqfEAB2hjtd

</code></pre></div></div>



<p>Pendaftaran berhasil setelah transaksi yang berisi pendaftaran Anda berhasil ditambang dan dimasukkan dalam blok.</p>



<p>Setelah transaksi ditambang, node yang baru saja Anda daftarkan akan muncul di tab masternode di dompet.</p>



<p><strong>Jangan lewati langkah ini.</strong> Untuk memeriksa status masternode Anda di masternode itu sendiri, lakukan <strong>kiirocoin-cli evoznode status</strong>. Jika semuanya telah diatur dengan benar, Anda akan melihat detail masternode Anda bersama dengan dua baris berikut di bagian bawah:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>"state": "READY", 

"status": "Ready"

</code></pre></div></div>



<h3 id="unbanning-your-masternode">Membatalkan pemblokiran masternode Anda</h3>



<p><em><strong>Proses pembatalan pemblokiran harus dilakukan di dompet lokal Anda, bukan di VPS/masternode Anda</strong></em></p>



<p>Masternode Anda diblokir jika berstatus <strong>POSE_BANNED</strong>. Anda dapat membatalkan pemblokiran masternode Anda dengan memasukkan perintah ini di Konsol Debug dompet lokal Anda:

<code class="lingual-plaintext highlighter-rouge">protx update_service proTxHash ipAndPort operatorKey operatorPayoutAddress feeSourceAddress</code></p>



<p>Detail:</p>

<div class="lingual-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>proTxHash: proTxHash dari masternode Anda. Di tab Masternodes di dompet lokal Anda, klik kanan pada node yang dilarang dan pilih 'Salin hash Protx'

ipAndPort: ipAndPort dari masternode yang dilarang

operatorKey: znodeblsprivkey dari masternode, biasanya di dalam kiirocoin.conf pada masternode. Ini berbeda dengan operatorPubKey!

operatorPayoutAddress: "" , jika Anda menyetel operatorReward ke 0 saat pendaftaran

feeSourceAddress: alamat di dompet lokal yang memiliki KIIRO untuk mendanai transaksi. Dapat diperoleh dengan perintah listaddressbalances

</code></pre></div></div>



<p>Pastikan Anda telah memperbaiki masalah yang menyebabkan pelarangan sebelum membatalkan pelarangan masternode Anda, jika tidak maka masternode akan diblokir lagi.</p>



<p>Setelah membatalkan pemblokiran, pastikan Anda memeriksa status masternode di dompet dan masternode itu sendiri.</p>


<h3 id="additional-tips">Tips tambahan</h3>


<p>Tips berikut tidak tercakup dalam panduan ini tetapi dapat memastikan kelancaran masternode Anda.</p>

<ul>

   <li>Pastikan masternode Anda dimulai secara otomatis setelah reboot VPS</li>

   <li>Atur Ubuntu untuk mengunduh dan menginstal pemutakhiran baru secara otomatis</li>

   <li>Amankan lebih lanjut masternode Anda dengan memodifikasi file konfigurasi SSH dan/atau menginstal dan mengkonfigurasi fail2ban</li>

   <li>Cegah debug.log menjadi terlalu besar dengan memutarnya</a></li>

</ul>
