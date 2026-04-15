# scan.tipschain.online

Starter repository for the Tipschain explorer asset set.

## Included assets

This repo currently ships the token logos used across the Tipschain ecosystem in a GitHub-friendly layout:

```text
branding/
└── tpc-network-icon.png            # Blockscout network icon / branding asset

tipschain-assets/
└── blockchains/
    └── tipschain/
        ├── info/
        │   ├── info.json             # Native TPC wallet metadata
        │   └── logo.png              # Native TPC coin logo
        └── assets/
            ├── 0x1F8a034434a50EB4e291B36EBE91f10bBfba1127/
            │   ├── info.json         # USDTC wallet metadata
            │   └── logo.png          # USD Tips (USDTC)
            ├── 0x9D41ed4Fc218Dd877365Be5C36c6Bb5Ec40eDa99/
            │   ├── info.json         # USDT wallet metadata
            │   └── logo.png          # Tether USD (USDT)
            └── 0xd2E9DFeB41428f0F6f719A74551AE20A431FA365/
                ├── info.json         # WTPC wallet metadata
                └── logo.png          # Wrapped TPC (WTPC)

wallet-listing/
├── tipschain.network.json           # EIP-3085 chain metadata for wallets
└── tipschain.tokens.json            # Token list for wallet imports
```

## Token mapping

- `0x1F8a034434a50EB4e291B36EBE91f10bBfba1127` -> `USD Tips (USDTC)`
- `0x9D41ed4Fc218Dd877365Be5C36c6Bb5Ec40eDa99` -> `Tether USD (USDT)`
- `0xd2E9DFeB41428f0F6f719A74551AE20A431FA365` -> `Wrapped Tips Coin (WTPC)`
- native coin -> `TPC` at `tipschain-assets/blockchains/tipschain/info/logo.png`

## Notes

- Source logo files were copied from the local Tipschain design assets supplied in this workspace.
- See `BLOCKSCOUT-CONFIG.md` for the exact links to paste into the explorer configuration.
- The current Blockscout handoff uses jsDelivr CDN links backed by `tipspay-dev/scan.tipschain.online` for Tipschain-native assets and `tipspay-dev/assets` as the fallback fork for other chain token icons.
- Trust Wallet-style metadata is now included here for canonical public hosting, but official third-party wallet support still depends on each wallet's own review and chain-support process.
