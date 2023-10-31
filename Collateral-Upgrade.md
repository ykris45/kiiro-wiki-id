# Cara Meningkatkan Jaminan

### Di VPS Masternode (MN) Milik Anda

1. Jalankan:  
```
kiirocoin-cli evoznode status
```

2. Salinlah kode berikut ini pada bagian output untuk dapat digunakan saat mendaftarkan MN Anda dengan jumlah jaminan yang baru
```json
{
  "outpoint": "COutPoint(f4deca21e0042d5a635a76020a71ace6b2887020d709d876d878108270xxxxxx, 0)",
  "service": "159.69.15.xxx:8999",
  "proTxHash": "xxxxxx6b9edacea9bf5ee9af2070a46e438e9b263d02b245f9e80e7732da6ca4",
  "collateralHash": "xxxxxx21e0042d5a635a76020a71ace6b2887020d709d876d87810827020e2dd",
  "collateralIndex": 0,
  "dmnState": {
    "service": "159.69.15.xxx:8999",
    "registeredHeight": 1622,
    "lastPaidHeight": 56213,
    "PoSePenalty": 0,
    "PoSeRevivedHeight": -1,
    "PoSeBanHeight": -1,
    "revocationReason": 0,
    "ownerAddress": "KFAr1jJnnZQSt7HfFUS4SVumd8ACP7Uxxx",
    "votingAddress": "KFAr1jJnnZQSt7HfFUS4SVumd8ACP7Uxxx",
    "payoutAddress": "KBhVyPWQUK4V3iAc7vSYULEyEoaZdxSxxx",
    "pubKeyOperator": "93c31c537cec347f596f4570058a897bd0e01b0046b4b717627d48e523d01a5b50cb4aae4c93008e0e90707f8exxxxx"
  },
  "state": "READY",
  "status": "Ready"
}
```
3. Jalankan: 
```
sudo systemctl stop kiirocoind.service
```

### Pada Dompet Kiirocoin Core milik Anda

1. Dari bagian tab **Receive**, berilah label sebagai berikut ini **MN1 Collateral 2500** sertakan jumlah sebesar 2500, lalu klik **Request Payment**

![image](https://github.com/Kiirocoin/kiiro/assets/146014363/90edf2de-6942-4639-9b6f-430ead647cf2)

2. Dari jendela berikut klik **Copy Address**

![image](https://github.com/Kiirocoin/kiiro/assets/146014363/b1f05bb0-e2f4-46b1-bc88-bcacd99f0c01)

3. Pergi ke tab **Send** dan Klik **Inputs**

![image](https://github.com/Kiirocoin/kiiro/assets/146014363/bb6b8138-323a-4c0c-820e-00a24242a0d5)

4. Klik kanan mouse pada jaminan lama dan pilih **Unlock unspent**

![image](https://github.com/Kiirocoin/kiiro/assets/146014363/a0a475fb-8717-4bb7-92d0-d06abdc40091)

5. Pilih input yang cukup untuk menghasilkan 2500 KIIRO

6. Masukkan alamat yang disalin dari langkah 2 dan 2500 dalam jumlah (**_jangan centang biaya pengurangan dari jumlah_**), klik kirim

![image](https://github.com/Kiirocoin/kiiro/assets/146014363/241d1c37-a642-48a0-ac12-bc8b706ff1ce)

7. Dari tab **Masternodes** pastikan MN lama Anda tidak lagi terdaftar

8. Pastikan setidaknya 1 konfirmasi dari 2500 dikirimkan ke alamat jaminan baru Anda

9. Dari konsol debug, jalankan: `evoznode outputs`

10. Temukan transaksi untuk agunan 2500 Kiiro Anda dan catat indeksnya (0 atau 1)

11. Buat perintah protx
  * protx register collateralHash collateralIndex ipAndPort ownerAddress operatorPubKey votingAddress operatorReward payoutAddress feeSourceAddress
    * collateralHash and collateralIndex from step 10
    * ipAndPort from **service** copied json response on VPS
    * ownerAddress from **ownerAddress** copied json response on VPS
    * operatorPubKey from **pubKeyOperator** copied json response on VPS
    * votingAddress from **votingAddress** copied json response on VPS
    * operatorReward should be 0
    * payoutAddress from **payoutAddress** copied json response on VPS
    * feeSourceAddress can be and address you have with enough to cover the tx fee

12. Jalankan perintah di atas di konsol debug Anda (Perlu menjalankan `walletpassphrase your_wallet_passphrase 60` untuk membuka kunci)

13. Kembali ke VPS Milik Anda dan jalankan:
```
sudo systemctl start kiirocoind.servce
```
