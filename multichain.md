
# Multi-chain system

One approach to scaling a blockchain system is to break a single chain into multiple chains, each with its own currency/currencies. Cryptocurrency exchanges already work on this principle: they download and check multiple blockchains in order to track currency amounts on these chains. Users only need to download the blockchains that they actually use.

If the chains are proof-of-work, there is a potential security vulnerability in that an attacker could devote lots of computation to a single chain at once, breaking it and gaining resources that can be used to buy more computers and attack other chains. A many-chain system is more vulnerable than a single-chain system because each individual chain will have a smaller amount of compute mining it, making it easier to take over.

Proof-of-stake does not have a similar issue. Although it is possible for an attacker to buy lots of currency, such currency must be voluntarily sold by current holders, and it would likely be clear to them that this was happening. It is also possible to separate a governance token from a monetary token, and have staking use the governance token; governors would be responsible for ensuring that the chain remains controlled by good actors.  This is similar to a private company in that the equity is not sold on an open market, and therefore the company is not vulnerable to hostile takeovers.

Even with this security problem solved, a multi-chain system has less functionality than a single scalable chain, since, for example, the different chains must use different currencies, and smart contracts can't work across chains.

A proposal for how to ameliorate this loss of functionality is to allow sending messages across chains. That is: a user of chain A should be able to log a message on chain A that is then read by verifiers of chain B, so that chain B can know that this message has been sent to it.

This raises the technical question of how to ensure that such messages can be known about, without requiring all users of chain B to download the entire chain A.  One approach, given the proof-of-stake setup, is to have stakers/governors of chain A sign a message saying that a given message is in the chain, or that a recent block in the chain has a given hash code. This information can be downloaded by users of chain B to confirm messages sent by chain A.

Verifiers of chain B need to download a partial history of chain A, as the governors could change over time, thus requiring a different set of governors to sign for a given message or block of chain A. Since governors will change infrequently compared with other blockchain events, this is not a large computational or memory cost.

A problem comes when a majority of governors lie about blocks of chain A. The main desideratum is that this lie can eventually be detected. Such lies will be rare if they can be caught; governors of chain A will have an interest in being trusted, both by users of chain A and chain B.

To catch these lies, someone may pay a small amount of chain A's governance token to challenge a claim made by a governor of chain A, who must in turn reveal blocks of chain A that prove the original claim. If such blocks are not revealed, the lying governor is punished by removing their governance tokens, giving some to the challenger as compensation.


