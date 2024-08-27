# Avalanche HYPERSDK PROJECT

This project uses HyperSDK that provides the ability to create a custom virtual machine, which offers complete control over a custom blockchain. By using the HyperSDK, we have full control over the rules and functionality of your chain, allowing us to create a custom blockchain that is tailored to your startup's specific needs. 


## Description 
```consts/consts.go``` contains the constants that is accessible across the hyperVM. The HRP, Name, and Symbol constants define information about the TokenVM, including its Human-Readable Part (HRP), name, and symbol.

```registry/registry.go``` contains the action that will be performed in the terminal during interaction.

## Steps of Execution
This project is execute on WSl on windows and GO installed inside wsl.<br>
1) run ```git clone https://github.com/Ms-10182/avax-advance-mod-2.git```
2) run ```cd avax-advance-mod-2```
3) Github is not allowing me to upload the files due to large no of files so I added the zip file.
4) Extract the ```Avalanche hyperSDK project```
5) cd ```'.\Avalanche hyperSDK project\' ```
6) In terminal run command ```MODE="run-single" ./scripts/run.sh``` and this will start our machine with 1 subnet and for 2 subnet run ```./scripts/run.sh```. after this command output will look like.
```javascript
Ran 4 of 4 Specs in 81.284 seconds
PASS
cluster is ready!
avalanche-network-runner is running in the background... 

use the following command to terminate:

killall avalanche-network-runner
```
7) To start interaction run ```./scripts/build.sh```. output will be :
```javascript
/scripts/build.sh
Building tokenvm in ./build/tHBYNu8ikqo4MWMHehC9iKB9mR5tB3DWzbkYmTfe9buWQ5GZ8
Building token-cli in ./build/token-cli
```
This command will put the compiled CLI in ./build/token-cli.
<b>NOTE- default address is ```token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp```</b>

8) Lastly, we'll need to add the chains we created and the default key to the token-cli. run command:
```javascript
./build/token-cli key import demo.pk
./build/token-cli chain import-anr
```
chain import-anr connects to the Avalanche Network Runner server running in the background and pulls the URIs of all nodes tracking each chain you created..

## Creation and Minting process
### Step 1 Asset Creation
To create an assest run the command:
```javascript
./build/token-cli action create-asset
```
Enter the metadata (eg:GoCoin) and confirm
output looks like:
```javascript
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: 2vCjHv1ws8YirjkcjsaVotLhCeownJDVBhUJgtBpu6j9ucupgf
metadata (can be changed later): GoCoin
continue (y/n): y
✅ txID: 2jce33uBTSa3yKrv7KngEdbwtyN4NBXfhGmx4Xtb6p6nPjtb9w
```
<b>NOTE - txID is the assetID of your new asset.</b>

### Step 2 Minting of asset
To mint the created assest run command:
```javascript
./build/token-cli action mint-asset
```
enter the assetID then enter the receipient then enter the amount and continue.
It would look like:
```javascript
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: 2skpAtPgFs5v5v2nzWaZKVrfRVxPXAVyfMQANy6EpFjG8dMQTo
assetID: 2fwV7cjRpH7jmK43BWtUc6uTo5Py6wKXBfdQ4CH6BwRMmEmdDe
metadata: GoCoin supply: 0
recipient: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
amount: 100
continue (y/n): y
✅ txID: 2hvyq3DSVHMwiWuJXPBy8T9LS2MjiX9Ki8ti625Vofrn7L1Ahi
```
### Step3 check balance
run the command:
```javascript
./build/token-cli key balance
```
and enter the assetID of the token and output will be like:
```javascript
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: 2skpAtPgFs5v5v2nzWaZKVrfRVxPXAVyfMQANy6EpFjG8dMQTo
✔ assetID (use TKN for native token): 2fwV7cjRpH7jmK43BWtUc6uTo5Py6wKXBfdQ4CH6BwRMmEmdDe█
uri: http://127.0.0.1:46526/ext/bc/2skpAtPgFs5v5v2nzWaZKVrfRVxPXAVyfMQANy6EpFjG8dMQTo
metadata: GoCoin supply: 100 warp: false
balance: 100 2fwV7cjRpH7jmK43BWtUc6uTo5Py6wKXBfdQ4CH6BwRMmEmdDe
```

### Additional to watcht the blockchain
run the command 
```javascript
./build/token-cli chain watch
```
and from the listed chainID enter the desired index of the chainID and it will start live watching of the blockchain.

### Closing 
run the command 
```javascript
killall avalanche-network-runner
```
This will close the blockchain we just deployed.
