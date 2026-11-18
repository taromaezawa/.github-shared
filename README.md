# shared GitHub Actions

Shared composite actions for taromaezawa repositories.

## .github/actions/ftp-deploy

Deploy files over **explicit FTPS with certificate verification** (`protocol: ftps`, `security: strict`, port 21).
Plain FTP and unverified TLS cannot be selected.

> Versions up to `484a901` did not pass `protocol` and sent everything — including the password — over **plain FTP**,
> despite the description saying "FTPS". Do not use them. Rotate any credentials that were used with them.

### Rules

- Pin this action by **commit SHA** (never `@main`).
- `ftp-host` must be the name on the server certificate (e.g. `ik10003.mixhost.jp`), not an alias or an IP address.
- Use a **dedicated FTP account whose directory is the deploy folder**, and set `ftp-path: .`.
  Never give CI an account that can write the whole `public_html`.
- Pass secrets only via `with:` (never expand them inside `run:`).

### Usage

```yaml
- uses: taromaezawa/.github-shared/.github/actions/ftp-deploy@<commit-sha>
  with:
    ftp-host: ${{ secrets.FTP_HOST }}
    ftp-user: ${{ secrets.FTP_USER }}
    ftp-pass: ${{ secrets.FTP_PASS }}
    ftp-path: .
    local-dir: ./dist/
```
