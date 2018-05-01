# TouristCoin Explorer

<b>Live Version: [explorer.touristcoin.net](https://explorer.touristcoin.net)</b>

## Local installation

Clone the repo

`git clone https://github.com/touristcoin/explorer`

Download [Nodejs and npm](https://docs.npmjs.com/getting-started/installing-node "Nodejs install") if you don't have them

Install dependencies:

`npm install`

Install mongodb:

MacOS: `brew install mongodb`

Ubuntu: `sudo apt-get install -y mongodb-org`

## Populate the DB

This will fetch and parse the entire blockchain.

Setup your configuration file: `cp config.example.json config.json`

Edit `config.json` as you wish

Basic settings:
```json
{
    "nodeAddr":     "localhost",
    "gethPort":     8545,
    "startBlock":   0,
    "endBlock":     "latest",
    "quiet":        true,
    "syncAll":      true,
    "patch":        true,
    "patchBlocks":  100,
    "settings": {
        "symbol": "TOU",
        "name": "TouristCoin",
        "title": "TouristCoin Network Blockchain Explorer",
        "author": "TouristCoin Network Community",
        "miners": {
           "0x826f76124d8acff7e1ae985bb50c481342695964": "tou.touristcoin.net",
        }
    }
}

```

```nodeAddr```    Your node API RPC address.

```gethPort```    Your node API RPC port.

```startBlock```  This is the start block of the blockchain, should always be 0 if you want to sync the whole CLO blockchain.

```endBlock```    This is usually the 'latest'/'newest' block in the blockchain, this value gets updated automatically, and will be used to patch missing blocks if the whole app goes down.

```quiet```       Suppress some messages. (admittedly still not quiet)

```syncAll```     If this is set to true at the start of the app, the sync will start syncing all blocks from lastSync, and if lastSync is 0 it will start from whatever the endBlock or latest block in the blockchain is.

```patch```       If set to true and below value is set, sync will iterated through the # of blocks specified

```patchBlocks``` If `patch` is set to true, the amount of block specified will be check from the latest one.


### Run:
If you run

`npm start`

Leave this running in the background to continuously fetch new blocks.

`node app.js`

Leave this running in the background to view the front end: Opened on http://127.0.0.1:3000 for default.

### Stats

it will also start sync.js and start syncing the blockchain based on set parameters. NOTE running app.js will always start sync.js keep listening and syncing the latest block.

`./tools/stats.js`
