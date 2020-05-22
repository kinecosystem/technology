# Kin Improvement Proposal
The purpose of this document is to propose a migration of the Kin Ecosystem from the Kin Blockchain to the Solana Blockchain.

## Proposed By:
Kik Interactive Inc.

## Summary
Today Kin is used by millions of consumers across more than 50 independent apps. From what we have seen, that makes Kin the most used cryptocurrency by mainstream consumers. Getting to this level of scale has required constant iteration. Kin was first launched on Ethereum but quickly capped out at thousands of consumers, with long transaction times and high  transaction fees. After building Kik Messenger for 10+ years we at Kik understood that for crypto to break into the mainstream, millions of people need to be able to transact near instantly with zero fees. This is what consumers expect in great consumer products, and crypto should be no different. So in Q1 2018, on behalf of the Kin Foundation, we  started working with the Stellar protocol as a potential alternative to Ethereum. After working through a number of iterations with the Stellar testnet, we proposed a custom fork of Stellar that was ultimately adopted by the Kin Ecosystem. This unlocked the ability for the ecosystem to introduce better consumer experiences at scale. Since then, the Kin Ecosystem has grown from 100k monthly active spenders to over 3MM. 

The fork of Stellar enabled Kin to reach millions of consumers, but we knew there were limitations. Stellar has five second block times, so irrespective of network load, a consumer could be seeing five second latency on their transactions - not what we would deem a great consumer experience. We also knew that at some point the Kin Ecosystem would overtake the bandwidth of Stellar, so in Q2 of 2019 we at Kik Interactive Inc. started looking at other potential options for Kin. 

Over the last year, we’ve been evaluating different options including existing blockchains, layer 2 solutions, and new blockchains coming to market. After working through all the options, we believe that Solana is the best fit for Kin and are making a formal proposal to developers with an active app in the Kin Ecosystem to migrate from the Kin Blockchain to the Solana Blockchain.

The following proposal has four parts: 
1. Challenges With Stellar
2. Opportunity With Solana
3. Aligning Incentives With Solana
4. Recommended Next Steps

## Challenges with Stellar
The Kin Blockchain is a fork of Stellar which has a number of limitations. These limitations can be broadly bucketed into the following:

1. Performance: Latency and transaction throughput
2. Feature Set: Limitations with how much ‘extra data’ can be attached to transactions

### Performance
The Stellar protocol publishes a ledger every five seconds, which has a maximum capacity of 500 transactions per ledger. This caps the throughput of Kin to 100 transactions per second. There has been a lot of work done to improve this throughput, but there are fundamental constraints that limit the overall transaction throughput. 

While there are likely small gains to be made, the Kin Blockchain is still at least an order of magnitude short of where we think it needs to be to support the growing demands of the Kin Ecosystem. 

Latency is one of the biggest fundamental challenges of the Stellar protocol. The average transaction confirmation time is approximately ½ the ledger generation time (5 seconds), which does not support a strong consumer experience. This is a hard constraint that cannot be reduced in Stellar. 

### Feature Set
While Stellar offers most of the features needed to do basic functions like sending Kin between accounts, there is a limited amount of space for metadata on transactions. Transaction metadata is important for the Kin Rewards Engine (KRE) to function, as well as other functions such as ecosystem metrics (e.g. breakdown of usage by app) and transaction type (e.g. IAP).

Stellar allows up to 30 bytes of metadata (called a ‘memo’) per transaction, which is far short of what Kin needs to perform its basic functions. As a result, SDKs have had to either omit metadata, or refer to an off-chain lookup - both of which are undesirable.

## Opportunity with Solana
Solana solves both the latency and feature set problems. Solana uses a Proof of History consensus model, along with a number of other novel innovations that unlock significant improvement in throughput and latency. Additionally, Solana would allow significantly more metadata in transactions since it has a Virtual Machine implementation, offering more flexibility.

### Performance
Solana is measured to have approximately 60,000 transactions per second, with 400ms block times. Utilizing just 3% of that throughput for Kin would result in an order of magnitude improvement to throughput.

Additionally, the 400ms block times results in an 84% reduction in average latency (assuming a uniform distribution on 5 second blocks, and a consistent distribution of arrival times between chains). This is far closer to ‘acceptable’ latency for consumer experience.

### Feature Set
Solana, much like Ethereum, allows the implementation of smart contracts (known as programs) which would allow us to create a custom token, similar to the ERC20 standard. That would enable additional metadata to be attached to transactions (provided the entire transaction is less than ~1KiB). This would provide significantly more room to add metadata, reducing the dependence on off-chain data references.

### Validation
In order to validate the above claims, we created a small proof of concept to simulate what Kin on Solana might look like and how it would perform. Using an ERC20 token program as a reference, we submitted transactions against a local Solana test node (running on a Macbook Pro, i9, no GPU enabled), as well as against Solana’s testnet. We were able to submit transactions with an average latency of less than 1 second, and a throughput of over 1,000 transactions per second. Additionally, we were able to fit at least triple (90 bytes) the metadata into a transaction without any issues, and it is likely that we could fit more.

## Aligning Incentives With Solana
A move to Solana would be an important step in unlocking the infrastructure required to build strong consumer experience at scale. This would also be an important step in continuing to decentralize the Kin Ecosystem by aligning with another strong team in crypto and running on their public infrastructure. Both we and the Solana team agreed it is important that there are aligned incentives between the two ecosystems. Given that, the Solana Foundation is offering a grant of SOL tokens to the Kin Foundation for the Kin Ecosystem to migrate to Solana. The parameters of that grant are as follows: 

I | II
------------ | -------------
Max Grant Amount | 1% of the total SOL supply </br>
Milestones | 0.1% for every 1MM Monthly Active Spenders (MAS)* </br> (Milestones unlock over discrete measurement periods, each milestone is measured as the median MAS in a given period) </br> *Defined as number of distinct Kin payment sources in the last 30 days
Schedule | Period 1: Time of signing to Jan 7, 2021 </br> Subsequent periods: Quarterly (Jan 8 - April 7, April 8 - July 7, etc.) through 24 months post signing
Lockup | Tokens earned in period 1 and period 2 are locked until June 1, 2021 
Notes | - All milestones are subject to review by the Solana Foundation board </br> - MAS must transact on the Solana blockchain to be counted
 
This grant would go to the Kin Foundation as the steward of the Reserves for the Kin Ecosystem. We recommend that the Kin Foundation incorporate the allocation of SOL tokens into its annual budgeting process that it undertakes for the management of the Kin Reserves. We also recommend that the Kin Foundation makes a public disclosure 30 days in advance of any distribution or sale of SOL tokens. 

## Recommended Next Steps
We at Kik Interactive Inc. have been working with the Solana team to stress test their technology. Through this process we have found that not only is the Solana infrastructure a strong fit for Kin, the Solana team is capable and well positioned to support Kin as it continues to scale. 

It is our recommendation that the Kin Foundation agrees to the grant proposed by the Solana Foundation and that the Kin Ecosystem begins working with the Solana team on a migration plan to move off of the Kin Blockchain and on to the Solana blockchain. 
