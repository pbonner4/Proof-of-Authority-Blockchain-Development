# Proof-of-Authority-Blockchain-Development

###

** Before beginning you must download geth, puppeth and MyCrypto Wallet before starting.

1. Open up notes or microsoft word, in order to have information to revert back to and save information for your terminal window.

2. Open up a folder and directory to work in, place nodes in, and place keystores in.

3. Create Node 1 and Node 2 accounts and save the passwords for those accounts using the code below.

"./geth account new --datadir node1" for node 1
"./geth --datadir node2 account new" for node 2

Next, Creating the Genesis block

  a. run puppeth, name your network, and select configure the new genesis block.

  b. Choose POA, and the default seconds for block.

  c. Seal and Pre-fund accounts with addresses of new nodes (you can find these addresses in your Node1>keystore folder)

  e. specify chain id, set it to a rememberable 3 or 4 digit number (be sure not to use 1 because ETH reserves these chain id's )

  f. export the genesis configurations, you will only need the your .json containing the networks name (yournetworksname.jason)

4. With the genesis block configured, we can now initialize the nodes with our nodes .json files
  a. using geth, which have previously downloaded, initialieze node 1 with "./geth --datadir node1 init networkname.json".
  
  b. Use "./geth --datadir node2 init networkname.json" in to initialize node 2.
  
5. With that done, we can now begin mining with the blocks with the nodes
  a. in seperate terminal windows, run the commands
    -./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock
    -./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
    
6. Now, your chain should be running.


____________________________________________________________________________________________________________________________________________________________________

### Open MyCrypto

7. With your blockchain now running, open up your myCrypto app and click on the change network link in the lower righthand corner. Make sure to scroll all the way to the bottom and click on the custom in order to reveal more options like the chain ID. Be sure to set the URL to http://127.0.0.1:8545.

8. Go to open your wallet, Select Keystore File to open up your wallet. Click “SELECT WALLET FILE” and navigate to node1/keystore file.

9. Send a transaction from Node 1 to a new Node 2. Confirm the transaction by clicking Check TX Status.




Aaron, I spoke with Kyle about the screenshots confirming the transaction and we could not come up with a solution to my problem.





In order to begin mining, run this code, inputting your own numbers.
./geth --datadir node1/ --syncmode 'full' --networkid 'any number' --rpc --minerthreads 1 --unlock "node1_sealer_address" --password node1/password.txt --mine --allow-insecure-unlock

Open up a second git bash terminal, and run below. Be sure to grab the "enode address" from the previous gitbash terminal.Also, if running windows, use "ipcdisable" at the end of the node.
./geth --datadir node2/ --syncmode 'full' --networkid 'same number as node 1" --unlock "node2_sealer_address" --password node2/password.txt --mine --allow-insecure-unlock --port 30304 --bootnodes "enode_address_from_node1" --ipcdisable

** Open MyCrypto

Press " Change Network", press add custom node, and find your chain id from the Genesis block. Remember you exported it in step 6 previously. Be sure to set node name and network name to the name you chose for your chain. Be sure to set the URL to http://127.0.0.1:8545.

Go to open your wallet, Select Keystore File to open up your wallet. Click “SELECT WALLET FILE” and navigate to node1/keystore file.

Send a transaction from Node 1 to a new Node 2. Confirm the transaction.
