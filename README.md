# Creator Pool

Creator Pool is a sponsor-funded campaign payout app for content creators.

- A sponsor sets a creative brief, a fixed reward per selected piece, a total budget and a closing date.
- Creators submit links to their work.
- The sponsor approves the pieces it wants. Each approval reserves that creator's reward.
- Each approved creator claims their own payout.
- Closing a campaign refunds only the uncommitted remainder. Approved rewards stay claimable after close.

Built by **TokenJunkieLabs**.

## Local demo only: no real money

This package runs a **local, non-monetary demonstration**:

- **Token:** `CPDEMO` (Creator Pool Demo Token) is a local development token. It has no value, no redemption and buys nothing.
- **Chain:** a private Ganache development chain on your own machine, chain ID 1337 (or 31337). It is bound to loopback only.
- **Accounts:** the `sponsor`, `creatorA` and `creatorB` actors are unlocked local development accounts. Choosing one is a demo convenience, **not authentication**.
- **Not included:** this package ships no hosted service, no public-chain deployment, no wallet credentials and no production keys.
- **Public mode:** the source contains an optional public-network mode. It is not deployed or configured here.

## Requirements

- Node.js 20 or newer, and npm.
- Backend dependencies (pinned in `creator-pool/backend/package.json`): `ethers` 6.13.4 and `solc` 0.8.26, plus the development dependency `ganache` 7.9.2.
- `npm install` downloads these from the npm registry. No other services are used.

## Run it locally

From this package root:

```sh
cd creator-pool/backend
npm install
npm run demo
```

`npm run demo` does the following:

- Starts a persistent local Ganache chain.
- Deploys the contracts once, only when the data directory is empty.
- Serves the campaign workspace at <http://127.0.0.1:8787>.

Wait for the "ready" line, then open that address. Press Ctrl+C to stop. Run `npm run demo` again to resume the same campaigns and balances.

### Data directory

- **`CP_DATA_DIR`** selects the data directory. It defaults to `data`, resolved relative to `creator-pool/backend/`.
- **Keep the whole directory together.** It holds:
  - `ganache-db/`: the saved chain.
  - `deployment.json` and `abi.json`: identify its contracts.
  - `state.json`: campaign text and the operation journal.
- **`PORT`** changes the workspace port.
- **`RPC_URL`** can point at an existing loopback development chain.

### Launcher safeguards (unchanged)

The launcher:

- Refuses non-loopback or credentialed RPC URLs.
- Refuses any chain other than 1337/31337.
- Refuses a non-loopback bind address.
- Leaves an unrelated process on an occupied port running and stops with an explanation.
- Never erases data or redeploys over saved state. Incomplete or mismatched data produces a recovery message instead.


## Package contents and licenses

The standalone package includes the Creator Pool application source, a package manifest, and both applicable license files.

Licensing: [LICENSE](LICENSE) and [creator-pool/LICENSE](creator-pool/LICENSE) are included. Retain both when redistributing.

## Provenance

The accepted Creator Pool source snapshot is commit `afcc48eccc32859762b57236f159c1f0b4bce1a6`.
`STANDALONE-MANIFEST.json` records the included paths and their source and packaged hashes.
