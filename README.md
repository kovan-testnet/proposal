# Kovan - Stable Ethereum Public Testnet

Kovan is a new testnet for Ethereum using Parity's Proof of Authority consensus engine, with benefits over Ropsten:

* Immune to spam attacks (as Ether supply is controlled by trusted parties)
* Consistent 4 second block time

## Resources

Connection Guide:  
https://github.com/kovan-testnet/config

Faucet Service:  
https://github.com/kovan-testnet/faucet

Blockchain Explorer:  
https://kovan.etherscan.io

Netstats:  
http://kovan-stats.parity.io

Validator Performance:  
https://kovan.etherscan.io/stat/miner?range=1&blocktype=blocks

Improvement Proposals:  
https://github.com/kovan-testnet/KIPs/issues

# Proposal

*Please note this proposal is being continually updated as the project matures*

## Abstract

The authors propose the formation of a public Proof-of-Authority (PoA) Ethereum testnet, named “Kovan”. This new testnet will be using Parity (an Ethereum client developed by Parity Technologies, FKA Ethcore) to provide a stable, secure testnet environment for Ethereum developers, due to the instability of the existing Ropsten testnet.

On 24th Feb 2017, Ropsten was under a denial-of-service attack (“spam attack”). Average block propagation time has since slowed to a crawl as a large miner has decided to deploy several zero-value high-gas transactions to spam the test network continually. The attacker’s intentions are unknown, but the result is that Ethereum developers who rely on Ropsten no longer have a stable public testing environment to deploy and test their smart contract code prior to deploying to production on the mainnet chain.

The use of Proof-of-Work (PoW) for testnets presents a fundamental game theoretical problem: the only significant economic incentive to mine on testnets using dedicated GPU resources is to launch an attack and reduce stability and the viability of the testnet (and thus hamper development for the mainnet chain).

## What is Proof-of-Authority?

Parity supports a PoA consensus engine to be used with Ethereum Virtual Machine (EVM) based chains. PoA is a replacement for PoW, which can be used for both public and private chain setups. There is no mining involved to secure the network with PoA, and relies on trusted ‘Validators’ to ensure that valid transactions are added to blocks, processed and executed by the EVM faithfully.

Because mining does not occur on our proposed public test net, malicious actors are prevented from acquiring testnet Ether, solving the spam attack that Ropsten is currently facing.

There is no difference in the way that contracts are executed compared to PoW chains, so developers can test their contracts and user interfaces before deploying to the mainnet in a more reliable and convenient environment.

More information about PoA can be found at: https://github.com/ethcore/parity/wiki/Proof-of-Authority-Chains

## Specification

A select group of trusted parties (“Consortium”) will be responsible for maintaining a cluster of Ethereum nodes running PoA to verify blocks.

### Decentralization

To ensure a sufficient degree of trust and redundancy, a minimum number of Consortium members should be recognised as being trusted members of the Ethereum/Blockchain community. Servers should not be controlled by a single entity, but run individually by the  consortium’s companies, preferably with servers located in multiple regions.

### Governance

Formal process to be confirmed. Currently using gitter for decision making. The Parity codebase (and thus Kovan) is ultiamtely controlled by Parity Technologies.

### Blockchain Configuration

