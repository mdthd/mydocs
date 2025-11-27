# CURL: Client URL

curl is a program to transfer data using protocols HTTP, HTTPS, FTP, SFTP

Fetch and Display web pages or API contents

## Download `curl`

For windows: Go to https://curl.se/windows/

For Linux: `sudo apt install curl` or `sudo dnf install curl`

### Check Version of curl

```bash
curl -V
```

| Flag | Purpose | Example |
| --- | --- | --- |
| `-X` / `--request` | Specify HTTP method | `curl -X POST https://api.example.com/data` |
| `-d` / `--data` | Send request body | `curl -d "name=John&age=30" https://api.example.com/users` |
| `-H` / `--header` | Add custom header | `curl -H "Content-Type: application/json" -H "Authorization: Bearer TOKEN" https://api.example.com/data` |
| `-u` / `--user` | Basic auth | `curl -u username:password https://api.example.com/login` |
| `-o` | Write output to file | `curl -o output.html https://example.com` |
| `-O` | Save with remote filename | `curl -O https://example.com/file.zip` |
| `-L` | Follow redirects | `curl -L https://short.url/link` |
| `-I` | Fetch headers only | `curl -I https://example.com` |
| `-s` | Silent mode | `curl -s https://example.com > page.html` |
| `-v` | Verbose mode | `curl -v https://example.com` |
| `--compressed` | Request compressed response | `curl --compressed https://example.com` |
| `-k` / `--insecure` | Ignore SSL cert check | `curl -k https://self-signed.badssl.com/` |