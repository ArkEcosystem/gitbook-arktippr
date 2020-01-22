# ArkTippr Usage Guide

## Before You Start
{% hint style="info" %}FYI: Many bots ignore text and commands that are stylized.  So you don't want to be executing commands that are bold, italic, etc.{% endhint %}

## Getting Started
**How to start using ArkTippr** 

1. Acquire Ark and store it on an official desktop or mobile wallet, or exchange (not recommended)
2. Send a private message to ArkTippr with the command DEPOSIT
3. ArkTippr will respond with your ArkTipper Ark address, forever bonded to your Reddit account
4. Copy this address and add it to your Ark Wallet.  The address will be in Watch-Only mode
5. The address is still in your clipboard, so you can use your wallet to send some Ark to it
6. Now your ArkTippr address has some Ark in it! To see, send ArkTippr the command BALANCE
7. Respond to a post or comment with command "2 u/ArkTippr"
8. That user has now been sent 2 Ark from you!
9. That user can still collect that Ark even if they have not set up their ArkTippr Ark address yet.

**Methods of using ArkTippr** 

1. Sometimes, you use ArkTippr publicly, in a comment or post. This is done when tipping or using the 'STICKERS' command.
2. Other times, you use ArkTippr by sending commands as a private message directly to ArkTippr. This is done when using all other commands.

---

## Tipping
**Publicly reply to a comment or post** 

To tip a user as a reward for good content, simply reply to the specific comment or post with:

    <amount> [currency] u/arktippr [~]

 or you can reverse the variables:

    [currency] <amount> u/arktippr [~]

This will transfer the `<amount> [currency]` converted to Ark from your ArkTippr Ark wallet to theirs - on-chain!

If the other user did not set up an ArkTippr Ark wallet yet, it still works. The Ark is waiting for them on the blockchain!

