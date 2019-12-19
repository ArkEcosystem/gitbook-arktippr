---
description: >-
  Instructions and recommendations on how to setup a tipbot for an ARK Ecosystem
  blockchain.
---

# How to setup an ARK Pay Tip bot like ArkTippr?

### Overview

A tipbot consists of platform listener servers \(_interacting with the platforms such as reddit or Twitter_\) and a secure database cluster. Below you will find instructions and recommendations on how to setup your tipbot.

{% hint style="info" %}
To check out and install the source code visit our [GitHub repository](https://github.com/wownmedia/pay).
{% endhint %}

### Setup the database 

It's essential to setup your database on a separate server/cluster than your platform listeners. The database should be configured to be **only** accessible by your platform listener servers and optional management environment. Remember that every seed in your setup will be stored in this database, so make sure you have a secure back mechanism in place including the option to replay every DB transaction. 

* ArkTippr has been tested with PostgreSQL 10
* Make sure you setup snapshots
* Limit access to only your platform listeners and optional management environment \(firewall\)
* All user wallet seeds will be stored in an encrypted format, to prevent them being abused in case your database, or backup, ever gets compromised.

{% hint style="info" %}
**Do make absolute sure that your database and your platform listeners are separate infrastructures! In case one of those infrastructures is ever compromised your user's wallets are safe; in case both get compromised your user's funds are at risk!**
{% endhint %}

Once you have configured your database server/cluster you can load the configuration from the [database.sql ](https://github.com/wownmedia/pay/blob/master/database.sql)file.

### Configuration File

The system is very configurable with a number of setting in a JSON file. See [example.pay-config.json](https://github.com/wownmedia/pay/blob/master/example.pay-config.json). The `pay-config.json` file resides in the `~/.config/ark-pay-nodejs/` directory on your platform listener servers.

To start it's easiest to copy the `example.pay-config.json` file into the config directory and change it's setting. Consult the [The Configuration file](the-configuration-file.md) page for an overview of all settings.

```text
cp -rp ./example.pay-config.json ~/.config/ark-pay-nodejs/pay-config.json
```

### Reddit Listener

A Reddit listener will actively poll the inbox of your tipbot's user account. Any new direct messages or mentions will be parsed for commands and if any commands are correctly identified they will be executed. You can \(and should\) run more than one server with a Reddit listener to avoid a single point of failure. The Reddit Listener can process a number of [commands](https://www.reddit.com/r/arktippr/wiki/usage).

To start create a dedicated Reddit user account for your tipbot and use it to [generate and configure your Reddit App credentials](https://github.com/reddit-archive/reddit/wiki/OAuth2). You will need these credentials in your [configuration file](the-configuration-file.md). 

{% hint style="info" %}
**Your Reddit tipbot useraccount will not be able to post automatic replies until it has sufficient Karma.** 
{% endhint %}

After you have created your Reddit account and credentials you can configure your listener servers. Clone the GitHub repository:

```text
git clone https://github.com/wownmedia/pay.git
```

and install the Node modules with **yarn**:

```text
cd pay
yarn install
```

Copy and edit the config file \(_see above_\) and use pm2 to start your listener:

```text
pm2 start ~/pay/packages/pay-reddit/bin/reddit-listener
```

{% hint style="info" %}
_The Reddit Listener has been tested with Node v11.15.0_
{% endhint %}

### Twitter Listener

A Twitter listener is a server that receives webhook events emitted by Twitter. Twitter will emit an event for every new direct message or mention and those will be parsed for commands and if any commands are correctly identified they will be executed. You can \(and should\) run more than one server with a Twitter listener to avoid a single point of failure. The Twitter Listener can process a number of [commands](https://www.reddit.com/r/arktippr/wiki/usage).

To start create a dedicated Twitter user account for your tipbot and use it to [generate and configure your Twitter App credentials.](https://developer.twitter.com/en/apply-for-access) You will need these credentials in your [configuration file](the-configuration-file.md).

After you have created your Twitter account and credentials you should setup your server to receive the webhook events. It's recommended to use NGINX to proxy/forward the HTTPS traffic to your listener. You can use a configuration like below with cloudflare SSL:

```text
server {

    listen 443 ssl;
    listen [::]:443 ssl;

    server_name twitter.your-domain.com;

    # Add Security
    # Whitelist Cloudflare IPs
    # Source: https://www.cloudflare.com/ips

    # IPv4
    allow 103.21.244.0/22;
    allow 103.22.200.0/22;
    allow 103.31.4.0/22;
    allow 104.16.0.0/12;
    allow 108.162.192.0/18;
    allow 131.0.72.0/22;
    allow 141.101.64.0/18;
    allow 162.158.0.0/15;
    allow 172.64.0.0/13;
    allow 173.245.48.0/20;
    allow 188.114.96.0/20;
    allow 190.93.240.0/20;
    allow 197.234.240.0/22;
    allow 198.41.128.0/17;
    allow 199.27.128.0/21;

    # IPv6
    allow 2400:cb00::/32;
    allow 2606:4700::/32;
    allow 2803:f800::/32;
    allow 2405:b500::/32;
    allow 2405:8100::/32;
    allow 2c0f:f248::/32;
    allow 2a06:98c0::/29;

    # Localhost
    allow 127.0.0.1;
    #deny all;

    # Only allow regular HTTP methods
    if ($request_method !~ ^(GET|HEAD|POST|PATCH|PUT|CONNECT|OPTIONS|TRACE)$ )
    {
        return 444;
    }

    add_header Strict-Transport-Security "max-age=31536000; includeSubdomains; preload";
    ssl_session_cache shared:SSL:50m;
    ssl_session_timeout 5m;
    ssl_ciphers 'ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SH$
    ssl_prefer_server_ciphers on;
    ssl_certificate /etc/nginx/ssl/arktippr.com/server.crt;
    ssl_certificate_key /etc/nginx/ssl/arktippr.com/server.key;

    location / {
      proxy_pass http://localhost:4466;
      proxy_http_version 1.1;
      proxy_set_header Upgrade $http_upgrade;
      proxy_set_header Connection 'upgrade';
      proxy_set_header Host $host;
      proxy_cache_bypass $http_upgrade;
    }
}
```

Clone the GitHub repository:

```text
git clone https://github.com/wownmedia/pay.git
```

and install the Node modules with **yarn**:

```text
cd pay
yarn install
```

Copy and edit the config file \(_see above_\) and use pm2 to start your listener:

```text
pm2 start ~/pay/packages/pay-twitter/bin/twitter-listener
```

{% hint style="info" %}
_The Twitter Listener has been tested with Node v11.15.0_
{% endhint %}

### On-Chain API Listener

The on-chain listener is a server the receives webhook events emitted by an ARK \(bridge\)chain node. The On-Chain API Listener can process a number of [commands](on-chain-api-commands.md).

Configure your node to emit webhooks:

```text
nano ~/.config/ark-core/mainnet/plugins.js
```

 and add/edit the webhooks section \(+enable in the .env\):

```text
"@arkecosystem/core-webhooks": {
    enabled: process.env.CORE_WEBHOOKS_ENABLED,
    server: {
        enabled: process.env.CORE_WEBHOOKS_API_ENABLED,
        host: process.env.CORE_WEBHOOKS_HOST || "0.0.0.0",
        port: process.env.CORE_WEBHOOKS_PORT || 4004,
        whitelist: ["127.0.0.1", "::ffff:127.0.0.1"],
    },
},
```

Create a new wallet on your BlockChain and optionally register it with a delegate-name for clarity. You will use the seed for this wallet in your [configuration file](the-configuration-file.md). 

Clone the GitHub repository:

```text
git clone https://github.com/wownmedia/pay.git
```

and install the Node modules with **yarn**:

```text
cd pay
yarn install
```

Copy and edit the config file \(_see above_\) and use pm2 to start your listener:

```text
pm2 start ~/pay/packages/pay-ark-api-server/bin/ark-pay-server
```

{% hint style="info" %}
_The On-Chain API Listener has been tested with Node v11.15.0_
{% endhint %}

