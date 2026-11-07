# Vigil for Homebrew

The Homebrew tap for [Vigil](https://github.com/godspeedhq/vigil), a job scheduler, supervisor and metrics forwarder written only in the shells that ship with each OS. macOS and Linux.

```sh
brew install godspeedhq/vigil/vigil
brew services start vigil      # runs it now and at every login
```

- Your configuration, scripts, state and logs are in `$(brew --prefix)/var/vigil`. `vigil config` edits the configuration; `vigil status` shows what it is doing.
- `brew upgrade vigil` updates it: a running supervisor picks up the new version by itself.
- `brew uninstall vigil` removes the program and keeps `$(brew --prefix)/var/vigil`.
- Under `brew services`, stopping the service ends running jobs too.

## How the formula is made

`Formula/vigil.rb` is written by Vigil's own `tools/release/tap-bucket.sh` from each release, with the archive's hash from the release's `SHA256SUMS`. The `update` workflow checks for a new release every hour, verifies `SHA256SUMS` against `release-key.pem` here, and commits the new formula. Change the formula in the Vigil repository (`packaging/homebrew/vigil.rb.in`), not here.

Licensed under the Apache License 2.0.
