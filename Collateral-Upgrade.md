# How to upgrade collateral

### On your Masternode (MN) VPS
1. Run:  
```
kiirocoin-cli evoznode status
```

2. Copy the output to be used when registering your MN with the new collateral amount
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
3. Run: 
```
sudo systemctl stop kiirocoind.service
```

### On your Kiirocoin Core Wallet

1. From the **Receive** tab, label it **MN1 Collateral 2500** and amount 2500, the click **Request Payment**

![image](https://github.com/Kiirocoin/kiiro/assets/146014363/90edf2de-6942-4639-9b6f-430ead647cf2)

2. From the following window click on **Copy Address**

![image](https://github.com/Kiirocoin/kiiro/assets/146014363/b1f05bb0-e2f4-46b1-bc88-bcacd99f0c01)

3. Go to the **Send** Tab and Click on **Inputs**

![image](https://github.com/Kiirocoin/kiiro/assets/146014363/bb6b8138-323a-4c0c-820e-00a24242a0d5)

4. Right mouse click on the old collateral and select **Unlock unspent**

![image](https://github.com/Kiirocoin/kiiro/assets/146014363/a0a475fb-8717-4bb7-92d0-d06abdc40091)

5. Select enough inputs to make up 2500 KIIRO

6. Enter in the address copied from step 2 and 2500 in the amount (**_do not check subtract fee from amount_**), click on send

![image](https://github.com/Kiirocoin/kiiro/assets/146014363/241d1c37-a642-48a0-ac12-bc8b706ff1ce)

7. From the **Masternodes** tab ensure your old MN is no longer listed

8. Ensure at least 1 confirmation from 2500 sent to your new collateral address

9. From the debug console run: `evoznode outputs`

10. Find the transaction for your 2500 Kirro collateral and take note of the index (0 or 1)

11. Create protx command
  * protx register collateralHash collateralIndex ipAndPort ownerAddress operatorPubKey votingAddress operatorReward payoutAddress feeSourceAddress
    * collateralHash and collateralIndex from step 10
    * ipAndPort from **service** copied json response on VPS
    * ownerAddress from **ownerAddress** copied json response on VPS
    * operatorPubKey from **pubKeyOperator** copied json response on VPS
    * votingAddress from **votingAddress** copied json response on VPS
    * operatorReward should be 0
    * payoutAddress from **payoutAddress** copied json response on VPS
    * feeSourceAddress can be and address you have with enough to cover the tx fee

12. Run the above command in your debug console (Will need to run `walletpassphrase your_wallet_passphrase 60` to unlock)

13. Go back to your VPS and run: 
```
sudo systemctl start kiirocoind.servce
```
