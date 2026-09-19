# google

Source config: [google.yaml](https://github.com/yagh779/rule/blob/main/source/google/google.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| google | google | true | http | domain | text | rules |  | [google.txt](https://raw.githubusercontent.com/nekolsd/sing-geosite/domain-set/google.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "google"
    type: select
    proxies: []
rules:
  - RULE-SET,google_Domain,google
  - RULE-SET,google,google,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,google_IP,google,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  google_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/google/google_Domain.mrs }
  google: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/google/google.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  google_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/google/google_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### google_IP.mrs

GitHub: [google_IP.mrs](https://github.com/yagh779/rule/blob/release/google/google_IP.mrs)
Text: [google_IP.txt](https://github.com/yagh779/rule/blob/release/google/google_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [google.original.txt](https://github.com/yagh779/rule/blob/release/google/google.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/google/google_IP.mrs
```

### mrs(domain)

#### google_Domain.mrs

GitHub: [google_Domain.mrs](https://github.com/yagh779/rule/blob/release/google/google_Domain.mrs)
Text: [google_Domain.txt](https://github.com/yagh779/rule/blob/release/google/google_Domain.txt)
Source: [google.original.txt](https://github.com/yagh779/rule/blob/release/google/google.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/google/google_Domain.mrs
```

### yaml(remaining)

#### google.yaml

GitHub: [google.yaml](https://github.com/yagh779/rule/blob/release/google/google.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [google.original.txt](https://github.com/yagh779/rule/blob/release/google/google.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/google/google.yaml
```