* 4 second block time
* Parity [AuthorityRound PoA consensus mechanism](https://github.com/ethcore/parity/wiki/Consensus-Engines#authority-round)
* Use `--force-sealing`
* Homestead rules with possible Metropolis & beyond additions;

### Faucet Service

A secure “Faucet” service will be provided to allow for verified (non-malicious) developers to acquire testnet Ether. It is important that the distribution of testnet Ether is available but is also rate-limited, so as to be not available in large amounts to non-trusted parties (to prevent spam attacks).

The faucet will have a web-based interface, and will require some level of verification (to be determined), but could include:

* Github User Verification (OAuth)
* SMS Verification (already developed by Parity)
* Manual KYC from consortium members

It is to be determined whether or not the faucet service will require manual approval from the consortium validators, with one or more validators approving requests for testnet Ether. This could be achieved using an admin backend for approving requests optionally, with an on-chain multi-sig wallet to prevent an individual validator from ‘going rogue’.

Another approach could leverage the economic properties of the Ethereum mainnet, by automatically granting testnet Ether to users who send mainnet Ether into a specific contract (which could in turn be used to fund maintenance of the Kovan testnet). This approach would grant privacy benefits to developers, whilst still creating an economic barrier to entry that prevents large amounts of testnet Ether from being accrued. 

### Blockchain Explorer

An important requirement for testnet developers is to be able to easily verify that transactions have been processed using a third party interface. The most popular blockchain explorer for Ethereum is Etherscan, which currently provides an explorer interface for both the Ethereum mainnet and Ropsten testnet. Etherscan will also provide this service and also a set of API endpoints for the Kovan testnet. 

### JSON-RPC Endpoints

Any developer, including non-consortium-members, can interact with the blockchain by running a local Parity node using a specific configuration.

Additionally, a number of public JSON-RPC endpoints will be provided for deploying Smart Contracts and interacting with the network, where developers can use “zero-wallets” for signing transactions, providing further convenience for any given dev environment - this removes the requirement of running a local node, and is useful for mobile and web-based applications.

Ideally, a scalable load-balanced service (such as Infura) should be used to ensure uptime and reliability.

### Deployment

It is critical that validators have correctly-configured PoA validation nodes running in reliable and redundant way. 
Various deployment options will be provided to validators:

* Docker Images (TBC)
* Manual Configuration/Setup Documentation

## Consortium Members and Roles

* Etherscan (Block Explorer Provider / PoA Validator)
* Parity Technologies (PoA Validator / Parity Client Developer)
* DigixGlobal (PoA Validator)
* Attores (PoA Validator)
* Maker / Dapphub (PoA Validator)
* OneBit / TenX (PoA Validator)
* Aurel Iancu, Prominent Miner / Contributor, Ethereum Advocate (PoA Validator)
* Melonport (PoA Validator)
* GridSingularity (PoA Validator)
* Nivaura (PoA Validator)

Additional consortium members could be added to provide increased trust and provide development resources for the Faucet service.

The listed PoA Validator entities will be (at least) responsible for maintaining validation nodes, and ideally with redundancy on other services to prevent critical failure if is in some way compromised. There will also be to-be-determined development responsibilities from these parties with regards to providing JSON RPC nodes and the Faucet service.

## Validator Addresses

* Etherscan: 0x00D6Cc1BA9cf89BD2e58009741f4F7325BAdc0ED
* Parity: 0x0010f94b296a852aaac52ea6c5ac72e03afd032d
* DigixGlobal: 0x007733a1FE69CF3f2CF989F81C7b4cAc1693387A
* Attores: 0x00427feae2419c15b89d1c21af10d1b6650a4d3d
* Maker: 0x00E6d2b931F55a3f1701c7389d592a7778897879
* TenX (OneBit): 0x4Ed9B08e6354C70fE6F8CB0411b0d3246b424d6c
* Aurel: 0x00e4a10650e5a6D6001C38ff8E64F97016a1645c
* Melonport: 0x0020ee4Be0e2027d76603cB751eE069519bA81A1
* GridSingularity: 0x00a0a24b9f0e5ec7aa4c7389b8302fd0123194de
* Nivaura: [will join in first HF]

## Advantages over the existing ropsten public testnet

Aside from solving the critical stability issue of the ongoing Ropsten “spam attack”, there are additional benefits for providing a public consortium PoA network.

* Shorter block times, allowing for more rapid deployment, testing and iteration
* Reduced overall maintenance costs (no cpu-intensive mining is required)

## Consortium Company Profiles:

The consortium will be made up of prominent companies / development studios / community members in this space.

### Parity Technologies
Gavin Wood (Founder, CTO) - gavin@parity.io  
Jutta Steiner (Co-founder, COO) jutta@parity.io   
Peter Czaban (Lead, Parity Enterprise Suite) peter@parity.io   
Björn Wagner (Head of Business Development) bjorn@parity.io   

Parity Technologies (FKA Ethcore) is the most advanced blockchain core technology provider. Our flagship product, Parity Ethereum, powers much of the Ethereum network, protecting more than $1b of Turing complete value and acutely demonstrated itself the most robust, performant Ethereum client software through single-handedly defending the network when attacked. Through its set of products, Parity provides the necessary technology to enterprises and individuals alike in the pursuit of trust-freedom.

### Etherscan
Matthew Tan (Founder, CEO) - matt@etherscan.io

EtherScan is the leading Block Explorer, Search, API and Analytics Platform for Ethereum.

### DigixGlobal
Kai Cheng, Chng (CEO) - kcchng@dgx.io  
Chris Hitchcott (Core Dev) - chris@dgx.io  

Digix provides a use case for the tokenisation and documentation of physical assets through its Proof of Asset (PoA) protocol. The PoA protocol utilises Ethereum and the InterPlanetary Files System (IPFS) to track an asset through its chain of custody. This allows for the open and public verification of an asset’s existence without a centralised database. Digix also offers an API allowing other applications to be built on top of our asset tokenisation service.

### Attores
David Moskowitz (CEO) - david@attores.com  
Gaurang Torvekar (CTO) - gaurang@attores.com  

Attores enables data and documents to be stored and shared securely utilizing Ethereum’s smart contracts and blockchain technology. The Attores Open Certificates platform (opencertificates.co) allows for the issuing of certificates on the Ethereum blockchain for trustless verification and real time auditability of the status of the certificates. Use cases include diplomas, licenses, ISO certificates and memberships in associations and societies.

### Maker / Dapphub
Rune - Rune.Kek@gmail.com  

Maker is a stablecoin platform on Ethereum that backs the dai stablecoin using a diversified portfolio of Ethereum based assets as collateral to guarantee price stability. Dai has minimal volatility against the SDR currency basket maintained by the IMF, and the holders of a special asset called MKR act as a decentralized governance body that utilizes wisdom of the crowd to manage the mbtary policy and risk of the system. Dapphub is the leading development company in the Maker community, and have created several cutting edge software tools to aid in the development of the Maker platform, including Dapple and Dappsys. 


### TenX
Toby Hoenisch (CEO) - toby@tenx.tech  
Paul Kittiwongsunthorn (COO) - paul@tenx.tech  

TenX - developer of open-source COMIT cross-blockchain interoperability protocol for instant transfer of assets across public and private blockchains. Building a decentralized banking platform where anyone can build global financial products effectively. Financial products launched on the network integrate seamlessly with other on-network products, creating an inclusive ecosystem. The first use case on COMIT is TenX - Their OneBit wallet allows you to spend blockchain assets/tokens in the real world via mobile payment, debit card and more. TenX’ mission is to “make global payments as easy and fast as sending a text message”.

### Blockchain Industries 
Iancu Aurel  (Blockchain Consultant) - aurel@ethereum.ro

Aurel Iancu is a consultant for an European Blockchain Consultancy firm based in Bucharest, Romania. Being one of the early adopters and advocates for Ethereum, in 2015, he has successfully lead the operations for building and launching a 1500+ GPU mining facility, a project which is nowadays expanding on an ongoing basis.

### Melonport
Reto Trinkler (Founder / Chairman) - rt@melonport.com  
Mona El Isa (CEO) - me@melonport.com	  
George Hallam (Head of Business Development) - george@melonport.com  

Melonport is the private company building the open-source Melon Protocol. The Melon protocol is a blockchain protocol for digital asset management built on the Ethereum platform. It enables participants to set up, manage and invest in digital asset management strategies in an open, competitive and decentralised manner.

### Nivaura
Avtar Sehra - avtar@nivaura.com

Nivaura makes debt financing for companies cheaper and faster, while ensuring full compliance through automated on-demand issuance and administration.

### GridSingularity
Ewald Hesse - ewald@gridsingularity.com 

GridSingularity is a team of energy and blockchain professionals building a decentralised energy data exchange platform which aims to revolutionise the energy generation and distribution industry.
