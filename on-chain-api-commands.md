---
description: >-
  You can add your platform to ArkTippr and allow your users to send and receive
  ARK and accepted BridgeChain tokens to each other and all users other
  platforms.
---

# On-Chain API Commands

### Why On-Chain?

You will forward your users commands to ArkTippr via the ARK blockchain. On chain commands make it harder for 3rd parties to scam and spam.

### How to communicate with an On-Chain Listener

#### First register your platform

To be able to send commands you need to register an ARK wallet for your platform, you will send commands from this wallet to ArkTippr by using the VendorField.

Send ArkTippr `AcqtFLrackRcUbDdkkSZ2vSum7WqQ3W7A1` a transaction of 25 ARK \(_registration fee_\) with the following **JSON structure** in the VendorField:

`{“command”:”REGISTER”, “platform”:”yourplatformname”}`

Where _yourplatformname_ is a unique name in **lower caps alphanumerical** that describes your platform. Choose wisely as this will enable users on other platforms to send ARK to your users \(e.g. marc@ yourplatformname\). Certain names such as youtube, facebook, etc. are not allowed for obvious reasons.

ArkTippr will send your wallet a transaction with a reply in the VendorField:

`{“id”:”commandTransactionId”, “registered”:true/false, “error”:”error message if an error occurred”}`

Where _commandTransactionId_ is the ID of the transaction you sent to ArkTippr with your command.

**Once you have successfully registered your platform you can now send commands from your wallet to ArkTippr.**

#### Now send commands

You can send the following commands to ArkTippr:

* `SEND`: Transfer ARK or an accepted BridgeChain token to an other user.
* `DEPOSIT`: Get the deposit address for a user \(ARK or accepted token\).
* `WITHDRAW`: Transfer ARK or an accepted BridgeChain token to an other wallet.
* `BALANCE`: Request the balance of a user \(ARK or accepted token\).

Each command has to be send in the VendorField as a JSON object; only commands coming from your registered address will be executed. Send your command in the VendorField to `AcqtFLrackRcUbDdkkSZ2vSum7WqQ3W7A1` with a transaction value of 0.0005 ARK.

### SEND

To have one of your users send ARK or an accepted BridgeChain token to any of the other users send the following command:

```text
{“command”:”SEND”,”senderId”:”senderUsername”,”receiverId”:”receiverusername@platform”,”amount”:”amountAsString”,”token”:”ARK”}
```

**senderUsername** is the unique username of the user on your platform \(alphanumerical, lowercaps\)

* **receiverusername** is the unique username of the user on the target platform \(alphanumerical, lowercaps\), if you want to transfer to a user on a different platform you need to specify the **@platform** \(e.g. marcs1970@reddit or cryptologyhk@twitter\)
* **amountAsString** is a numerical string of the amount in token \(e.g. “1” or “1.25”\)
* **token** is one of the accepted currencies \(USD, EUR\) or tokens \(ARK, QXR\).

 ArkTippr will send your wallet a transaction with a reply in the VendorField:

```text
{“id”:”commandTransactionId”, “transactionId”:”transactionId”, “explorer“:”http://explorer.ark.io”,“error”:”error message if an error occurred”}
```

* **commandTransactionId** is the ID of the transaction you sent to ArkTippr with your command.
* **transactionId** is the ID of  the executed transfer on the ARK or BridgeChain blockchain.
* **explorer** is the URL of the blockchain explorer of ARK or BridgeChain.
* **error** contains an error message in case an error occurred.

{% hint style="info" %}
**Remember that you are sending the commands to ArkTippr for your users, there is currently no way for ArkTippr to verify that the command originates from your user so be responsible.**
{% endhint %}

### DEPOSIT

To request a deposit address \(ARK or an accepted BridgeChain\) for one of your users:

```text
{“command”:”DEPOSIT”,”senderId”:”senderUsername”, “token”:”ARK”}  
```

* **senderUsername** is the unique username of the user on your platform \(alphanumerical, lowercaps\)
* **token** is one of the accepted currencies \(USD, EUR\) or tokens \(ARK, QXR\).

 ArkTippr will send your wallet a transaction with a reply in the VendorField:

```text
{“id”:”commandTransactionId”, “address”:”address”, “error”:”error message if an error occurred”}
```

* **commandTransactionId** is the ID of the transaction you sent to ArkTippr with your command.
* a**ddress** is the ID of personal address for the user on the token blockchain.
* **error** contains an error message in case an error occurred.

### WITHDRAW

To have one of your users withdraw ARK or an accepted BridgeChain wallet:

```text
{“command”:”WITHDRAW”,”senderId”:”senderUsername”,”address”:”address”,”amount”:”amountAsString”,”token”:”ARK”}
```

* **senderUsername** is the unique username of the user on your platform \(alphanumerical, lowercaps\)
* a**ddress** is the address of the wallet where to withdraw into.
* **amountAsString** is a numerical string of the amount in token \(e.g. “1” or “1.25”\)
* **token** is one of the accepted currencies \(USD, EUR\) or tokens \(ARK, QXR\).

 ArkTippr will send your wallet a transaction with a reply in the VendorField:

```text
{“id”:”commandTransactionId”, “transactionId”:”transactionId”, “explorer“:”http://explorer.ark.io”,“error”:”error message if an error occurred”}
```

* **commandTransactionId** is the ID of the transaction you sent to ArkTippr with your command.
* **transactionId** is the ID of  the executed transfer on the ARK or BridgeChain blockchain.
* **explorer** is the URL of the blockchain explorer of ARK or BridgeChain.
* **error** contains an error message in case an error occurred.

{% hint style="info" %}
**Remember that you are sending the commands to ArkTippr for your users, there is currently no way for ArkTippr to verify that the command originates from your user so be responsible.**
{% endhint %}

### BALANCE

To request a deposit address \(ARK or an accepted BridgeChain\) for one of your users:

```text
{“command”:”BALANCE”,”senderId”:”senderUsername”, “token”:”ARK”}  
```

* **senderUsername** is the unique username of the user on your platform \(alphanumerical, lowercaps\)
* **token** is one of the accepted currencies \(USD, EUR\) or tokens \(ARK, QXR\).

 ArkTippr will send your wallet a transaction with a reply in the VendorField:

```text
{“id”:”commandTransactionId”, “balance”:”balanceAsString”, “error”:”error message if an error occurred”}
```

* **commandTransactionId** is the ID of the transaction you sent to ArkTippr with your command.
* **balance** is the balance in ArkToshi for the user on the token blockchain.
* **error** contains an error message in case an error occurred.

