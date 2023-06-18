Title
===================
SubQuery Expands Data Indexing Support to EOSIO

Abstract
--------------

Almost every blockchain has a need to process and query data, however everyone knows that a core weakness of blockchain data is that the processing and query performance is extremely inefficient. SubQuery is an open source platform that solves that and provides a more performant and feature-rich alternative to The Graph.

SubQuery's mission is to make decentralised data more accessible. SubQuery is your own custom open-source API between blockchain data and your dApps and tools. Our indexer works on Ethereum, Polygon, BNB, Arbitrum, Optimism, Polkadot, Substrate, Avalanche, Cosmos, Near, Flare and Algorand chains, and then provides that data for developers to use for a wide array of projects (wallets, explorers, custom chains, or any other decentralised app).

Simple Summary
--------------

We have three products:

-   An open source SDK, which includes the instructions on how any Indexer should traverse the blockchain, what data to collect, and how it should be shown to users. 

-   A Managed Service, which provides enterprise level hosting (99.9% uptime) for SubQuery projects by our team (with a generous free tier)

-   A decentralised SubQuery Network. With the testnet just finished, we are about to launch a first version of the SubQuery Network. The SubQuery Network is our effort to move towards a decentralised and tokenised network in order to ensure no single point of failure and superior performance for SubQuery. It will support EOSIO from genesis and will encourage as many participants in the process as possible.

In our view, the EOSIO ecosystem is poised for an extreme growth period and it requires tools such as SubQuery in order to thrive.

Motivation
--------------

What first brought our attention to EOSIO were customer requests asking for our indexing support for the EOS chain:\
<https://github.com/subquery/subql/issues/1799>
<https://github.com/subquery/subql/issues/1605>

Upon researching further we found we're in complete agreement with EOSIO's focus on providing a fast, efficient and highly configurable stack - SubQuery is designed to be a tool that supports this. Our goals have always been to build tools and services that accelerate the world's transition to web3 and EOSIO is a fascinating layer 1 that has attracted a large developer base.

SubQuery is an incredibly useful tool that developers can use to build dApps faster. It provides a critical level of infrastructure that developers need to access, organise, and utilise data efficiently. By supporting EOSIO, we will allow our existing customers to easily migrate over to EOSIO from other ecosystems by providing a common tool. We specialise in new layer-1 chains, and our customers generally take a cross chain approach to development.

How far along is our Project
--------------

SubQuery is an established project launched early 2021. We've been building and scaling our tool to hundreds of customers across 11 different layer 1s (Ethereum, Polygon, BNB, Optimism, Arbitrum, Substrate/Polkadot, Avalanche, Cosmos, Near, Flare and Algorand) for some time now. We have a proven product with large customers across most verticals (wallets, deFi, NFTs, gameFi, explorers) etc. You can see some examples of projects using SubQuery in our [public explorer.](https://explorer.subquery.network/)

Competitive advantages?
--------------

SubQuery is a flexible, cross-chain indexing service similar to the Graph. There are endless possibilities for the variety of data sources that can be analysed and served using SubQuery.

We build SubQuery with the following key competitive advantages in mind:

-   Faster than others. We're focusing on making SubQuery faster than other solutions with advanced indexing caches and precomputed indices saving developers time, our solution is fast to set-up, fast to manage, and fast to index. 

-   More Flexible and Feature rich. SubQuery is a scaffold for building custom APIs and we provide additional features like GraphQL subscriptions, automated historical tracking, and more.

-   Open. Customers have already extended our open source SDK to suit their own custom implementation.

-   Universal. A universal infrastructure stack bringing communities together, developers now have a tool to search, sort, filter and query any data for their app across multiple blockchains.

