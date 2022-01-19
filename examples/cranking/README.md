## Cranking

There are multiple permissionless instructions that `crank` or keep the zeta platform in an up to date state.
This example runs all the necessary instructions.

1. Crank event queue.
- This will process maker fill events to ensure that user margin accounts are in the correct state after trades occur.

2. Update pricing.
- This calls our instruction to recalculate mark prices and greeks for our products on a expiry basis.

3. Retreat market nodes.
- This retreats our volatility surface and interest rates based on the trades that have occurred on the platform.

4. Rebalance insurance vault.
- This moves funds collected from fees between margin accounts and the insurance vault (which is used to ensure platform security).

## Cranking on Mainnet

To crank on mainnet, you will need to install the following:

- [NodeJS + NPM](https://nodejs.org/it/)
- [Solana cli](https://docs.solana.com/cli/install-solana-cli-tools)

### Generate a new Solana account from the CLI

Generate the private key using solana cli: `solana-keygen new -o ~/my-key-folder/keyfile.json`

The key will be in this format: `[111,222,10,20,101,...]` and will be a JSON file..

Save this key for later and make sure to not share it with anyone! You can import it in [Phantom wallet](https://phantom.app/) to interact with the account from the Phantom browser extension.

Send some SOL to the account, since you will need it to pay the transaction fees.

### Setup the cranking

After cloning this repo, go to `./sdk/examples/cranking` and edit the `.env` file with your text editor of choice

Add the private key you previously generated in the `private_key` field of the .env file. 

You can also setup the intervals for cranking (they are in milliseconds). **(NB: small interval = more frequent cranking and higher costs due to fees.)**

### Install deps and run

Install dependencies with `npm install`

Finally, run the cranking with `npm run start` 

That's it! Happy cranking.
