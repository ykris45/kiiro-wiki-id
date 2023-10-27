how to upgrade collateral to your masternode

if u lost or dont remember all datas used for previous masternode, login to your vps, then type evoznode status, will get something like this, so save all infos!

 kiirocoin-cli evoznode status
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

the secret key is in kiirocoin.conf file always on vps



once saved do as follow:
go to your wallet and create new collateral address
sent there exactly 2500 coins
after 1 confirmation save trx id
create new fee address and send there 0.5 coin
wait for 1 confirmation
then
evoznode outputs
and grab trxid and index outputs

replace your datas to final imput

protx register collateralHash collateralIndex ipAndPort ownerAddress operatorPubKey votingAddress 0 payoutAddress feeSourceAddress