# Chainscale: a project to scale blockchains to support all the world's financial transactions

As a substrate for a financial and bureaucratic system, blockchains have important advantages: they
allow anyone with a computer to participate in the system, they allow transactions to be audited
so that everyone can know that the rules of the system are being followed, and they aren't dependent
on centralized parties that could commit fraud or otherwise sabotage the system.

The most popular blockchains, such as Bitcoin and Ethereum, are not scalable.  They require every
full node to download and verify every transaction.

## Alternatives to "everyone verifies everything"

There are 2 broad categories of alterantives to everyone verifying everything:

1. A _positive_ verification method will include in each piece of data (such as a block) a "proof" that that data is valid.  This includes verifying that other pieces of data referred to by this piece of data contain such proofs.
2. A _negative_ verification method permits proofs that a given piece of data is invalid.  If such proofs are found, they are distributed to others so that the invalidity can be widely known.

We concentrate mainly on positive verification methods, since negative verification methods are vulnerable to network issues (including issues caused by uncooperative parties) that could prevent the sharing of invalidity proofs.

There are 2 main forms of positive verification we consider:

1. Use of zk-SNARKs to prove the data is valid, and that data referred to contains valid zk-SNARKs showing their own validity, recursively.
2. Signatures from a supermajority of a random set of verifiers may be included, which assert that the supermajority has checked that the data is valid (and referenced data contains valid signatures asserting validity of that data, recursively).

Although zk-SNARKs are sufficient to show validity, they aren't sufficient to show that the data itself is generally available to third parties.

In the case of the supermajority of a random set, the set must be selected to be large enough (and the supermajority threshold must be set) such that it is very likely that there is an honest supermajority, and extremely unlikely that there is a dishonest supermajority.
