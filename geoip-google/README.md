# geoip-google

Source config: [geoip-google.yaml](https://github.com/yagh779/rule/blob/main/source/geoip-google/geoip-google.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| geoip-google | geoip-google | true | http | ipcidr | text | rules |  | [google.txt](https://raw.githubusercontent.com/nekolsd/geoip/release/text/google.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "geoip-google"
    type: select
    proxies: []
rules:
  - RULE-SET,geoip-google_IP,geoip-google,no-resolve
  - RULE-SET,geoip-google_Domain,geoip-google # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  - RULE-SET,geoip-google,geoip-google,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  geoip-google_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-google/geoip-google_IP.mrs }
  geoip-google_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-google/geoip-google_Domain.mrs } # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  geoip-google: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-google/geoip-google.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
```

## Artifacts

### mrs(ipcidr)

#### geoip-google_IP.mrs

GitHub: [geoip-google_IP.mrs](https://github.com/yagh779/rule/blob/release/geoip-google/geoip-google_IP.mrs)
Text: [geoip-google_IP.txt](https://github.com/yagh779/rule/blob/release/geoip-google/geoip-google_IP.txt)
Source: [geoip-google.original.txt](https://github.com/yagh779/rule/blob/release/geoip-google/geoip-google.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-google/geoip-google_IP.mrs
```

### mrs(domain)

#### geoip-google_Domain.mrs

GitHub: [geoip-google_Domain.mrs](https://github.com/yagh779/rule/blob/release/geoip-google/geoip-google_Domain.mrs)
Text: [geoip-google_Domain.txt](https://github.com/yagh779/rule/blob/release/geoip-google/geoip-google_Domain.txt)
Placeholder: upstream currently has no domain rules; contains blackhole.invalid only
Source: [geoip-google.original.txt](https://github.com/yagh779/rule/blob/release/geoip-google/geoip-google.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-google/geoip-google_Domain.mrs
```

### yaml(remaining)

#### geoip-google.yaml

GitHub: [geoip-google.yaml](https://github.com/yagh779/rule/blob/release/geoip-google/geoip-google.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [geoip-google.original.txt](https://github.com/yagh779/rule/blob/release/geoip-google/geoip-google.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-google/geoip-google.yaml
```
