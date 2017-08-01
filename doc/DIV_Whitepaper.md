> ![](https://raw.githubusercontent.com/steempunks/div/master/assets/div_logo.svg.png) 
> # The DIV Network
> ### *White Paper*
> #### Monetising Governance, Infrastructure and Content 
> ------------ for ------------
> #### Decentralised Distributed Social Networks
> ###### *Loki Verloren, July-August 2017*

# Abstract

DIV is a multi-tier Byzantine Fault Tolerant Database system designed to engage users, via monetisation incentives, in every aspect of the system, from open self-governance of code, curation, content creation, content hosting, search services, archiving, validation, query services, short and long messaging.

It is intended to be easily extensible in the future to expand to include classified advertising, cryptocurrency exchange, custom databases from very large to small and extreme low latency for multiplayer gaming; for privacy services, and whatever else the community that grows out of it decides it wants to add.

# Contents

<!-- TOC -->

- [Abstract](#abstract)
- [Contents](#contents)
- [Introduction](#introduction)
  - [The "Inflation Tax" Solution](#the-inflation-tax-solution)
- [Core Principles of DIV](#core-principles-of-div)
  - [Self Governed and Self Hosted](#self-governed-and-self-hosted)
  - [About the name](#about-the-name)
- [Overall Architecture of DIV](#overall-architecture-of-div)
  - [Database Services](#database-services)
  - [Application Services](#application-services)
- [The Registry](#the-registry)
  - [Linked External Accounts](#linked-external-accounts)
    - [Mandatory Proof of Control](#mandatory-proof-of-control)
- [The Refractory Token Ledger](#the-refractory-token-ledger)
  - [Activity Driven Issuance](#activity-driven-issuance)
  - [Liquid Tokens and Stake Contracts](#liquid-tokens-and-stake-contracts)
  - [Stake liquidity Restrictions](#stake-liquidity-restrictions)
  - [Change Operations to pay Interest on Stake](#change-operations-to-pay-interest-on-stake)
  - [Rewards Pool Split](#rewards-pool-split)
- [Reward Pool Voting Systems](#reward-pool-voting-systems)
  - [The Forum](#the-forum)
    - [Self-voting and Curator/Creator Split](#self-voting-and-curatorcreator-split)
    - [Automatic Equilibriation of user activity to match market value of tokens](#automatic-equilibriation-of-user-activity-to-match-market-value-of-tokens)
- [Messaging](#messaging)
- [Database Code Repository](#database-code-repository)
  - [Voting rules](#voting-rules)
- [Interface Code Repository](#interface-code-repository)
- [Structure of Validator, Replicator and Archivist nodes](#structure-of-validator-replicator-and-archivist-nodes)

<!-- /TOC -->

# Introduction

> *Before going any further, I just want to stress that no claims of fitness to purpose belong in a thesis such as this. As such, I will strive to use language befitting the practical impossibility of a theory being 100% correct before the theory is proven in implementation and practice.*

Since the appearance of Steem in the "Blockchain space", there has also been a number of related and competing systems emerging such as Yours.Network, Synereo, LBRY and most recently Ark and Alexandria.

The central goal of these systems is to stimulate the engagement of users in the production of content and monetising the content according to the subjective evaluation of peers.

Steem, the first, and by far most successful of these platforms, fails to deliver in some critical areas promised in its White Paper, specifically:

* in flattening the distribution curve of tokens in order to produce "fair" distribution of the new tokens
* the lack of search facilities
* the lack of user created affinity and operational groups
* a single reward scheme and content format that greatly diminishes its' potential for wider appeal
* the back end being monolithic, graph based only, and lacking a pruning and garbage collection severely limits scalability

The competing systems tend to address one or another of these, but being so narrow versus the relative breadth of Steem's general utility, none are likely to make significant inroads towards the goal of mass adoption, and not solve the bigger problem of isolated islands of users and the complication of many different tokens and wallets, in comparison.

## The "Inflation Tax" Solution

However, there is no doubt that the "Inflation Tax" model from Steem, of how to fund the incentives for users to join and participate in the network, by distributing a portion to both curator/creators, and to the validators, is the correct and effective distribution model, for the simple reason it allows the elimination of data heavy micro-payment schemes. It also potentially opens up the potential to reward directly for development.

These costs can be calculated in temporary, "virtual operations", in a deterministic manner based on data that is certified and replicated to all validator nodes, and thus reducing the size of the ledger without sacrificing the benefit of micropayment incentives.

No other platform, to my knowledge, uses this. DIV will use this scheme, albeit with a more dynamic issuance rate that targets a lower, flat interest charge hidden in the expansion of supply, and as a means to modulate activity to fit the rewards, maintaining effective pay rates for all contributors.

DIV is primarily aiming to supersede Steem, by omitting its most egregious flaws, and adding the elements that it needs in order to be both scalable and elastic, by monetising all relevant infrastructure, including the service of web based interfaces, search engines, content hosting, and hosting of the codebase and documentation in a monetisable structure that eliminates the inertia of Steem's governance system and the Prisoner's dilemma in the Witness election, and in the forum voting system.

# Core Principles of DIV

Key guiding principles are

* that there should be no outside party to the userbase with direct influence
* that every service to the network is rewarded
* that from the beginning of the network going live, it is a fully self contained system that is resilient to every type of failure in every aspect, not depending on or vulnerable to any outside influence
* that governance be *both* stake *and* merit based

## Self Governed and Self Hosted

By staging the development process into logical sequence, the first stage is to implement a wrapper around a git code repository, of the code itself, using a preliminary database replication protocol, and a NoSQL database backend, with a simplified posting CLI to upload changes and additions, and a basic browser that allows users to vote on submitted changes, then compute an appropriate reward scheme with a basic token ledger, the development process will be gamified, and even this document will become a subject of the development rewards system.

Furthermore, it will be designed so that the build itself is automated, and a special trigger event, which mirrors Steem's User Activated Hard Forks, but set by a voting scheme, will trigger rewards payouts, and automatically build the nee code modules and commence their operation. 

It is intended that simply running nodes should not be excessively technically or hardware capacity demanding. The code should take care of this and the rewards for development this also the biggest in the platform, ideally over time increasingly elusive because of driving the highest code quality and design innovations in the industry.

The theory is that most "blockchains" have quickly cobbled together code, just enough to function and attract "investors (very cynically), and tend to not change as fast as the lessons learned in operation could drive. DIV will therefore start from this base and at first will just be a game for coders, designers documenters and architects. Its' structure and eventual token model will be based upon the consideration of frequent, small updates being both fixes and improvements. Even the rewards scheme itself is a valid subject for code change, of course.

Steem and Dash have the distinction of being the most rapidly changing codebases in the "blockchain space", and DIV will take this a step further, by centering the funds distribution around funding development, and in doing so, hopefully, draw the greatest pool of talent to compete for the biggest share of the rewards. In doing this, ensure that the platform stays permanently ahead of the competition and even starve them of developers by paying better.

## About the name

On a more trivial note, addressing the question of why is it called "DIV", there is many aspects to the answer, but primarily it is to emphasize the aspect of all users having a share in the rewards pool, and a consensus level enforced right to a commensurate decision making power therefrom.

Even more trivially, `div.` is a mathematical term for divergence, `Div.` means "Divine", in several types of American and British street and prison slang, it means mental patient, lowly worker, crazy or retarded person. 

I originally chose it based on the colloquialism "divvy", meaning sharing out a pool of assets according to merit as agreed by a group, except, of course, with an impartial, automated recording of labor and the validation of this labor both automatically and through human judgement.

Completely irrelevant is that DIV is 504 in roman numerals, which is the HTTP error code for timeout error.

# Overall Architecture of DIV

DIV splits roles into multiple tiers with differing levels of frequency of activity, versus comprehensiveness of storage in the database, as well as application databases for tye various functions.

The former certifies and enforces the rules for each of the latter, and the application databases are all isolated from each other and use merkle tree hash references to link, such as payments for posts, use identifiers in all tied to the registry, and whatever relevant dependencies an application database requires.

## Database Services

* **Validators** have the most time critical role in rapidly assessing, confirming and propagating new transactions, they are the Write Side of the back end for clients.
* **Replicators** distribute the newest data and maintain 3 months of data, and are paid to respond to queries to provide results for user's client applications to cover the great majority of activity on the backend on the Read Side.
* **Archivists** specialise in storing a complete historical archive and answering queries passed on by Replicators when the query falls outside of the 3 month period. This is much less frequent, but per operation far more expensive, as is the infrastructure required.

> By breaking the levels of service into these three tiers, latency can be minimised where it is critical, and where completeness is required, it can be provided for, at significantly higher latency, where the client needs complete data rather than fast answers.

## Application Services

This includes the six initial and essential databases systems for DIV:

1. [The Registry](#the-registry)
2. [Refractory Token Ledger](#refratory-token-ledger)
3. [The Forum](#the-forum)
4. [Messaging](#messaging)
5. [Database Code Repository](#database-code-repository)
6. [Interface Code Repository](#interface-code-repository)

A key deficiency of Steem is the lack of accessibility and participation in governance, of users to the Database and Interface codebases, the complete lack of an integrated short and long form, transient messaging system, it only implements a Forum, and it does it within a large monolithic database. 

The maxim about hammers and nails is relevant here, though to be generous, the problem of mingled concerns during early stages of new technologies is almost an ironclad rule, of the inevitable errorsin transition.

Good system architectures isolate concerns and do not tangle unrelated data together in any way. The Model Viewer Control principle is applied throughout DIV, to both simplify code, as well as eliminate unintentional dependencies. 

All of these data stores exist within distinct database instances within the node, which minimises the amount of indexing overhead required for each. 

Merkle trees are used where the data in one database relates to another, such as the Registry being referred to by all others (this is the user registry), and the Forum and Code Repositories are referred to by the ledger when the votes stored in these databases results in a claim for a payout from the pool of new tokens.

With the exception of Messaging, these 6 components are governed and regulated by the Database Services. 

The messaging system has a more fluid architecture which is peer to peer and does not include monetisation, but instead simply has rules about transaction rates per account, propagation patterns, caching patterns, that are designed to optimise for latency and minimising on redundancy beyond necessary to ensure successful delivery of messages. 

All accounts must run one or more nodes to pay for their messaging service, though they do not have to be always online. The caching and delivery strategy assumes intermittency and accounts for it with redundancy.

# The Registry

At the centre of all cryptographically secured, distributed database systems, are cryptographic accounts. The registry is a simple table containing usernames, and the public keys that prove authority of the user to perform operations using the account.

## Linked External Accounts

The Registry also will have the infrastructure in protocol and data types enabled to allow in the future, automated control verifications for external, non-cryptographically secured accounts, such as Facebook, Reddit, Twitter, and others, as well as the more direct and easier to verify cryptographic accounts, whose addition and amendments by account holders can be directly signed using the public keys of the cryptographic accounts.

### Mandatory Proof of Control

This proof of ownership is necessary in order to prevent the spammy registration of many attached accounts, as the cost of proving ownership eliminates the ability to arbitrarily claim to control an arbitrary number of accounts that the user does not in fact have any control of.

# The Refractory Token Ledger

Instead of using the traditional double entry ledger accounting system, the primary currency in DIV functions more like a property registry. 

There is multiple reasons why this has been chosen, the main one being 

1. that the growth of the database is highly predictable, because the number of tokens only expands up to a maximum level, but it does not expand without activity driving it,
2. no more than 3-5 past transactions are required for 100% confidence a double spend is not occurring, whereas splitting double ledger tokens endlessly expand in size, unrelated to the rate of issuance, but driven by activity. 

RTL merges these concerns to eliminate the endlessly branching tree of splits, and then allows arbitrary pruning strategies to optimise the database.

Further, the burden of replicators is reduced, who also proxy for write requests for clients, who can then pre-process in the case of needing to take a token out of cold storage on archivist databases, *before* forwarding the transaction to the validator.

Of course this will mean jitter in transaction latency from time to time, but optimises replicators and validators for fast responses for the majority of transactions and queries.

When tokens are issued, the amount issued is composed of a collection of unique serialised tokens with a specific power of two denomination, a piece of data that never needs to be repeated, and can then be referred to by a hash instead. 

The number of new tokens increases in sum of denominations, at a moving average target of 5%, and thus generally will mean the database of tokens will grow at about 40% per year, varying according to the variance of activity, based on the average number of tokens falling at around 8 "bits", giving a typical precision on average of 16bits, more than enough for most.
s
After all, it tends to be that large priced commodities are rounded for human convenience. In terms of data storage requirements this means a big price and a little price take about the same amount of storage. 

Thus, if a token is not spent at least every 3 months, it can be pruned from validator and replicator databases, and stored only in Archivist databases.

In general this will mean that change will not often be required, however, it will be required, and this is one of the purposes of having the deposit contract, and provides an interest payment to depositors for their service.

## Activity Driven Issuance

There is in fact no true economic justification for issuance of new tokens in any monetary system at all. Whether supply is growing, shrinking, or unchanging, makes no difference in the long run, but in the short term, zero effective new tokens makes economic calculation simpler, because it is unchanging against the background of every other commodity in the economy. Increasing supply benefits the recipients of new tokens, decreasing it benefits the holders of deposits. The RTL will apply both depending on the demand for services.

However, in order to use issuance as a way to monetise especially public infrastructure, the price of these services is hidden in the background of a slowly declining value, steadily increasing supply of tokens. Holders of the tokens are implicitly funding the network as shown in the decline in the value of their assets.

Furthermore, in the RTL, unlike double entry ledgers, but rather like a commodity coin currency, issuance is necessary, even if the total pool of denomination sum is static, as the economy grows, large tokens still must be split to allow the increasing valueof the tokens in exchange.

Rather than precisely model coins, the cost of the tokens is the same whether new smaller tokens are issued, or if old ones are split, revoked and a divided set of tokens is issued. New tokens are simpler to implement and avoid branching trees of provenance.

> Thus the subject of the 'correct rate of issue' is a constant source of debate for monetarists, who argue over entirely arbitrary ratios, usually percentages of compounding, an flat rates.

The Refractory Token Ledger has a built-in mechanism by which a rate of issuance at the baseline can be pegged to the relative rate at which the tokens are issued - because of the need to change the larger tokens into smaller ones, an ongoing background task of reshuffling large liquid tokens with smaller, locked deposit tokens, allows a mechanism for paying interest to holders of deposits, which tends to track the total amount of liquidity needed to facilitate ongoing trade, at the same time as directly, randomly, rewarding depositors.

It will be explained later in the section about content and hosting monetisation, how the use of a moving average will regulate the issuance of new tokens to fund the content production incentivisation also, in a way that does not create an artificial flat issuance rate, but rather one that drops the relative share issued during busy times, and raises it during quiet times, acting as a contrary influence against attempts to game the issuance system and the inevitable 'peak hour' and 'graveyard shift' that results. 

Like Off-Peak tarrifs for energy and telecoms services, the value in busy times is decreased, and increased during quiet times, encouraging a smoother bandwidth utilisation in the network. The price will naturally equilibriate because when liquidity rises, the supply rises, when liquidity falls, the supply falls. All else being equal, this will mean that excess activity will 'punish' by a drop off in value and insufficient activity will incentivise an increase in activity via a rise in value of the liquid tokens.

## Liquid Tokens and Stake Contracts

As exists in the Steem Ledger, except contracted to only include one of each type, and no hedging contract (as it is a design error to place this in the ledger). This also simplifies the process of calculating rewards, as Steem requires a base currency called VESTS, to implement both Steem and Steem Backed Dollars, and Steem is used to implement the Steem Power contract.

The liquid token is called DIV Coins or DIVC as a ticker, and the Illiquid Vote Power instrument is called DIV Stakes or DIVS. Coins can be transferred freely to any other account at zero cost (as the cost of running the network is accounted for in the payments to the Validators). Steem has therefore in fact 2 different currencies, whereas DIV will only have one, which greatly simplifies computation of rewards for the various network functions.

## Stake liquidity Restrictions

In order to restrict the rate at which users can reverse their staking of Coins into Stake contracts, deposit is instant, but withdrawal can only take place at a rate of 1% per day, paid daily.

This also eliminates the advantage that may be gained by users seeking to draw down when everyone else is buying in. Liquidity is very important in marketplaces, and daily payments on ledgers is standard in the banking industry. Weekly payouts cause a cyclic price fluctuation that will flatten in the case of a daily payout, due to trade opportunities being able to be seized by any holder of liquid tokens.

## Change Operations to pay Interest on Stake

Since it may sometimes happen that a user's collection of tokens does not have exact change to allow a transaction, instead, Validators preemptively break the larger tokens in smaller accounts with the smaller tokens of larger accounts. It is very simple to establish how to redistribute the different sized tokens, because if there is one in each progressive power of two denomination, any payment can be made. 

As tokens automatically exchanged between accounts in order to ensure a minimum capability to spend any amount that can be denominated in the total and down to the smallest token in circulation require an available pool that is not in circulation, it is part of the purpose of DIVS to enable this, and the amount of a change operation, divided by 100, is paid in new tokens to holders whose stake allows this maintenance of adequate change for any amount of payment without the user needing to concern themselves with how the Refractory token mechanism, while providing a reason to pay interest to stake, and determining how much it needs to be done (driven by the amount of money being transferred around.

Note that these operations are not just randomly chosen, stake in accounts to be used to provide change, must have no incoming or outgoing user initiated transfers between each other, so users can't deliberately spend in order to win interest payments. On average every user will end up earning about the same thing over time, but in the short term the variance can be very wide. However, the bigger one's DIVS pool, the more likely to get a payment, rewarding the use of stake.

The providers of change also are selected by a strict criteria that there can be zero transfers, or votes in the various content monetisation databases, between the change provider and the recipient. The change operation is marked as enacted as one of the delegated responsibilities of Validators, and thus via the Validator Election process, a proper chain of authority is created. These operations do not count as business between two accounts.

There is inevitably accounts which never make any interactions with each other, and by choosing such distant nodes in the financial network graph, users can be assured that this interest payment mechanism cannot be gamed with spammy, intentionally change requiring operations. Instead, after an account makes a payment, the Validator examines their pool of DIVC to ensure that it has at least 1 of every denomination from smallest to largest, and if it finds holes in the supply, it makes a change operation that is invisible to the account needing the change, and appears as an interest payment of 1% of the reqired change quantity, to the DIVS of the change provider. 

## Rewards Pool Split

The rewards pool splits so that 50% is divided amongst the three [Database Services](#database-services) pools, and likewise, in [the Forum](#the-forum), and [Interface](#interface-code-repository) and [Database](#database-code-repository) Code Repositories. The Messaging component does not have a reward split, because it is highly optimised and essentially builds in the cost of provision to the direct operation of client/peer nodes in the messaging network.

It may seem like the Database Services get a lot of the share, but, being a multivaried set of three service types, with basically equal value to the network, and equal opportunity to participate in it, for the technically minded, there is very good reason to give the lions share of rewards to those who are producing the network. This is a serious flaw in the distribution of Steem, and is only somewhat ameliorated by the recognition of its' value by users of the forum.

Replicators also serve web-based interfaces via the ZeroTier mesh, and Archivists provide query services for older data and secondary, more advanced search systems.

The forum only gets 1/6th of the allocated new resources, because otherwise it would be a drag on the value of the token, with most of its value going outside the network and not being reinvested into improving infrastructure and the competitiveness of each individuals role in the different sections of the system.

In fact, there is very good reason for this structure, and it is cognate to the software industry as a whole. The utility of the software is more important to users than being paid for it. A smaller share means tighter competition, and more incentive to move into more lucrative development and systems administration sides, and more generally, closes most of the loops that would otherwise lead funds to end up largely being sold off at exchanges and cutting *everyone's* effective pay rate. The most likely place for this leaking out to happen is [the Forum](#the-forum).

# Reward Pool Voting Systems

These are the Forum and the Code Repositories. The voting systems in both operate differently, as their purposes are different, but in terms of the rewards pool, they split evenly. Thus, the Forum, the Database and the Interface pools have equal split of the Reward Pool Voting systems. 

These are subjective, and aim to be meritocratic, the latter two are more based on merit than opinion, however, because at the end of the day, the code has to work, and loses votes if it fails to function.

## The Forum

This is the most visible part, and is where the primary portion of new tokens are distributed to. The format is basically the same as Steem - the fundamental unit of publication is a text formatted document, in Markdown (DIV will use strict Markdown code, and provide a layout engine along similar lines to stackedit and quip as well as editors derived from these codebases). 

In the initial rollout, there will not be the peer to peer hosting network built yet, and regular urls will be parsed to pull assets into the output of the interface. However, the provision of full internally provided hosting within the network is part of the version 1.0 featureset, and is a top priority to implement.

### Self-voting and Curator/Creator Split

Forum posts cannot be voted upon directly by users themselves, but to compensate for this, each post is itself a vote upon itself, and thus the curation reward for any post is always greatest for the user. This is balanced by the increase of curation share to 50%, as curators compose a much larger number of individuals than the account operator, and the incentive must be substantial enough to encourage engagement in the process of discovering quality content.

### Automatic Equilibriation of user activity to match market value of tokens

As mentioned in [Refractory Token Ledger](#refractory-token-ledger), in DIV, there is no prescribed interest rate, only a rate target of 5%, around which issuance rates will move up and down in order to average to this target over the period of a month or so. Thus, if posting activity thins out, rewards will escalate beyond 5% in order to induce return of users to reap the growing rewards, and when the amount of activity rises, the rewards will naturally be distributed thinner, but also be contracted in order to bring activity down to sustainable level.

There is a natural n-Person Prisoner's Dilemma built into the rewards issuance distribution in Steem, in that when prices go up, user activity goes up, and it does not naturally come back down by itself, but instead by the increased rate of selling of Steem on the market by authors, and then, in a lagging manner, then downregulates user activity. Instead of depending on the market to do this, and the peaky curve that this naturally creates in the price, the reward algorithm naturally adjusts the equilibrium up and down in order to pre-empt the slowdown in a peak congested period of posting, by thinning rewards faster, the faster user activity rises, and vice versa, increasing rewards faster than the loss of activity is causing.

This avoids the problem of excessive levels of exuberance and depression in the community, which is deleterious to user retention, the same way as an excessively sharp distribution of prize payouts in a gambling system exhausts the more marginal players. (Note that this is essentially a gambling system, this is why it is so compelling to users, far more than the thrill of getting 100 likes, is getting $100 worth of tokens).

# Messaging

# Database Code Repository

In fact, this is the real centrum of the governance of the DIV platform. Alongside the subordinate, though equally important [Interface Code Repository](#interface-code-repository), this is where the legislation of the Government of DIV occurs. 

Posts to this database are in some ways like [the Forum](#the-forum), however, there is not the same endless creation of new root posts based on an account, but instead, a root post, being the README.md document, and from this branches a tree of code, a mirror image documentation branch. It is also possible for many lateral replications of the root (master), which can then have additions made that can be merged back to the master later on.

Basically, a github repository, except that developers involved can vote upon whether modifications and additions will be added, and when there is parallel branches, a request to merge can be made, and if it passes a vote, the code is merged to the main branch, and where conflicts arise, the Master remains active until a proposed consolidation is voted upon.

## Voting rules

Of course, this is not a forum for general consumption. Thus, while stake is important to calculating votes, this stake is multiplied by a reputation score that is built upon the historical record of each account voting correctly for changes that gain 4/5ths assent (by ratio), and the more that a user successfully does this, the weight of their votes increases through a natural process of discovery of merit in technical skills. 

Thus, unlike the entirely arbitrary and social system of voting in the Forum, the Code Repositories are all about discovering the best coders, designers and architects, and rewarding them both in increased power to make decisions, as well as a monetary reward.

# Interface Code Repository

# Structure of Validator, Replicator and Archivist nodes