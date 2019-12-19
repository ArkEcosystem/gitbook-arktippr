---
description: How to setup and structure the configuration file for your tipbot
---

# The Configuration File

### Overview

Setup your JSON configuration containing the following elements:

#### Server

Each of your listener servers will be identified by a public key, generated from a BIP39 seed. Each of your servers needs to be able to uniquely identify itself in order to claim and execute any of the commands your listener receives. 

```text
"server" : {
        "seed": "great squeeze swing air find seed siege flag bench hundred garlic culture"
},
```

{% hint style="info" %}
**Make sure each listener server has a unique seed or you risk multiple servers executing the same command.**
{% endhint %}

#### Database

Access credentials for your database

```text
"database": {
        "dbUser": "arktippr",
        "dbPassword": "your-secret-password",
        "host": "your-database-server",
        "database": "arktippr",
        "port": 5432
},
```

#### Secure Storage

All your user's wallets are securly encrypted in the database. The key for this encryption needs to be 32 characters. 

```text
"secureStorage": {
      "encryptionKey": "32CharactersKey"
},
```

{% hint style="info" %}
**Do NOT loose this key**, all your user's funds will be lost with the key. In case this key and your database are both compromised your user's funds can be moved by the attacker.
{% endhint %}

#### Currency

Your accepted and default currencies. The baseCurrency setting defines your default currency. Each of the accepted currencies can be parsed and converted to your base currency. 

```text
"currency": {
      "baseCurrency": "ark",
      "acceptedCurrencies": ["ARK", "Ѧ", "USD", "$", "EUR", "€", "BTC", "BCH", "GBP"]
},
```

{% hint style="info" %}
Your base currency needs to be an ARK Ecosystem token known by CoinGecko. In case you want to launch a tipbot for your own bridgechain and your token is not \(yet\) added to CoinGecko you should use ARK as a base currency and add your token to the `arkEcosystem` settings \(see below\).
{% endhint %}

#### Parser

Configure what seperator to use for cross platform transactions. The seperator is used to seperate the username from the platform name e.g. `username@platform` where `@` is the seperator.

```text
"parser": {
    "seperator": "@"
},
```

#### ARK Ecosystem

Configure the ARK Ecosystem your tipbot should be able to process. Create an entry for each of the ARK \(bridge\)chains you want to include.

the `minValue` \(_minimum accepted tip value_\) and `transactionFee` \(_fee for each of the transactions_\) are in _ARKTOSHI._

You can add an array of nodes per token to where your transactions will be sent. In case a bridgechain uses a different EPOCH and is running on an older version of ARK Core, you can add the `epoch` to the configuration.

```text
"arkEcosystem": {
      "ark": {
          "networkVersion": 23,
          "minValue": 20000000,
          "transactionFee": 800000,
          "nodes": [
              {
              "host": "localhost",
              "port": 4003
              }
          ],
          "explorer": "https://explorer.ark.io"
      },

      "xqr": {
          "networkVersion": 58,
          "minValue": 20000000,
          "transactionFee": 1300000,
          "nodes": [{
              "host": "159.69.89.111",
              "port": 4103
          },
          {
              "host": "116.203.58.165",
              "port": 4103
          }],
          "explorer": "https://explorer.qredit.io/#",
          "epoch":"2017-03-21T13:00:00.000Z"
      },
      
      "dark": {
          "networkVersion": 30,
          "minValue": 2000000,
          "transactionFee": 300,
          "nodes": [{
              "host": "devnet.server",
              "port": 4003
          }],
          "explorer": "https://dexplorer.ark.io"
      }
  },
```

#### Platforms

Configure the listeners for each of the accepted platforms \(_currently Twitter and Reddit_\).

```text
"platforms" : {
    "reddit": {
        "admin":"adminAccountUsername",
        "clientId":"Reddit-client-id",
        "clientSecret":"Reddit-client-secret",
        "username":"tipbotAccountUsername",
        "password":"tipbotAccountPassword",
        "usernamePrefix": "u/"
    },
        
    "twitter": {
        "admin":"adminAccountUsername",
        "userId": "tipbotAccountUsername",
        "usernamePrefix": "@",
        "serverUrl": "https://your-webhook-server",
        "route": "/webhooks",
        "consumerKey": "Twitter-app-consumerKey",
        "consumerSecret": "Twitter-app-consumerSecret",
        "accessToken": "Twitter-accessToken",
        "accessTokenSecret": "Twitter-accessTokenSecret",
        "environment": "Twitter-webhook-environment",
        "accountApiPort": port-to-listen-for-events
    }
},
```

#### On-Chain API Listener

If you plan to run an on-chain API listener configure both `apiServer` and `apiFees`. The fees for registration and commands are in ARKTOSHI. 

```text
"apiServer": {
        "port":4467,
        "url":"http://127.0.0.1:4467/",
        "node":"http://127.0.0.1:4004",
        "seed":"a valid BIP39 seed for the wallet that receives the on-chain requests"
},

"apiFees": {
        "registration":2500000000,
        "command":1000
},
```

