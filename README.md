# Proof of Authority Development Blockchain

![Blockchain Technology](Images/istockphoto.jpg)

The first step as a blockchain enthusiast is to set up a private testnet that you and your colleagues or team members 
can use to explore potentials for blockchain.

This project aims to to set up a testnet blockchain as a sandbox blockchaain to try explore what this technology can bring to fruition.

In order to set up a testnet, We will need to use the following tools and utilities:

* Puppeth, to generate your genesis block.

* Geth, a command-line tool, to create keys, initialize nodes, and connect the nodes together.

* The Clique Proof of Authority algorithm.

* MyCrypto Tool, an open-source, client-side tool for generating ether wallets and send/receive test Coins/tokens.


Be sure to include any preliminary setup information, such as installing dependencies and environment configuration.
* Write instructions on how to use the chain for the rest of your team.

## Pre Requisite Installations


## Setup the custom out-of-the-box blockchain

### Creating network nodes

* Using commandline interface of Go Ethereum tool (geth) we will create two nodes with a separate `datadir` for each using `geth`., say node1 and node 2 in our custome test network. This step will create the address of the keys for these nodes and in each of the node directories a key store file gets created. We will use this keystore file to access our Wallet on MyCrypto.

![Node Creation](Images/configuring_new_nodes.PNG)


### Creating Genesis Block

* Create a Genesis block using puppeth tool which is bundled along with geth in Go Ethereum tool.
* Puppeth tool helps to maintain and install various helper tools for managing and deploying your private blockchain. 
** Running puppeth: Open a Terminal/Command shell and type ./puppeth 
** Run `puppeth`, name your network, and select the option to configure a new genesis block.
** The first thing it’ll ask for is the network name. This is useful for identifying various blockchains if you’re running several on your local machine. We’ll use “poatestnet” here. 

![Puppeth](Images/puppeth.PNG)

** We will use Proof of Authority as the Concensus Algorithm which allows only specific address to mine /produce a block on the network. 
** Paste both account addresses (node addresses) from the first step one at a time into the list of accounts to seal.
** Paste them again in the list of accounts to pre-fund. There are no block rewards in PoA, so you'll need to pre-fund.
** You can choose `no` for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei. This keeps the genesis cleaner.
** Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" option.
** Export genesis configurations. This will fail to create two of the files, but you only need `poatestnet.json`.
* You can delete the `poatestnet-harmony.json` file.

![Genesis Block](Images/configuring_new_network.PNG)

![Genesis Block](Images/configuring_new_network_2.PNG)

### Initializing and configuring the nodes to mine or produce new blocks

* Initialize each node with the new `networkname.json` with `geth`.
* Run the first node, unlock the account, enable mining, and the RPC flag. Only one node needs RPC enabled.
* Set a different peer port for the second node and use the first node's `enode` address as the `bootnode` flag.
* Be sure to unlock the account and enable mining on the second node!
* You should now see both nodes producing new blocks

![Initializing Nodes](Images/initializing_nodes.PNG)

## Send Test transactions.

Using MyCrypto which is an open-source, client-side tool for generating ether wallets and interacting with the blockchain for development purpose, 
we will connect our local blockchain and import the pre-funded wallets. Mycrypto registers the address enabling us to send and recieve transactions or cryto currencies, just like transacting with real currencies on Ethereum network.
* open  Mycrypto tool and connect to the newly created test network
* Use the MyCrypto GUI wallet to connect to the node with the exposed RPC port.
* You will need to use a custom network, and include the chain ID, and use ETH as the currency.

![custom-node](Images/custom_network.PNG)

* Once the custom node is created on MyCrypto, select the keystore file option on the home page of crypto tool. Import the keystore file from the `node1/keystore` directory into MyCrypto. This will import the private key.

![custom-node](Images/keystore.PNG)

* the account balance will show a large number of tokens which are prefunded into the acccount when creating the Genesis block and configuring the nodes.
* select the Send Ether & Tokens option on the top menu which will open up the transaction initiation page as shown below
* Celebrate, you just created a blockchain and sent a transaction!

![Initiate Transaction](Images/initiate_tx.PNG)

*Enter the number of tokens you want to send to the second node we created in our network and the node address and then submit the transaction
* Send a transaction from the `node1` account to the `node2` account.

![send Transaction](Images/tx_from_node1_to_node2.PNG)

* As both Node11 and node2 in our POATestnet are configured to mine the blocks, The transaction will be confirmed and a transaction hash will be shared once it is mined. 
* Copy the transaction hash and paste it into the "TX Status" section of the app, or click "TX Status" in the popup.

![Confirm Transaction](Images/tx_success.PNG)

### Remember, *never* share your mainnet private keys! This is a testnet, so coins have no value here!

---
