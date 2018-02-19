# hello-ether
Private Ethereum testnet to develop and test decentralized apps



## Prerequisites 

- Geth (go-ethereum) 


```bash
brew tap ethereum/ethereum 
brew install ethereum
```

### Create temp genesis block

```bash
geth --identity "MyTestNetNode" --nodiscover --networkid 1999 --datadir data  init genesis.json
```


#### Create Ether Account 

```bash
geth account new --datadir data
```

Save the adress value!

Address: {eab0d85372b745b6bf4d0f4e9b1e5d52e09891af}


#### Delete all data

```bash
geth removedb --datadir data
```

#### Replace new account adress in genesis.json and run the init_genesis_block.sh again 

```bash
geth --identity "MyTestNetNode" --nodiscover --networkid 1999 --datadir data  init genesis.json
```




### Prefunding

geth --identity "MyTestNetNode" --datadir data --nodiscover --networkid 1999 console

### Check you account funds

web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")





# Starting with contracts


Important: Make sure that you include  *--datadir data* when running any local testnet geth command!

Example:
` geth attach --datadir data`


Login

```bash
personal.unlockAccount(eth.coinbase, 'password', 0)
```





Go to greeter folder

npm i

npm build 

Run 

```bash
 node_modules/.bin/testrpc
 ``` 

Open a NEW terminal window (with the first one still open and running), and run node :

node
> Web3 = require('web3')
> web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));
> web3.eth.accounts

Now you sould be able to run 

```bash
node lib.js
```


You should see something like:

```
| => node lib.js
Contract transaction send: TransactionHash: 0x096954decd6bed2d4485b12946930a2d2944948622648e1a8401bb02f156bcf7 waiting to be mined...
Contract mined! Yay! Address: 0xd2d12b8e56d804d547b1dc1f5fca489867d2c038
Contract {
  _eth:

 ...
```


Take note if the contrat address = 0xd2d12b8e56d804d547b1dc1f5fca489867d2c038


Once contract has been mined you can return to the geth javascript console and create an instance of your contract, and call greet on it.

To do this you need two things:
- the contract's ABI 
- the contract address


To get the contracts ABI run 
```bash
node_modules/babel-cli/bin/babel.js printAbi.js --out-file transpiledPrintAbi.js --no-comments && node transpiledPrintAbi.js
```





var myContract = web3.eth.contract([{"constant":false,"inputs":[],"name":"kill","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"greet","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"inputs":[{"name":"_greeting","type":"string"}],"payable":false,"stateMutability":"nonpayable","type":"constructor"}]).at(0xd2d12b8e56d804d547b1dc1f5fca489867d2c038).greet()





var greeter2 = eth.contract([{constant:false,inputs:[],name:'kill',outputs:[],type:'function'},{constant:true,inputs:[],name:'greet',outputs:[{name:'',type:'string'}],type:'function'},{inputs:[{name:'_greeting',type:'string'}],type:'constructor'}]).at('0xd2d12b8e56d804d547b1dc1f5fca489867d2c038');








#### References

- https://medium.com/@WWWillems/how-to-set-up-a-private-ethereum-testnet-blockchain-using-geth-and-homebrew-1106a27e8e1e
- https://github.com/evbots/greeter_contract
- https://github.com/ethereum/go-ethereum/wiki/Contract-Tutorial









