# chargeOperators

台灣充電業者目錄（`ChargingOperators.json`），供 [ChargingWallet](https://github.com/talk812/ChargingWallet) App 遠端 OTA 更新。

## 資料流

1. **編輯目錄**：在此 repo 修改 `ChargingOperators.json`，遞增 `version` 與 `updatedAt`
2. **Push 此 repo**：`git push` → App 透過 `raw.githubusercontent.com` 拉取更新
3. **同步到 App bundle**：在 ChargingWallet 執行 `./scripts/sync_operator_catalog.sh pull`
4. **發版**：ChargingWallet 內建副本隨 App 版本釋出

若在 ChargingWallet 開發時先改了 bundle，推送前請：

```bash
cd /path/to/ChargingWallet
./scripts/sync_operator_catalog.sh push
cd ~/Documents/chargeOperators
git add ChargingOperators.json && git commit -m "catalog: vN ..." && git push
```

## Schema

與 `ChargeLog/Config/ChargingOperators.json` 相同：`version`、`updatedAt`、`operators[]`（`id`、`displayName`、`aliases`、`parser`、`rank` 等）。
