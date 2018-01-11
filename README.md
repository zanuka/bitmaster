# Ƀitmaster

#### Explorations in Ƀitcoin :: decentralized trust networks :: the open blockchain

The purpose of this repo is to record my notes, summaries, thoughts, questions, and explorative research from **[Mastering Bitcoin 2nd Edition - Programming the Open Blockchain](https://www.safaribooksonline.com/library/view/mastering-bitcoin-2nd/9781491954379/)**, by Andreas M. Antonopoulos. The official repository for the book is [https://github.com/bitcoinbook/bitcoinbook](https://github.com/bitcoinbook/bitcoinbook).

## Intro

**What it is:**
- collection of concepts and technologies that form the basis of a digital money ecosystem
- used to store and transmit value among participants in the bitcoin network
- users communicate with each other using the bitcoin protocol
- bitcoin protocol stack is open source
- it can be run on a wide range of computing devices

**How it's used:**  
- users transfer bitcoin over the network
- like fiat money they can buy and sell goods, send money to people or organizations, or extend credit
- it can be purchased, sold, and exchanged for other currencies at specialized currency exchanges
- near perfect form of money for the internet because it is fast, secure, and borderless

**Virtual by nature:**
- bitcoin are entirely virtual, so there's no physical coins or even digital coins
- coins are implied in transactions that transfer value from sender to recipient
- users own keys that allow them to prove ownership of bitcoin in the bitcoin network
- keys sign transactions to unlock the value and spend it by transferring it to a new owner
- keys are often stored in a digital wallet on each user’s computer or smartphone
- possession of the key that can sign a transaction is the only way to spend bitcoin
- this puts the control entirely in the hands of each user

**Distrubuted peer-to-peer system:**
- no “central” server or point of control
- Bitcoin are created through a process called “mining”
- involves competing to find solutions to a mathematical problem while processing bitcoin transactions
- anyone can be a miner if they're using a device running the full bitcoin protocol staci
- they use their computer's processing power to verify and record transactions
- miners validate the transactions of the past 10 minutes and are rewarded with a new bitcoin
- this process decentralizes the currency-issuance and clearing functions of a central bank
- it conveniently replaces the need for any central bank

**The protocol:**
- the included algorithms regulate mining function across network
- dynamic adjustment occurs during the mining process 
- this adjustment is the increase or decrease of difficulty of the processing task
- the intent for the adjustment is to make it so every 10 minutes, a miner succeeds
- by default, the protocol is also responsible for halving the rate at which new bitcoin are created
- it also limits the total number of bitcoin to be mined to just below 21 million coins
- this results in a predictable curve where the total bitcoin in circulation will max out in 2140
- as time goes on the currency becomes deflationary due to lower rate of issuance
- it cannot be inflated by printing new money

**The four key ingredients of Ƀitcoin:**
- decentralized peer-to-peer network (the bitcoin protocol)
- public transaction ledger (the blockchain)
- set of rules for independent transaction validation and currency issuance (consensus rules)
- tool for reaching global decentralized consensus on valid blockchain (Proof-of-Work algorithm)

**The history:**
- invented in 2008 by Satoshi Nakamoto
- comprised of several prior invenctions (b-money, HashCash)
- key innovation was using distributed computation system called "Proof of Work"
- solves the problem of double-spend by having global election every 10 minutes
- network officially started in 2009
- mining algorithm now exceeds combined processing power of world's top supercomputers
- Satoshi withdrew from public in 2011
- volunteers now run the project
- groundbreaking invention operating on mathematical prinicples, open source and consensus
- solves the Byzantine Generals' Problem using Proof-of-Work to acheive consensus
- total breakthrough in distributed computing
- can be widely applied beyond just currency

## How Bitcoin Works

**The system consists of the following:**
- users with wallets that contain keys
- transactions that are propagated across the network
- miners who produce the consensus blockchain through competitive computation
- this blockchain is the authoritative ledger of all transactions

**Tracking transactions via blockchain explorer:**
- blockchain explorers allow you to search for addresses, transactions and blocks
- with explorers you're able to view where in the system the transactions are
- search by bitcoin address, transaction hash, block number or block hash
- retreiving info about transactions is simple
- QR code can be scanned with a device
- QR-encoded URL's contain destination address, payment amount and description 
- transactions inform network that owner has authorized transfer of a bitcoin value
- transfers can then be made to another owner right down the chain

**Inputs and outputs:**
- each transaction can have one or more inputs and outputs
- inputs are debits against a bitcoin account
- outputs are credits added to a bitcoin account
- inputs and outputs don't add up to same amount due to transaction fees
- outputs will add slightly less with the difference representing the fee
- proof of ownership of inputs and outputs are verified through digital signature

**Transaction chains:**
- inputs from latest transaction correspond to outputs from previous transaction
- the user's key provides signature to unlock previous transaction outputs
- this proves to bitcoin network that the user owns the funds
- the output also will require the user (recipient) to provide signature to receive amount
- transactions simply move value from inputs to outputs

**Change address:**
- since transaction inputs cannot be divided, a change address is needed to handle balance
- buying a $5 item with $20 will result in approximately $15 going to back to your change address
- transaction fee is subtracted before remainder is sent to change address
- change address can differ from origin address for enhanced privacy
- chain of ownership created as value is moved from owner to owner

**Common transaction forms:**
- most common is a simple payment that includes change returned to original owner
- aggregating several inputs into a single output (wallet cleanup, small change stuff)
- distribution of funds like payroll where one input gets sent to multiple outputs

**Constructing a transaction:**
- input/output logic for transaction is set in wallet or exchange
- can be done offline and signed once connected
- before transaction can occur, inputs must be found by wallet
- if user A pays user B, user B's wallet will lookup the output from user A's transaction
- all unspent outputs can accessed via available APIs, cURL or asking a full-node
- outputs contain scripts that indicate who can access output via key signature
- outputs are also responsible for handling the change after main payment is complete
- transaction fees are collected by the miner for validating and recording in blockchain
- blockchain explorers allow user to view current state of the transaction

**Adding to ledger - propagation:**
- bitcoin network receives transmission of transaction
- everything needed to process the transaction is included
- it's destination within the network is not important 
- the peer-to-peer nature connects client to other clients
- propagation occurs when nodes receive valid transactions and then forward
- known as _flooding_, the majority of nodes are rapidly propagated
- transaction has been added and is now cemented in the blockchain forever

**Mining:**
- validates transactions utilizing _consensus rules_
- secures bitcoin transactions by rejecting invalid or malformed transactions
- create new bitcoin in each block
- amount per block is limited, diminishing over time
- uses electricity to solve mathematical problem
- miners earn new bitcoins as a reward
- reward only collected if all transactions are validated
- difficulty of miner's puzzle is adjusted accordingly
- first miner to find solution wins the round and published block to blockchain

**Mining transactions in blocks:**
- unverified transactions are added to new blocks
- miners can then mine the block once previous block from network is received
- new block is created and filled with transactions
- fingerprint of previous block is also included in new block
- Proof-of-Work calculations begin
- a special transaction is also added to the block to pay miner for reward
- miners utilize mining pools that contain a _candidate block_
- _candidate blocks_ represent transactions picked up by network that need validation
- once solution is found for candidate block it's announced to network
- it's then validated by other miners
- the process starts again, new race to generate the next block
- as block height increases, so does the computation difficutly
- a block with six confirmations is irrevocable
- too much computational power would be needed to recalculate six blocks 
- more trust is built

Spending the transaction:
- once embedded in block on the chain it is now spendable
- full-node clients can trace the funds back to moment it was generated
- Simplified Payment Verification can be utilized by lightweight clients
- SPV lets you validate YOUR transactions without worrying about everyone elses
- SPV ensures your transactions are in a block
- SPV provides confirmations through (PoW) that additional blocks are being added
- through the simple and secure SPV system, spending can happen quickly
- transactions build up the ownership chain







