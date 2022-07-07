# Gigascaling: a project to scale blockchains to support all the world's financial transactions

As a substrate for a financial and bureaucratic system, blockchains have important advantages: they
allow anyone with a computer to participate in the system, they allow transactions to be audited
so that everyone can know that the rules of the system are being followed, and they aren't dependent
on centralized parties that could commit fraud or otherwise sabotage the system.

The most popular blockchains, such as Bitcoin and Ethereum, are not scalable.  They require every
full node to download and verify every transaction.  This means high transaction fees, and it means
that even a single large country's financial transactions could not all occur on these networks.

## Theoretical alternatives to "everyone verifies everything"

There are 2 broad categories of alternatives to everyone verifying everything:

1. A _positive_ verification method will include in each piece of data (such as a block) a "proof" that that data is valid.  This includes verifying that other pieces of data referred to by this piece of data contain such proofs.
2. A _negative_ verification method permits proofs that a given piece of data is invalid.  If such proofs are found, they are distributed to others so that the invalidity can be widely known.

We concentrate mainly on positive verification methods, since negative verification methods are vulnerable to network issues (including issues caused by uncooperative parties) that could prevent the sharing of invalidity proofs.

There are 2 main forms of positive verification we consider:

1. Signatures from a supermajority of a random set of verifiers may be included, which assert that the supermajority has checked that the data is valid (and referenced data contains valid signatures asserting validity of that data, recursively).
2. Use of zk-SNARKs to prove the data is valid, and that data referred to contains valid zk-SNARKs showing their own validity, recursively.

Although zk-SNARKs are sufficient to show validity, they aren't sufficient to show that the data itself is generally available to third parties.

In the case of the supermajority of a random set, the set must be selected to be large enough (and the supermajority threshold must be set) such that it is very likely that there is an honest supermajority, and extremely unlikely that there is a dishonest supermajority.
However, individual random sets are potentially vulnerable to bribery as they include only a minority of verifiers.

## Concrete algorithms

The main algorithm we are developing is [Erasure Coded Sharding](./ErasureCodedSharding.pdf) (2022), which uses a combination of recursive zk-SNARKs,
Reed Solomon codes, and signatures by a supermajority of verifiers to ensure validity and data availability even in the face of bribery.

A previous algorithm is the [Inductive Consensus Tree Protocol](http://ictp.io) (2018), a method that uses signatures of a supermajority of a random set of verifiers for
ensuring validity, and constructs a new Merkle Patricia tree of account states in each new block.

We are additionally researching [multichain](/multichain) systems that allow for users of different blockchains (with their own currencies) to send messages between the different chains, enabling cross-chain applications, and achieving scalability through the multitude of mostly-independent blockchains. The technical design we are using has many similarities with [Cosmos](cosmos.network), and some differences.

# Contact

This website was created by [Jessica Taylor](http://jessic.at).  I can be contacted at [jessica@gigascaling.net](mailto:jessica@gigascaling.net).

<form action="https://gigascaling.us20.list-manage.com/subscribe/post?u=61c975c73b706888efaa969c1&amp;id=6cc0960d2f" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
	<label for="mce-EMAIL">Subscribe to our newsletter:</label>
	<input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="email address" required>
    <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
    <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_61c975c73b706888efaa969c1_6cc0960d2f" tabindex="-1" value=""></div>
    <input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button">
</form>


