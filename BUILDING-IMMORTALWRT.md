# Building ImmortalWrt APK artifacts

This fork includes a GitHub Actions workflow that builds APK packages named like:

- `quickfile-*.apk`
- `luci-app-quickfile-*.apk`

for ImmortalWrt `25.12.1`, target `rockchip/armv8`, architecture `aarch64_generic`.

## Run a build

Open **Actions** -> **Build ImmortalWrt APK** -> **Run workflow**.

The default inputs build the latest upstream source from:

```text
sbwml/luci-app-quickfile@main
```

The workflow also runs weekly, so the fork can keep producing artifacts when the upstream package changes without needing to sync this fork first.

## Download the packages

After a successful run, open the run page and download the artifact named like:

```text
quickfile-immortalwrt-25.12.1-rockchip-armv8-<run-number>
```

The artifact contains the APK files, `SHA256SUMS`, and `build-info.txt`.

## Build from this fork instead

If you edit the package in this fork and want to build your forked source, run the workflow manually and set:

```text
source_repository = <your-github-user>/luci-app-quickfile
source_ref = main
```

## Install on the R4SE

Copy both APK files to the router and install them with `apk add`.

QuickFile depends on the nginx LuCI setup. Keep your existing nginx configuration and only include or merge the QuickFile locations where needed.
