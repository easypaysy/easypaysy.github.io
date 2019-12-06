---
permalink: /faq/
title: "FAQ"
published: True
---

# What is easypaysy?
Easypaysy stands for Easy Payment System. It is a Layer 2 blockchain technology designed to improve the usability, safety, accountability and privacy of crypto payments by allowing users to create accounts directly on the blockchain and make payments to account ids instead of addresses.

# What is a (blockchain) Layer 2 technology?
A layer 2 technology -in the blockchain context- is a technology that, like easypaysy- doesn’t require any changes in the consensus protocol. As such, it is completely optional and doesn’t need neither a soft nor a hard fork on the blockchain. 
It simply builds upon the existing blockchain technology to provide a capability that wasn’t available before, in this case, payments to accounts instead of addresses.

# Is it only for Bitcoin or can other cryptocurrencies use this technology?
It is originally intended for bitcoin. The proof of concept code has been designed to use it only with bitcoin, but it can easily be ported to other altcoins, especially those intimately derived from bitcoin, such as Litecoin and many others.  Segwit is a plus, but not mandatory.

# What is an easypaysy account?
An easypaysy account is a specially formatted entry (transaction) within the blockchain, which has an associated account id (like btc@789123.640/335-026), a couple of public keys and a JSON document that details the types of payment accepted and  the contact information. 

# Will the bech32 and base58 addresses disappear with the introduction of the easypaysy accounts?
Not at all. Easypaysy accounts hides the complexity of traditional addresses from the user, but they are still used underneath. Also, this is an optional technology. Users can decide to keep using addresses for their payments.

# Accounts?  Does that mean that the nefarious big banks are behind this technology to monopolize the use of Bitcoin?
Again: not at all. Users are free to open easypaysy accounts on their own. The accounts are open on the blockchain itself and no third party is required. Banks, or any other entity could one day offer a service to facilitate the opening of easypaysy accounts, but those will always be optional services that the users will decide whether to use or not.

# How long does it take to open an account?
Easypaysy accounts are based on standard blockchain transactions. For additional security it is necessary to wait until the account has at least 100 confirmations. On average, it will take around 17 hours to have a new account operational, give or take a few minutes. You can use that time to verify that everything is OK. Otherwise, you can update the account's configuration before it becomes operational.

# How secure are these accounts, compared with traditional crypto payments?
Exactly the same. This is just a mechanism to hide the complexity of dealing with addresses, but the internals are the same.

# How about privacy?
There are different kinds of easypaysy payments: interactive and non-interactive. Interactive payments come in different flavors, depending on the protocol used to request the payment addresses. All the communications back and forth between payer and payee are encrypted by default, so privacy should be ensured.

However, for maximum privacy, non interactive payments (aka IOC or Hollywood payments) can be used. With these payments, the payer can generate a unique payment address for each payment, without ever contacting the payee. This way, there is absolutely no way a third party can snoop these kind of payments. The only potential problem is the query to get the account info, before the payment is prepared, and that is a non-issue for full nodes. If a full node is not suitable for your application, you can minimize confidentiality risks by retrieving full blocks in order to retrieve account information, instead of asking for a particular account tx.

# Why use the blockchain to store account information?
By leveraging on the blockchain, users get many benefits: 
- The infrastructure used to make and receive crypto payments, is exactly the same
- We have a good understanding of the strengths and vulnerabilities of the blockchain
- All the properties that make crypto payments robusts, also make easypaysy accounts robust.
- No third parties or technologies are involved.
