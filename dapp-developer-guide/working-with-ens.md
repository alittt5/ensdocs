# Working with ENS

Before you can begin interacting with ENS, you will need to obtain a reference to the ENS registry. How you do this depends on the library you are using.

Example code for the Javascript-based APIs \(ensjs, web3.js, ethjs-ens, and ethers.js\) here expect that they are being run inside a DApp browser, such as Chrome with [metamask installed](https://metamask.github.io/metamask-docs/Main_Concepts/Getting_Started), which exposes the `ethereum` object.



```javascript
import ENS, { getEnsAddress } from '@ensdomains/ensjs'

const ens = new ENS({ provider, ensAddress: getEnsAddress('1') })
```

```javascript
var Web3 = require("web3")

var accounts = ethereum.enable();
var web3 = new Web3(ethereum);
var ens = web3.eth.ens;
```

```javascript
const ENS = require('ethjs-ens');
// Currently requires both provider and
// either a network or registryAddress param
var accounts = ethereum.enable();
const ens = new ENS({ ethereum, network: '1' });
```

```javascript
var ethers = require('ethers');
var provider = new ethers.providers.Web3Provider(ethereum);
// ENS functionality is provided directly on the core provider object.
```

```go
import (
  ens "github.com/wealdtech/go-ens/v2"
  ethereum "github.com/ethereum/go-ethereum"
)

// Can dial up a connection through either IPC or HTTP/HTTPS
client, err := ethereum.Dial("/home/ethereum/.ethereum/geth.ipc")
registry, err := ens.Registry(client)
```

```python
from ens.auto import ns
```

```java
EnsResolver ens = new EnsResolver(web3j, 300 /* sync threshold, seconds */);
```


Some web3 libraries - e.g., ethers.js, web3j, and web3.py - have integrated support for name resolution. In these libraries, you can pass in an ENS name anywhere you can supply an address, meaning you do not need to interact directly with their ENS APIs unless you want to manually resolve names or do other ENS operations.

If no library is available for your platform, you can instantiate the ENS registry contract directly using the interface definition [here](https://github.com/ensdomains/ens/blob/master/contracts/ENS.sol). Addresses for the ENS registry on each supported network are available in the [ENS Deployments](../ens-deployments.md) page.

