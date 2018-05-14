
# Introduction

This code pattern is for developers looking to start building Blockchain applications with Hyperledger Composer. When the reader has completed this code pattern, they will understand how to:

* Create a business network using Hyperledge Composer and recording transactions on the Blockchain ledger
* Deploying the network to an instance of Hyperledger Fabric
* Building an Angular app to interact with the network through REST API


# Architecture Flow

<p align="center">
  <img width="650" height="200" src="images/arch.png">
  
  <img src="https://github.com/LennartFr/learnblockchain/img/arch.png">  
</p>

1. The administrator interacts with Decentralized Energy UI comprising of Angular framework
2. The application processes user requests to the network through a REST API.
3. Implements requests to the Blockchain state database on Hyperledger Fabric v1
4. The REST API is used to retrieve the state of the database
5. The Angular framework gets the data through GET calls to the REST API

# Included Components

* Hyperledger Composer https://hyperledger.github.io/composer/latest/
* Angular Framework  https://angular.io/
* Loopback

# Running the Application
Follow these steps to setup and run this code pattern. The steps are described in detail below.

## Prerequisite
- Operating Systems: Ubuntu Linux 14.04 / 16.04 LTS (both 64-bit), or Mac OS 10.12
- [Docker](https://www.docker.com/) (Version 17.03 or higher)
- [npm](https://www.npmjs.com/)  (v5.x)
- [Node](https://nodejs.org/en/) (version 8.9 or higher - note version 9 is not supported)
  * to install specific Node version you can use [nvm](https://davidwalsh.name/nvm)
- [Hyperledger Composer](https://hyperledger.github.io/composer/installing/development-tools.html)
  * to install composer cli
    `npm install -g composer-cli`
  * to install composer-rest-server
    `npm install -g composer-rest-server`
  * to install generator-hyperledger-composer
    `npm install -g generator-hyperledger-composer`

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

<img src="/img/arch.png">

<img src="/img/scrnshot.PNG">

# Steps

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

## Step 1. Clone the repo

Clone the `Decentralized-Energy-Composer code` locally. In a terminal, run:

`git clone https://github.com/IBM/Decentralized-Energy-Composer`

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

## Step 2. Setup the Hyperledger Fabric

These commands will kill and remove all running containers, and should remove all previously created Hyperledger Fabric chaincode images:

```none
docker kill $(docker ps -q)
docker rm $(docker ps -aq)
docker rmi $(docker images dev-* -q)
```

All the scripts will be in the directory `/fabric-tools`.  Start fabric and create peer admin card:

```
cd fabric-tools/
./downloadFabric.sh
./startFabric.sh
./createPeerAdminCard.sh
```
<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

## Step 3. Generate the Business Network Archive

Next generate the Business Network Archive (BNA) file from the root directory:

```
cd ../
npm install
```

The `composer archive create` command in `package.json` has created a file called `decentralized-energy-network@0.1.15.bna`.

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

## Step 4. Deploy to Fabric

Now, we are ready to deploy the business network to Hyperledger Fabric. This requires the Hyperledger Composer chaincode to be installed on the peer,then the business network archive (.bna) must be sent to the peer, and a new participant, identity, and associated card must be created to be the network administrator. Finally, the network administrator business network card must be imported for use, and the network can then be pinged to check it is responding.

First, install the business network:

```
composer network install --card PeerAdmin@hlfv1 --archiveFile decentralized-energy-network@0.1.15.bna
```

Start the business network:

```
composer network start --networkName decentralized-energy-network --networkVersion 0.1.15 --networkAdmin admin --networkAdminEnrollSecret adminpw --card PeerAdmin@hlfv1 --file networkadmin.card
```

Import the network administrator identity as a usable business network card:
```
composer card import --file networkadmin.card
```

Check that the business network has been deployed successfully, run the following command to ping the network:
```
composer network ping --card admin@decentralized-energy-network
```
<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

## Step 5. Run the Application

First, go into the `angular-app` folder and install the dependency:

```
cd ../angular-app/
npm install
```

To start the application:
```
npm start
```

The application should now be running at:
`http://localhost:4200`

<div style='border: 2px solid #f00;'>
  <img width="800" src="images/app_scrnshot.png">
</div>
</br>

The REST server to communicate with network is available here:
`http://localhost:3000/explorer/`

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

## 6. Create Participants

Once the application opens, create participants and fill in dummy data.  Create Residents, Banks and Utility Companies.

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

## 7. Execute Transactions

Execute transactions manually between Residents, Resident and Bank, and Resident and Utility Company.  After executing transactions, ensure the participants account values are updated.


At the end of your session, stop fabric:

```
cd ~/fabric-tools
./stopFabric.sh
./teardownFabric.sh
```

<img src="https://farm5.staticflickr.com/4503/37148677233_71edc5a37b_o.png" width="1041" height="53" alt="blueband">

# Appendix

## Extending Code Pattern

This application demonstrates a basic idea of a decentralized energy network using Blockchain and can be expanded in several ways:
* Adding specific permissions and participant access
* Setting up real time transactions among participants
* Integrating with IoT to read from power meter and distribute energy

## Deploy to IBM Cloud

The blockchain network can be deployed to IBM Cloud. 
You can use the [IBM Blockchain platform](https://console.bluemix.net/catalog/services/blockchain) and start for free under `Starter Membership Plan`.  Follow [these instructions](https://ibm-blockchain.github.io/platform-deployment/) to deploy the business network to IBM Blockchain platform.

To deploy the Blockchain network as kubernetes cluster follow the instructions [here](https://ibm-blockchain.github.io/setup/).  The guide walks through creating a free cluster on IBM Cloud and deploying your business network.  This will provide the IP address for the composer rest server to be used by the application.


## Additional Resources
* [Hyperledger Fabric Docs](http://hyperledger-fabric.readthedocs.io/en/latest/)
* [Hyperledger Composer Docs](https://hyperledger.github.io/composer/latest/introduction/introduction.html)

## License
[Apache 2.0](LICENSE)
