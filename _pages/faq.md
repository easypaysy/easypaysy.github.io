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

# Won’t this bloat the blockchain?
Opening an account only takes a few hundred bytes of blockchain space. One can hardly imagine a more appropriate use case for using blockchain space than a mechanism that radically improves the safety and ease of use of crypto payments. 
Anyway, when easypaysy becomes so popular that blockchain space starts becoming a problem, we'll introduce Master accounts (a feature reserved for a future release).

# What are Master accounts?
Master accounts are a planned feature for a future release.
If and when they are introduced, they allow up to 2048 to reside in a single transaction.
They drastically reduce the need for blockchain space.

The one caveat is that they require cooperation from a service provider, but no trust. 
The details will be ironed out in its due time.

# I don’t see the need to create yet another way of payments, why should I bother?
You shouldn’t. If you are fully satisfied with the way you are conducting crypto payments currently, just keep going on.



# Ok, but really, why should I bother, what are the key benefits of easypaysy accounts?
Since you insist, these are some of the key benefits:

- (1) Account ids are short and easy to remember and communicate, like:
	btc@883624.1549/347
  btc@curious-insect.script/fine
  
- (2) Account ids are permanent, you get one and don’t ever need another

- (3) By paying to an account id, you can be reasonably sure of whom you are paying to.

- If the need arises, the payer can legally prove he made the payment to the proper destination.

- Because of (1) account ids can be typed easily, thus avoiding COPY and PASTE attacks

- Small mistakes are very easy to spot. 

- Since you have to spend some time and money to open an easypaysy account, it is wholly impractical for an attacker to open fake accounts in order to have one ID that’s similar to yours. Also, because the checksum is unpredictable since it depends on data outside of the account itself (namely the block hash and the merke root), account ids are extremely secure.

# Who assigns the account id?
Nobody really, they are assigned quasy randomly. You can only control the block number, which constitutes the first part of the account id. The rest depends on the positioning of your account within the block and that is a random even by all purposes, unless you are the miner yourself. However, the checksum part, which is also an integral part of the account id, depends also on the Merkle Root and the Hash of the block, so even the miners have very little control over the naming of your account.



# If I pay extra, can I choose a particular account id?
No you can’t. That would undermine the uniqueness and safety of the protocol and it is impossible by design.
But I really really want to have a custom account id, what can I do?
You can associate your account id with a domain of yours. Following the previous examples, if you own the domain: example.com, you could have these account ids:

	btc@example.com/269
	btc@example.com/drive

The checksum part of the domain id is out of your control however. The best you could do is trying more than one account until you find one whose checksum you like.

# How is the checksum computed?
The checksum of an account is computed following a very simple procedure, namely:
1.- Let block_hash be the sha256 hash digest of the block where the account tx is stored.
2.- Let merkle_root the the sha256  hash digest of the merkle root of said block
3.- Let tx_hash be the sha256 hash digest of the transaction that contains the account.
4.- Let checksum_hash be the  digest of sha256.hash( block_hash & merkle_root & tx_hash) where & denotes concatenation.
5.- Let checksum_1 be checksum_hash[0..7] modulus 1000, where checksum_hash[0..7] represent the first 8 bytes of checksum_hash, zero left padded to 3 positions.
6.- Let checksum_2 be checksum_hash[8..15] modulus 1000, as in  5.
7.- Let checksum_3 be checksum_hash[16..23] modulus 1000, as in 5.
8.- Let checksum_4 be checksum_hash[24..32] modulus 1000, as in 5.
Given these calculations, the checksum is formed by concatenating the checksum_i fields using the hyphen symbol, that is:

checksum = checksum_1 & ‘-’ & checksum_2 & ‘-’ &  checksum_31 & ‘-’ & checksum_4 

where & denotes concatenation and ‘-’ represents the hyphen symbol.
What’s the probability of two accounts having the same checksum?
There are 10^12 different checksums. Given the way they are computed, you could calculate the probability

# Do easypaysy accounts have a maintenance fee?
No, they don’t.  Once you open the account (for which you pay a regular tx fee) is paid forever. However, if you need to update or cancel it, you’ll have to pay a new tx fee.

# When can I start using them?
At the time of writing this (december 2019) easypaysy accounts are still a work in progress. Much of the specification is probably close to final, and there is some proof of work code, but there is still much to do. 
Hopefylly, it will launch in the next 12-18 months.

# Can I have more than one easypaysy account?
Sure! You can have as many as you are willing to pay for. However, in the general case, you will only need one account, so please don’t open more than you need since it provides no real benefit to you and you would be pointlessly increasing the UTXO size.

# Can I close an easypaysy account?
Yes, you can close your easypaysy account at any moment.

# How can I cooperate with this project?
If you have knowledge and would like to be part, please get in contact at easypaysy@gmail.com

# What wallets support easypaysy accounts?
At the time of writing, no wallet that I know of supports easypaysy accounts. If you are responsible of a wallet and want to integrate easypaysy accounts in your application, please get in contact at easypaysy@gmail.com

# What coins are supported by easypaysy?
Although primarily intended for Bitcoin, the easypaysy technology can be easily adapted to many other crypto projects, specially those that are closely related or derived from Bitcoin.
Litecoin should be very straightforward, for instance. If you would like to comment something on a crypto project you are part of, please get in contact at easypaysy@gmail.com

