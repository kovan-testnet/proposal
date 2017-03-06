# “Kovan” public testnet to provide a stable environment for Ethereum Development

Singapore - Mar 6 2017 to be released 9am London Time / 5pm SGT

On 24th Feb 2017, Ethereum’s public testnet Ropsten suffered a denial a service attack (“spam attack”), resulting in Ethereum developers who rely on Ropsten to no longer have a reliable public testing environment for deploying and testing of smart contract code prior to deployment on the Ethereum mainnet.

Within 24 hours, a consortium of 10 Ethereum companies came together to organise the launch of a stable Ethereum public testnet called “Kovan”, based on the Proof of Authority (PoA) consensus engine pioneered by Parity Technologies. 

The use of Proof-of-Work (PoW) on testnets presents a fundamental game theoretical problem: the only significant economic incentive to mine on using dedicated GPU resources is to accrue a large amount of testnet Ether in order to launch “spam attacks”, which reduce stability and viability of the network in order to hamper development of applications that would later be deployed on the mainnet chain. 

The Kovan testnet solves this issue by preventing malicious actors from acquiring large amounts of Ether and providing Ether to legitimate developers via a slow-release “faucet” service controlled by the consortium members. PoA also allows for shorter and predictable block times for a more developer-friendly environment. 

Ten organisations have collaborated in order to create and maintain this new stable testnet:

* DigixGlobal - Asset Tokenisation Platform
* Etherscan - Ethereum Block Explorer
* Parity Technologies - Developer of the Parity Ethereum Client
* Attores - Smart Contracts as a Service Provider
* Maker - Stablecoin Platform
* OneBit by TenX - Real world payments with Blockchain Assets
* Blockchain Industries - Blockchain Consultants
* MelonPort - Digital Asset Management Platform
* Nivaura - Financial Instrument Issuance and Administration Technology  
* GridSingularity - Decentralized Energy Data Application Platform

Etherscan will be providing the Kovan blockchain explorer to facilitate transaction tracking and inspection at https://kovan.etherscan.io/ and a Netstats console is available at https://kovan-stats.parity.io. Additional services including public RPC endpoints will also become available in the near future, which allow developers and testers to interact with Kovan without running a local Ethereum node.

Thanks to the Kovan testnet initiative, Ethereum developers now have access to a stable public environment for testing Smart Contracts and Decentralized Applications.

Kovan is designed to aid the Ethereum development workflow as much as possible: it has a 4 second block time to minimise transaction confirmation latency, and unlike PoW networks such as Ethereum and Bitcoin, the time between blocks is extremely consistent. Furthermore, it includes EIP-98, allowing nodes to execute most transactions in parallel giving a 3-6x improvement in transaction throughput on modern processors. Future integration of “dust-protection” EIP-169 is planned, securing Kovan against “state-bloating” attacks. To ensure the smooth upgradability, it includes support for Parity’s secure blockchain-based auto-update system. 

Gavin Wood, co-founder of Ethereum and Parity Technologies (and who also coined the term Proof of Authority) explains: “after the failure of Ropsten, it is clear that we need reliable infrastructure to aid development of Ethereum dapps in an inclusive and interoperable manner. While PoA is far from our philosophical roots, I hope that in the context of a pure testnet it will nonetheless be valuable. I'm excited to be a part of this truly multilateral grassroots community effort and hope it sets us on a path to a more inclusive and decentralised Ethereum ecosystem.”

In line with the “Morden” and “Ropsten” naming convention, “Kovan” is named after a metro station in Singapore - home of Digix, Attores and TenX - where the initial proposal for the Kovan public testnet was drafted at the SGInnovate co-working space.

For information on connecting to the live Kovan testnet and using the faucet service, please read the configuration guide at: https://github.com/kovan-testnet/config, or join the gitter channel for support at: https://gitter.im/kovan-testnet
