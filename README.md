# Vigolium Scoop bucket

Official Windows x64 package for [Vigolium](https://github.com/vigolium/vigolium).

```powershell
scoop bucket add vigolium https://github.com/vigolium/scoop-bucket
scoop install vigolium
```

Update with `scoop update vigolium` and remove with `scoop uninstall vigolium`.
Configuration and scan data stay in the user's normal Vigolium directories.
The manifest downloads the upstream ZIP and verifies its SHA-256 checksum.

The initial v0.5.1 binary predates Vigolium's new package-manager updater guard.
Use Scoop for binary upgrades; the guard will take effect in a future upstream
binary release. This is a dedicated bucket; it is not yet in Scoop's main bucket.

## Release updates

The **Update release** GitHub Actions workflow checks the latest published stable
release of `vigolium/vigolium` hourly. It downloads and verifies the five upstream
archives against `checksums.txt`, reads license notices from the release tag, and
tests the candidate before committing it. Ordinary upstream commits and
prereleases do not publish a new package. Older versions cannot replace newer
ones, and version tags are never overwritten.

You can also run the workflow manually with an explicit stable tag. Enable
`force` to test the current version again. Failed validation leaves the current
package in place. GitHub may delay scheduled runs, and disables schedules in
public repositories after 60 days without repository activity; re-enable the
workflow in Actions if that happens.

The publishing job uses this repository's automatic, short-lived `GITHUB_TOKEN`
with `contents: write`. No personal access token, password, or custom secret is
required. Download and test jobs have read-only access.

Recipe generation and automation sources are maintained in
[`vigolium/vigolium/build/packaging`](https://github.com/vigolium/vigolium/tree/main/build/packaging).
The `.github/packaging` copy and pinned Nix package set/Scoop installer are updated
deliberately when the packaging tools change. This initial setup originated from
the packaging changes prepared locally; that source link will be available once
those changes are merged upstream.
