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
        │   └── logo.png              # Native TPC coin logo
        └── assets/
            ├── 0x1F8a034434a50EB4e291B36EBE91f10bBfba1127/
            │   └── logo.png          # USDTips (USDTC)
            ├── 0x9D41ed4Fc218Dd877365Be5C36c6Bb5Ec40eDa99/
            │   └── logo.png          # Tether USD (USDT)
            └── 0xd2E9DFeB41428f0F6f719A74551AE20A431FA365/
                └── logo.png          # Wrapped TPC (WTPC)
```

## Token mapping

- `0x1F8a034434a50EB4e291B36EBE91f10bBfba1127` -> `USDTips (USDTC)`
- `0x9D41ed4Fc218Dd877365Be5C36c6Bb5Ec40eDa99` -> `Tether USD (USDT)`
- `0xd2E9DFeB41428f0F6f719A74551AE20A431FA365` -> `Wrapped TPC (WTPC)`
- native coin -> `TPC` at `tipschain-assets/blockchains/tipschain/info/logo.png`

## Notes

- Source logo files were copied from the local Tipschain design assets supplied in this workspace.
- GitHub CLI is not installed on this machine, so the remote GitHub repository still needs to be created manually before pushing.
- See `BLOCKSCOUT-CONFIG.md` for the exact links to paste into the explorer configuration.
- The current Blockscout handoff uses jsDelivr CDN links backed by `tipspay-dev/scan.tipschain.online` for Tipschain-native assets and `tipspay-dev/assets` as the fallback fork for other chain token icons.
