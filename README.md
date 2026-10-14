# PK Media commerce update manifest

This repository publishes one file: `v1/version.json`. Every PK Media commerce store's dashboard reads it
(server side, at most once an hour) to learn whether a newer version of the platform exists, and shows
"Update available" when it does. It contains no code and no client data.

Stores read it from:

    https://raw.githubusercontent.com/SeifxEssam/commerce-updates/main/v1/version.json

(`COMMERCE_UPDATE_CHECK_URL` in the store's environment; new stores made with create-store 1.0.1 or later
use this URL by default.)

Fields: `latest_version` (required), `released_at`, `notes_url`, `min_upgradable_from` (an older store must
update to that version first), `security` (marks a security release). The format is versioned by the `v1/`
path. The file is written by `bin/release-package.sh` in the platform's source repository at each release and
copied here.
