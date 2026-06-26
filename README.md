# shared GitHub Actions

Shared composite actions for taromaezawa repositories.

## .github/actions/ftp-deploy

Deploy files to an FTP server via FTPS.

### Usage

```yaml
- uses: taromaezawa/.github-shared/.github/actions/ftp-deploy@main
  with:
    ftp-host: ${{ secrets.FTP_HOST }}
    ftp-user: ${{ secrets.FTP_USER }}
    ftp-pass: ${{ secrets.FTP_PASS }}
    ftp-path: ${{ secrets.FTP_PATH }}
    local-dir: ./dist/
```