* `<amount>` is the amount you like to tip *(e.g. 10, 1.5)* 
* `[currency]` is one of the [supported currencies](#wiki_supported_currencies). If no currency is declared, ARK is the default.
* `[~]` enables a smaller footer on the public reply ArkTippr posts on a tip comment.
 
**Examples:**

Commenting on that cool post - or replying to his remarkable comment - by u\/bobby with:
   
    2.5 USD u/arktippr

will let Bobby know how cool he is and transfer (*from your ArkTippr Ark Wallet*) the amount of Ark with the current value of $2.50 USD to u\/bobby. Or, you can use Ark natively:

    1.1 u/arktippr

That will send Bobby a tip of Ѧ1.1 Ark. Keep in mind, when we say "currency" and "conversions" we are simply estimating how much Ark to tip according to the current exchange rate. "10 USD" does not send actual USD, it sends 10 USD worth of Ark at the current exchange rate. ArkTippr calculates exchange rates in the background for you, in near real-time. See the bottom of this page, as ArkTippr supports many currencies other than USD!

{% hint style="info" %}**Did You Know?** You can tip any Reddit user on any Subreddit- you are not confined to Ark's Subreddit!{% endhint %}

---
 

## Reward
**Publicly reply to a comment or post** 

To tip multiple users as a reward for good content, simply reply to the specific comment or post with:

    REWARD u/arktippr
    <amount> ARK username1
    <amount> ARK username2
    <amount> ARK username3

This also works with STICKERS:

    REWARD u/arktippr
    STICKERS username1
    STICKERS username2
    STICKERS username3

This allows you to reward multiple people publicly with ARK. Keep in mind to specify all usernames WITHOUT the "u/" callsign. 

Arktippr will respond to your comment with multiple confirmation comments per user tipped.

Also keep in mind, to create a new line, you need to hit enter twice when composing, otherwise the comment will not show up with new lines.

If you are using the REWARD command responding to a post, you will need to specify the original poster's username in the reward list if you want to tip them as well.

{% hint style="info" %}**Did You Know?** You can tip any Reddit user on any Subreddit- you are not confined to Ark's Subreddit!{% endhint %}

---

## Send
**Send ArkTippr a Private Message** 

Sometimes, you will want to send Ark to another Reddit user privately, without a public comment that everyone can see. This is accomplished with the SEND command. It's more anonymous than Venmo, and more fun than Paypal :) 

To transfer Ark to a Reddit user privately, send ArkTippr a private message like this:

```SEND <username> <amount> [currency]```

or you can reverse the variables:

```SEND <username> <currency> <amount>```
 
* `<username>` should be a **valid Reddit user**

* `<amount>` is the amount you like to send *(e.g. 10, 1.5)*

* `[currency]` is one of the [supported currencies](#wiki_supported_currencies).  If no currency is declared, ARK is the default.

**SEND is irreversible,** so be sure the reddit username and amount is correct. 

**Examples:** 

Sending ArkTippr a private message with:

    SEND bobby 5 USD

will transfer (*from your ArkTippr Ark wallet*) the amount of Ark with the current value of $5.00 USD to u\/bobby.

    SEND bobby 7.865

will transfer Ѧ7.865 ARK to u\/bobby

The SEND command will result in another Reddit user receiving funds from you without you needing to post a public comment.

{% hint style="info" %}**Points to consider regarding SEND:**

1. **Do not send 'commands' directly to the other user.** You will be sending commands to ArkTippr, who will take care of the rest.
2. SEND will bypass the need for a public comment on Reddit, but it will still create a publicly viewable transaction on the Ark blockchain itself.
3. If for some reason the other user no longer has access to their Reddit credentials, they will not be able to retrieve the funds you sent. {% endhint %}

{% hint style="info" %}**Did You Know?** You can use SEND for any Reddit user- you are not confined to Ark Subreddit users!{% endhint %}

---


## Stickers

[ArkStickers](https://ArkStickers.com) has created a great set of stickers and Ark info sheet that can be used to promote Ark technology. 

When you use the STICKERS command, you will give that user (or yourself) a code redeemable at [ArkStickers.com](https://ArkStickers.com) for a sticker set, and it never expires!

There are two ways to accomplish this:

**1) Publicly reply to a comment or post** 

To send a Reddit user an ArkStickers sticker code, comment on their post or reply to their comment with:

```STICKERS u/arktippr```

This will do the following:

1. Send Ѧ2 ARK from your balance to ArkStickers.com Ark wallet
2. Generate an ArkStickers stickers code
3. Send the code privately to the user in question via Reddit private message.

They will receive a code that you paid for in their messages Inbox, and they can use their code on ArkStickers.com to get their stickers for free (no Ark transaction required for them). 

Everyone on Reddit will see that you gave them stickers!

Sticker codes can only be used one time.

**2) Send ArkTippr a Private Message** 

You can also do this by sending ArkTippr a private message with the command:

```STICKERS <username>```

This will do the following:

1. Send Ѧ2 ARK from your balance to ArkStickers.com Ark wallet
2. Generate an ArkStickers stickers code
3. Send the code privately to the user in question via Reddit private message.

*(This method allows you to get a code sent to yourself if you want to.)*

They will receive a code that you paid for in their messages Inbox, and they can use their code on ArkStickers.com to get their stickers for free (no Ark transaction required for them). 

This method does not use public comments, so no one will see that you gave them stickers.

Sticker codes can only be used one time.

{% hint style="info" %}**Did You Know?** You can use STICKERS for any Reddit user on any Subreddit- you are not confined to Ark's Subreddit!{% endhint %}

---
 

## Deposit and Address
**Send ArkTippr a Private Message** 

Before you can tip a Reddit user, you need to deposit Ark to your ArkTippr wallet. Arktippr creates a personal wallet for each Reddit user on the Ark blockchain, and your balance is kept on your wallet. 

To receive your deposit address, send ArkTippr a private message with this command:

```DEPOSIT ```
 
You can load up your ArkTippr wallet with any amount of Ark you'd like. Please keep in mind that anybody with access to your Reddit credentials also will have access to this wallet. 

**Do NOT deposit or store large amounts of Ark in this wallet**. Treat it like a small coinpurse.

{% hint style="info" %}Pro Tip: Add your ArkTippr [Ark wallet address](#wiki_deposit_and_address) to any of the official wallets as a Watch-Only address and you can track your ArkTippr balance alongside your other addresses as well.{% endhint %}

---

## Balance
**Send ArkTippr a Private Message** 

To see the balance of your ArkTippr Ark wallet, send ArkTippr a private message with this command:

```BALANCE```


{% hint style="info" %}Pro Tip: Add your ArkTippr [Ark wallet address](#wiki_deposit_and_address) to any of the official wallets as a Watch-Only address and you can track your ArkTippr balance alongside your other addresses as well.{% endhint %}

 
---

## Withdraw
**Send ArkTippr a Private Message** 

You can withdraw all the Ark in your ArkTippr wallet to a different wallet:

**To withdraw the total balance:** 

    WITHDRAW <address>

You can also withdraw only some of the Ark in your ArkTippr wallet to a different wallet:

**To withdraw a partial balance:** 

    WITHDRAW <address> [amount] [currency]

* `<address>` should be a **valid Ark wallet that you control.** WITHDRAW is irreversible so make sure the address is correct.

* `[amount]` is the amount you like to withdraw *(e.g. 10, 1.5)*

* `[currency]` is one of the [supported currencies](#wiki_supported_currencies).  If no currency is declared, Ark is the default.

**Examples:**

Sending ArkTippr a message with:

    WITHDRAW AUDud8tvyVZa67p3QY7XPRUTjRGnWQQ9Xv 50.25 EUR

will transfer (*from your ArkTippr Ark Wallet*) the amount of Ark with the current value of €50.25 EUR to AUDud8tvyVZa67p3QY7XPRUTjRGnWQQ9Xv 

    WITHDRAW AUDud8tvyVZa67p3QY7XPRUTjRGnWQQ9Xv

will transfer the total balance to AUDud8tvyVZa67p3QY7XPRUTjRGnWQQ9Xv

---
 

## Stacking Multiple Commands
**Send ArkTippr a Private Message** 

When using private messages to send commands to ArkTippr, you can stack commands in a single private message. 

**Examples:**

**To send Ark to multiple people at once, send this private message to ArkTippr:**

    SEND bobby 5
    SEND sally 3 USD
    SEND kenny 6.543
 
This will send 5 Ark to Reddit user bobby, 3 USD worth of Ark to Reddit user sally, and 6.543 Ark to Reddit user kenny.
Remember that the SEND command does not use public comments, so these actions will not be publicly displayed on Reddit.

**To withdraw to multiple of *your* other wallets at once:**

    WITHDRAW <address1> 12
    WITHDRAW <address2> 12
    WITHDRAW <address3> 8 USD

This will withdraw 12 Ark to your address1, 12 Ark to your address2, and 8 USD worth of Ark to your address3.

**To make it rain stickers on a bunch of people:**

    STICKERS bobby
    STICKERS sally
    STICKERS kenny
 
This will send unique ArkStickers stickers codes directly to Reddit usernames bobby, sally and kenny.

**As you can tell, there are many great uses for stacking commands:**

1. Reward everyone who contributed to a post with Ark or Stickers
2. Withdraw your ArkTipper balance to multiple addresses easily
3. Send sticker codes or Ark to high-profile Reddit users so they can learn about Ark
4. Reward or pay all volunteers with ease who assisted you with a task
5. Send a bunch of people Ark without knowing all their Ark addresses in advance
6. Even more uses!

ArkTippr is a powerful tool you can use to reward others and use Reddit and Ark in concert.

---

# Supported Currencies

Currently arktippr supports the following currencies:

* `ARK` | `Ѧ` - Ark 
* `USD` | `$` - United States dollar 
* `EUR` | `€` - Euro  
* `GBP` - British pound
* `BTC` - Bitcoin Core
* `BCH` - Bitcoin Cash
* `XQR` - Qredit

# Direct Deposits

You can send ARK directly from the ARK desktop/Mobile wallet to any Twitter and Reddit user:

1. Generate a new (Send) transaction in the wallet;
2. Select [Arktippr](https://explorer.ark.io/wallets/AcqtFLrackRcUbDdkkSZ2vSum7WqQ3W7A1) `AcqtFLrackRcUbDdkkSZ2vSum7WqQ3W7A1` as the receiver;
3. Add the Twitter/Reddit user you like to transfer ARK to in the Vendor-field, make sure you include the platform! Examples: `marcs1970@reddit` or `cryptologyhk@twitter`;
4. Set the amount of the transaction to the amount you like to transfer + 0.016 ARK for fees (e.g. like to transfer 1 ARK, then set the amount to 1.016 ARK);
5. Send.

ArkTippr will receive your transaction, detect the intended receiver from the Vendor-field and forward the amount. It will notify the receiver on either Twitter or Reddit and notify you with a transaction on the ARK Blockchain. The transaction to you contains the transaction ID of the forwarded transaction so you can keep track.
