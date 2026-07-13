# xiangsushooter-crosspromo-config

Static config and icon hosting for XiangsuShooter (像素丧尸 / UnitZs) cross promotion and ads remote config via GitHub Pages.

## Structure

- `docs/app_config.json`: Remote runtime ads config used by `AdsOrchestrator`.
- `docs/cross_promo/config.json`: Cross promotion data consumed by `CrossPromoManager`.
- `docs/cross_promo/icons/`: Hosted PNG icons used by the config.

GitHub Pages base URL:

```text
https://gxhdky2345.github.io/xiangsushooter-crosspromo-config/
```

## Cross Promo Schema

```json
{
  "games": [
    {
      "name": "Battle Shooter",
      "iconUrl": "https://gxhdky2345.github.io/xiangsushooter-crosspromo-config/cross_promo/icons/battle_shooter.png",
      "iosIconUrl": "https://gxhdky2345.github.io/xiangsushooter-crosspromo-config/cross_promo/icons/battle_shooter.png",
      "androidIconUrl": "https://gxhdky2345.github.io/xiangsushooter-crosspromo-config/cross_promo/icons/battle_shooter.png",
      "iosId": "1234567890",
      "androidId": "com.company.game"
    }
  ]
}
```

Field notes:

- `name`: Display name shown in the panel.
- `androidIconUrl` / `iosIconUrl`: Platform-specific icons when set.
- `iconUrl`: Shared fallback icon (keep populated).
- `androidId`: Google Play package name.
- `iosId`: Apple App Store numeric ID only (no full URL).

## Ads Config Schema

`docs/app_config.json` matches this project's `AdsAppConfigData` / `app_ads_config.json` shape (`providers` arrays for android/ios).

Primary endpoint:

```text
https://gxhdky2345.github.io/xiangsushooter-crosspromo-config/app_config.json
```

jsDelivr backup:

```text
https://cdn.jsdelivr.net/gh/gxhdky2345/xiangsushooter-crosspromo-config@main/docs/app_config.json
```

## Publish Changes

```powershell
git add docs README.md
git commit -m "update cross promo config"
git push origin main
```

GitHub Pages usually reflects the change within a few minutes after the push succeeds.

## Unity project wiring

In the game project:

- CrossPromo `configUrl`: `https://gxhdky2345.github.io/xiangsushooter-crosspromo-config/cross_promo/config.json`
- CrossPromo backup: `https://cdn.jsdelivr.net/gh/gxhdky2345/xiangsushooter-crosspromo-config@main/docs/cross_promo/config.json`
- Ads `configUrl`: `https://gxhdky2345.github.io/xiangsushooter-crosspromo-config/app_config.json`
- Ads backup: `https://cdn.jsdelivr.net/gh/gxhdky2345/xiangsushooter-crosspromo-config@main/docs/app_config.json`
