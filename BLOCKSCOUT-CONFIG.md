# Blockscout Config

This file is aligned to the live GitHub repo paths:

- `tipspay-dev/scan.tipschain.online`
- `tipspay-dev/assets`

## Paste into Blockscout config

### Network icon -> branding link

```env
NEXT_PUBLIC_NETWORK_ICON=https://cdn.jsdelivr.net/gh/tipspay-dev/scan.tipschain.online@main/tipschain-assets/blockchains/tipschain/info/logo.png
```

Optional if you want the same art in the expanded navigation/logo slot too:

```env
NEXT_PUBLIC_NETWORK_LOGO=https://cdn.jsdelivr.net/gh/tipspay-dev/scan.tipschain.online@main/tipschain-assets/blockchains/tipschain/info/logo.png
FAVICON_MASTER_URL=https://cdn.jsdelivr.net/gh/tipspay-dev/scan.tipschain.online@main/tipschain-assets/blockchains/tipschain/info/logo.png
```

### Token icons -> repo path

Use this as the base repo path for token icons:

```text
https://cdn.jsdelivr.net/gh/tipspay-dev/scan.tipschain.online@main/tipschain-assets/blockchains/tipschain
```

Resolved asset paths in this repo:

- Native TPC: `https://cdn.jsdelivr.net/gh/tipspay-dev/scan.tipschain.online@main/tipschain-assets/blockchains/tipschain/info/logo.png`
- USDTips (USDTC): `https://cdn.jsdelivr.net/gh/tipspay-dev/scan.tipschain.online@main/tipschain-assets/blockchains/tipschain/assets/0x1F8a034434a50EB4e291B36EBE91f10bBfba1127/logo.png`
- Tether USD (USDT): `https://cdn.jsdelivr.net/gh/tipspay-dev/scan.tipschain.online@main/tipschain-assets/blockchains/tipschain/assets/0x9D41ed4Fc218Dd877365Be5C36c6Bb5Ec40eDa99/logo.png`
- Wrapped TPC (WTPC): `https://cdn.jsdelivr.net/gh/tipspay-dev/scan.tipschain.online@main/tipschain-assets/blockchains/tipschain/assets/0xd2E9DFeB41428f0F6f719A74551AE20A431FA365/logo.png`

### Other coins -> your Trust Wallet fork

Use this repo for non-Tipschain token fallback paths:

```text
https://cdn.jsdelivr.net/gh/tipspay-dev/assets@master/blockchains
```

## Important

After this:

1. Paste the branding link and token icon repo path into your Blockscout configuration.
2. Restart the explorer so the updated configuration is loaded.

## Notes

- The official Blockscout frontend docs explicitly document `NEXT_PUBLIC_NETWORK_ICON`, `NEXT_PUBLIC_NETWORK_LOGO`, and `FAVICON_MASTER_URL`.
- The official backend docs explicitly document `DISPLAY_TOKEN_ICONS`, but do not spell out your custom repo-path field on the docs page I checked. The token repo-path instruction here follows the explorer setup you described and the Trust Wallet-style asset layout you asked for.

## Legacy Token Patch

If you are patching the legacy Blockscout `token_icon.js` helper, use this version:

```js
const TRUSTWALLET_ASSETS_REPO =
  'https://cdn.jsdelivr.net/gh/tipspay-dev/assets@master/blockchains'

const TIPSCHAIN_ASSETS_REPO =
  'https://cdn.jsdelivr.net/gh/tipspay-dev/scan.tipschain.online@main/tipschain-assets/blockchains'

const TIPSCHAIN_ID = '19251925'

function normalizeAddress(hash) {
  return String(hash || '').trim()
}

function getTipsChainTokenIconPath(address) {
  const normalized = normalizeAddress(address)
  return `${TIPSCHAIN_ASSETS_REPO}/tipschain/assets/${normalized}/logo.png`
}

function getTrustWalletTokenIconPath(chainId, address) {
  const normalized = normalizeAddress(address)
  return `${TRUSTWALLET_ASSETS_REPO}/smartchain/assets/${normalized}/logo.png`
}

export default function tokenIconUrl(address, chainId) {
  const normalizedChainId = String(chainId || '')

  if (!address) return null

  if (normalizedChainId === TIPSCHAIN_ID) {
    return getTipsChainTokenIconPath(address)
  }

  return getTrustWalletTokenIconPath(chainId, address)
}
```
