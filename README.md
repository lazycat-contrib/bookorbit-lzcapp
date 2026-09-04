# BookOrbit for LazyCat

This repository packages [BookOrbit](https://github.com/bookorbit/bookorbit) as a LazyCat LPK v2 application.

BookOrbit is your reading space: a self-hosted library manager and reader for organizing books, enriching metadata, tracking reading, and integrating with reading devices.

## Deployment wizard

The setup wizard configures the library owner, timezone, initial administrator profile and password, one-time bootstrap token, and Node.js heap limit. Database and JWT credentials are generated internally as stable secrets.

The selected user's private documents directory stores the book library. BookOrbit application data and PostgreSQL data remain in application-managed storage.

## Automatic publishing

The scheduled workflow discovers stable semantic-version tags from `ghcr.io/bookorbit/bookorbit`, verifies the `linux/amd64` image through `ghcr.nju.edu.cn`, creates a versioned GitHub Release asset, and publishes it only to the MiaoMiao private store. PostgreSQL is pinned to the immutable `pgvector/pgvector:0.8.6-pg18` mirror tag.

Required GitHub Actions secrets:

- `APPSTORE_URL`
- `APPSTORE_TOKEN`
- `APP_ID` (optional)
- `PRIVATE_STORE_GROUP_CODES` (optional)

## Local build

```bash
lzc-cli project release -o dist/bookorbit.lpk
lzc-cli lpk info dist/bookorbit.lpk
```

## License and attribution

BookOrbit and its branding are provided by the upstream project under AGPL-3.0. This packaging repository does not modify the upstream application image.