Additionally, we are committed to running our managed hosted service over the long term. We have made huge investments into it and have many customers relying on it. This will provide an alternative to customers that are currently threatened by the [imminent sunsetting of the Graph's hosted service](https://thegraph.com/blog/sunsetting-hosted-service).

Business Model
--------------

SubQuery's SDK is open source under the Apache 2.0 Licence. This SDK provides everything that you need to build and run an indexer for your dApp. You can see detailed instructions on how you can run [SubQuery locally in our documentation](https://academy.subquery.network/run_publish/run.html). The SubQuery Network will be open source under the same licence.

The SubQuery managed service is a hosted environment that is closed source and run privately by SubQuery. It does not have any features that customers can't do themselves and runs the same open source versions of SubQuery SDK.

Growth Strategy
--------------

We build an advanced developer tool that makes a technically challenging process easy. As a result, the sole measure of our success is the number of developers and projects in EOSIO using our tool to index data for their dApp/service. We put a lot of effort into business development, developer education, and ecosystem outreach to achieve this.

But if we don't build the best indexer tool, with unmatched features, faster performance, and higher reliability - then we will fail at onboarding developers to use our tool. That's why we focus on both BD and product development. Additionally, our Managed service solves a huge pain point with small teams that don't want to focus on reliability and uptime. We completely manage this critical infrastructure for many teams and we've become experts at it.

About our Team
--------------

Based in New Zealand, the inception of SubQuery occurred in February 2021 and since then the below core team of 4 has rapidly grown to more than 20 members spread across New Zealand, Singapore and Portugal. We're a high performing team, mostly comprised of software developers, devOps engineers, and business development staff with a track record of experience in extending our tooling to different layer 1 chains.

Sam Zou - CEO (<https://www.linkedin.com/in/sam-zou-5b8169a/>)

Entrepreneur, Investors and more than 20 years  of IT experience specialising in infrastructure and cloud service design

Ian He - CTO (<https://www.linkedin.com/in/yin-he-7a266345/>)

Blockchain Architect, Contributor of polkadot-js, Early adopter of substrate technology and won second place in the first polkadot hackathon.

James Bayly - COO (<https://www.linkedin.com/in/james-bayly/>)

Software engineer with experience creating and growing 3 startups over the past 5 years

Existing support and partnerships
--------------

Read through <https://blog.subquery.network/> for all partnership announcements.

Chains we support

-   Ethereum

-   Polygon

-   BNB Chain

-   Arbitrum

-   Optimism

-   All Substrate and Polkadot/Kusama chains

-   Avalanche

-   Cosmos (both CosmWasm and Ethermint)

-   Algorand

-   Near

-   Flare

Project Goals
-------------

This funding grant aims to help us  to build the next stage of our vision for SubQuery to become a multi-chain tool - SubQuery support encompassing EOSIO through full testing and implementation.

-   The SubQuery SDK will be open-sourced / free for the EOSIO community and (test) network agnostic

-   The SubQuery Hosted Service will be available for free for all customers on EOSIO (up to a basic level with paid enterprise level support for larger ones to cover infrastructure costs)

-   The decentralised SubQuery Network will be fully compatible with EOSIO

-   We will deliver a considerable amount of developer documentation, tutorials, and example projects that will help developers in your ecosystem build

-   Our BD teams will reach out to multiple developers in your ecosystem make themselves available for any demos or workshops

Milestones and Cost Projection
-------------

|Deliverable|Time (FTE Days)|
|:----|:----|
|Create a new data source processor for EOSIO|12|
|Define new manifest structure and update SubQuery CLI|10|
|Import and manage EOSIO ABIs|7|
|Create basic documentation for EOSIO support|5|
|Create end to end developer tutorial (written and video)|7|
|Project Management|10|
|Milestone 1 Time|53|

|Resource|Quantity (Days)|Day Rate (USD)|Cost (USD)|
|:----|:----|:----|:----|
|Engineers|41|$900|$36,900|
|Project Managers|10|$900|$9,000|
|Milestone 1 Cost (USD)| | |$45,900|

Intellectual Property
-------------

I hereby agree that this EEP is subject to this [copyright waiver](https://creativecommons.org/publicdomain/zero/1.0/) and I certify that I have all necessary rights and permissions to make this submission and to agree to such waiver.

Link to Proposal:
-------------
[https://docs.google.com/document/d/1_3g6c4Jp3RHT13KknHk5Y-J8te5nJqwzVAgEowCaRzw/edit?usp=sharing](https://docs.google.com/document/d/1_3g6c4Jp3RHT13KknHk5Y-J8te5nJqwzVAgEowCaRzw/edit?usp=sharing)
