# Deploy ProofPort

## Celo

1. Install and verify locally:

```bash
npm install
npm run compile:celo
npm run test:celo
```

2. Deploy to Celo Sepolia:

```bash
cp .env.example .env
# set PRIVATE_KEY and CELO_SEPOLIA_RPC_URL
npm run deploy:celo:sepolia
```

3. Copy the printed address, deployment transaction hash, and deployment block into your launch notes. Set:

```bash
NEXT_PUBLIC_CELO_NETWORK=celoSepolia
NEXT_PUBLIC_CELO_CONTRACT_ADDRESS=<address>
NEXT_PUBLIC_CELO_DEPLOYMENT_BLOCK=<block>
PROOFPORT_CELO_CONTRACT_ADDRESS_SEPOLIA=<address>
```

4. Mainnet deploy for production:

```bash
# set PRIVATE_KEY, CELO_MAINNET_RPC_URL, and enough CELO for gas
npm run deploy:celo:mainnet
```

5. For production set:

```bash
NEXT_PUBLIC_CELO_NETWORK=celo
NEXT_PUBLIC_CELO_CONTRACT_ADDRESS=<mainnet-address>
NEXT_PUBLIC_CELO_DEPLOYMENT_BLOCK=<mainnet-deploy-block>
PROOFPORT_CELO_CONTRACT_ADDRESS_MAINNET=<mainnet-address>
```

Optional verification:

```bash
npm run verify:celo:mainnet
```

## Stacks

1. Install Clarinet if needed:

```bash
brew install clarinet
```

2. Validate and test:

```bash
npm run check:stacks
npm run test:stacks
```

`npm run check:stacks` uses the installed Clarinet SDK, so it works without a global CLI. If you have the Clarinet CLI installed, `npm run check:stacks:clarinet` runs the native `clarinet check`.

3. Deploy to testnet:

```bash
# set STACKS_PRIVATE_KEY and STACKS_DEPLOY_FEE_MICROSTX
npm run deploy:stacks:testnet
```

4. Copy the printed contract id and tx id. Set:

```bash
NEXT_PUBLIC_STACKS_NETWORK=testnet
NEXT_PUBLIC_STACKS_CONTRACT_ADDRESS=<deployer-address>
NEXT_PUBLIC_STACKS_CONTRACT_NAME=proofport-log
PROOFPORT_STACKS_CONTRACT_ID_TESTNET=<deployer-address>.proofport-log
```

5. Mainnet deploy for production:

```bash
STACKS_NETWORK=mainnet npm run deploy:stacks:mainnet
```

6. For production set:

```bash
NEXT_PUBLIC_STACKS_NETWORK=mainnet
NEXT_PUBLIC_STACKS_CONTRACT_ADDRESS=<mainnet-deployer-address>
NEXT_PUBLIC_STACKS_CONTRACT_NAME=proofport-log
PROOFPORT_STACKS_CONTRACT_ID_MAINNET=<mainnet-deployer-address>.proofport-log
```

## Website

Deploy the Next.js app after both public contract configs are set:

```bash
npm run lint
npm run typecheck
npm run build
```

Keep these launch links with the production release:

- Website: `https://your-domain.example`
- Celo publishing path: `https://your-domain.example/celo`
- Stacks publishing path: `https://your-domain.example/stacks`
- Celo contract and first entry explorer receipt
- Stacks contract id and first entry explorer receipt
