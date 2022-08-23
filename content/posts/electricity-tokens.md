---
title: "Electricity Tokens - No extra wires"
date: 2022-08-01T08:48:51+07:00
tags:
    - electricity
    - iot
    - simple
    - listrik
    - pln
    - cryptography
    - sts
cover:
    image: /benar.png
draft: false
---

**I am by no means an expert in this topic. I just dig some information on the Internet and condense it to some words. Please take a look at the references listed below, and feel free to correct me!**

Some years ago, I have a weird fascination about how the prepaid electricity meter works. In Indonesia, there's two ways you can have electricity in your home. One is postpaid, where for every month the electricity usage is tracked by a meter installed in your home and a person will come to check it and prints out a bill. The second one is prepaid, where you purchase a "token" of whichever nominal you'd like, and then you enter the token into the electricity meter in your home and boom, you granted electricity in your home until you used all the power from the nominal that you have purchased.

## But it scratches my head, How does that work?


I mean it's not like it's connected to the internet, your meter doesn't connect to WiFi like everything needs to these days, right? Or maybe it does have a SIM card on it and it connects via 3G... or uhh 4G??? Or maybe PLN have some sort of other cable other than electricity to connect the meters with their headquarters??? Wrong.

I digged the Internet for the documentation on a quite common prepaid electricity meter (as in I saw it in some places), the **Hexing HXE116-KP**. The implementation of features on this meter may be different from other meters, but the standardization that is used is standard across all prepaid electricity meter in Indonesia.

# SPLN D3.009-1:2010 and STS
The Hexing HXE116-KP documentation advertises itself as a meter that is **SPLN D3.009-1:2010** compliant and adheres to the **STS** system to transfer credits. 

So what is this "SPLN D3.009-1:2010" standard? The PLN (Perusahaan Listrik Negara/*National Electricity Company*) issued a standard in 2010 called the "**Meter statik energi aktif fase tunggal prabayar dengan Sistem Standard Transfer Specification (STS)**", or "***Static single phase active energy prepaid meter with the Standard Transfer Specification System (STS)***". Bingo! This should explain it all.

To know how all this magic works, we need to know about the Standard Transfer Specification (STS). The STS is essentially a one way prepaid method with a flat cost, where information is sent from the vending system to the meter and not the other way around. That means the meter doesn't communicate to anything, really.

# What is this STS thing and how does it work?

If you are into programming, networking, computer security, or just IT in general, you might know about [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography). The Standard Transfer Specification (STS) is a global standard that is used for the transfer of electricity and other utility prepayment tokens.

![](/electricity-tokens/posmeterkey.png)

Simply, in the STS system there is a meter, a point of sale, and the consumer. The meter's job is to regulate the supply to it's credit balance, and you get the credit from tokens. Every meter is assigned with a unique code and a decryption key to decrypt tokens, and it can only decrypt tokens that are assigned to it. So how do you get these tokens then? Well, you buy it!

The Point Of Sale's job essentially is to just 
1. Get the payment of the consumer
2. Find the encryption key that is assigned to the meter's unique code
3. Convert the amount of money to utility credit with current costs (how much kWh can you get for x amount of $)
4. Create the token by encrypting the credit amount with the encryption key
5. Give token back to consumer

And then the consumer just needed to enter the token into the meter and voila!

The meter knows that the token is valid because it is able to decrypt it, meaning it is encrypted with the right key, and it is able to know the credit amount after decrypting the data. No internet, no IoT, no connection just simple cryptography magic!

# What if the electricity provider wanted to control the cost?
The meter does not care at all how much you paid for the token. Each token generated contains the granted quota of the utility for that token. For example, you buy an electricity token for $30, that would be converted to how much electricity can you get for $30 at the time of purchase. If today it gets you 328.9 kWh, then the token would contain that value and it only cares about that value, so controlling the cost is easy as the provider just needs to change it from one side.

For consumers, this is also a *saving* grace. Postpaid electricity is more susceptible to price control due to the nature of it being postpaid. Your current monthly usage could cost more tomorrow even if you have not paid for it [1].  In theory, the STS system means that the provider cannot control what you have already paid for, as it can only control the price of the tokens, not how much a usage costs.

## Closing note - Good for consumers, and good for providers
Prepaid electricity is good for consumers and it's providers. For consumer, they will be more aware of their usage and have less unexpected bills. For providers, this is a cheap system to implement and is more easy to maintain [2].

[1] Just a posibility. This will depend on your electricity provider's policy 

[2] This is from my point of view and experience. For one, in Indonesia usually there's people going to houses to check the meters of postpaid electricity. [The providers that wants to implement STS needs to pay a membership fee annually to the STS association](https://www.sts.org.za/membership-application-process-form), it is a small price to pay for an electricity provider, but still worth mentioning.

## References
[SPLN-D3-009-1-2010](https://www.scribd.com/doc/213657911/SPLN-D3-009-1-2010)
[Brosur Hexing HXE116-KP](https://www.scribd.com/document/359415242/Brosur-Hexing-HXE116-KP)
[Standard Transfer Specification Association](https://www.sts.org.za/)
[Prepayment Standard Transfer Specification: An IEC standard](https://www.smart-energy.com/wp-content/uploads/Don%20Taylor.pdf)
