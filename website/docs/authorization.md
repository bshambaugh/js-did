# Authorization

Authorize and use DIDs where needed. At the moment, only Ethereum accounts
are supported with the EthereumAuthProvider. Additional accounts will be supported in the future.

```ts
import { DIDSession } from 'did-session'
import { EthereumAuthProvider } from '@ceramicnetwork/blockchain-utils-linking'

const ethProvider = // import/get your web3 eth provider
const addresses = await ethProvider.enable()
const authProvider = new EthereumAuthProvider(ethProvider, addresses[0])

// the resources param is a list of strings identifying resources you want to authorize for,
// according to the verification protocol you use (e.g. for Ceramic Network Protocol, these are ceramic stream IDs)
const session = await DIDSession.authorize(authProvider, { resources: [...]})

// use the session to verify that a given address is authorized

```