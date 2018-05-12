# learnblockchain

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# Introduction

## The heart of Blockchain, the Distributed Ledger: https://youtu.be/Cqk7PN8f8gM
                           
## How does blockchain work? https://youtu.be/lD9KAnkZUjU 

## Blockchain Car Lease demo: https://youtu.be/IgNfoQQ5Reg

## Blockchain Use Cases: https://www.ibm.com/blockchain/use-cases/
                                                     
<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# Hyperledger Fabric   

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

<img src="https://farm1.staticflickr.com/960/41055079635_d00c82c7dd_z.jpg" width="640" height="203" alt="fabric">

https://www.hyperledger.org/projects/fabric

[Hyperledger Fabric Documentation](https://hyperledger-fabric.readthedocs.io/en/release/)

Hyperledger, an open source collaborative effort to advance cross-industry blockchain technologies, 
is hosted by The Linux Foundation®. 

Deployed in Docker images.

<img src="https://farm5.staticflickr.com/4494/37926120211_b7dddb090d_o.png" width="682" height="423" alt="Hyperledger Services">
<p> Permissioned<p> 

https://medium.com/@robertgreenfieldiv/hyperledger-blockchain-for-a-web-2-0-architecture-6d3c83818eb1
<p>

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# Hyperledger Composer

<img src="https://farm1.staticflickr.com/968/27085403057_c8a2ccd0cc_z.jpg" width="640" height="202" alt="composer">

https://www.hyperledger.org/projects/composer

[Composer Playground](https://composer-playground.mybluemix.net/login)

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

<img src="https://www.ibm.com/developerworks/cloud/library/cl-deploy-sample-application-ibm-blockchain-platform/image001.jpg">

# [IBM Blockchain Platform Service](https://console.bluemix.net/catalog/services/blockchain)

[IBM Blockchain Platform](https://console.bluemix.net/developer/blockchain/dashboard)

[Launch a basic IBM Blockchain network on the IBM Container Service's free plan](https://ibm-blockchain.github.io)

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband"> 
  


# Appendix

## Channels
A Hyperledger Fabric channel is a private “subnet” of communication between two or more specific network members, for the purpose of conducting private and confidential transactions. 

## The Ledger and the State Database

There are two place which "store" data in Hyperledger Fabric:
### The ledger is the actual "blockchain". 
It is a file-based ledger which stores serialized blocks. Each block has one or more transactions. <br>
Each transaction contains a read-write set which modifies one or more key/value pairs. <br>
The ledger is the definitive source of data and is immutable.

### The state database holds the last known committed value for any given key. 
It is populated when each peer validates and commits a transaction. <br>
The state database can always be rebuilt from re-processing the ledger. <br>
There are currently two options for the state database: an embedded LevelDB or an external CouchDB.
<p>
As an aside, if you are familiar with Hyperledger Fabric channels, there is a separate ledger for each channel as well.
<p>
When we query from where do we retrieve data?  1) from the blockchain chain or 2) from state db? <p>.
If it is from state db how can it retrieve a specific key because you mentioned "state database holds the last known committed value for any given key" <p> 
Queries or GetState in chaincode return data from the state db. They will only return the last value for a key. <p>
If you want to get the entire history for a key, you need to enable the historical database in the configuration of your peer 

### Chaincode.
Like <b>Stored Procedures</b> in a traditional database, handles business logic. http://hyperledger-fabric.readthedocs.io/en/release/chaincode4ade.htm

<img src="https://farm5.staticflickr.com/4523/38243385192_43d682cf94_o.png" width="910" height="483" alt="Hyperledger helloworld 2">
<p>  
Chaincode is a piece of code that is written in one of the supported languages such as Go or Java. It is installed and instantiated through an SDK or CLI onto a network of Hyperledger Fabric peer nodes, enabling interaction with that network's shared ledger. 
  
 ### [Consensus](https://www.zurich.ibm.com/blockchain/) 
 <p>Today, consensus protocols exist in many variations, but all of them need a majority or even a qualified majority (such as 2/3 of the nodes) to be correct, whereas the remaining ones could fail, misbehave, or even act adversarially against finding consensus.

Starting with the celebrated protocols for Byzantine Agreement established in 1982, consensus protocols have found widespread applications for keeping distributed systems healty and making cloud platforms operate continuously. </p> 

<b>A blockchain is a decentralized virtual ledger for recording transactions <b>without central authority </b> through a distributed cryptographic protocol. It is made up of three technologies 

1. cryptographic algorithms, 
1. a distributed protocol, 
1. and replicated data 
<p>
which combined provide a trustworthy service to a group of nodes that do not fully trust each other. 
<p>
</i>
<p>
Source: https://www.zurich.ibm.com/dccl/papers/cachin_dccl.pdf


# The Blockchain Distributed Ledger  
  
<img src="https://www.ibm.com/blogs/internet-of-things/wp-content/uploads/2017/05/2-1.jpg">
<p> 
A distributed ledger is a type of database that is shared, replicated, and synchronized among the members of a network. The distributed ledger records the transactions, such as the exchange of assets or data, among the participants in the network.

Participants in the network govern and agree by consensus on the updates to the records in the ledger. No central, third-party mediator, such as a financial institution or clearinghouse, is involved.

Every record in the distributed ledger has a timestamp and unique crytographic signature, thus making the ledger an auditable history of all transactions in the network. One implementation of distributed ledger technology is the open source Hyperledger Fabric blockchain.

https://console.bluemix.net/docs/services/blockchain/index.html#ibm-blockchain-platform

Hyperledger, 1,000 transactions/second
