# geoip-private

Source config: [geoip-private.yaml](https://github.com/yagh779/rule/blob/main/source/geoip-private/geoip-private.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| geoip-private | geoip-private | true | http | ipcidr | text | rules |  | [private.txt](https://raw.githubusercontent.com/nekolsd/geoip/release/text/private.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "geoip-private"
    type: select
    proxies: []
rules:
  - RULE-SET,geoip-private_IP,geoip-private,no-resolve
  - RULE-SET,geoip-private_Domain,geoip-private # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  - RULE-SET,geoip-private,geoip-private,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  geoip-private_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-private/geoip-private_IP.mrs }
  geoip-private_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-private/geoip-private_Domain.mrs } # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  geoip-private: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-private/geoip-private.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
```

## Artifacts

### mrs(ipcidr)

#### geoip-private_IP.mrs

GitHub: [geoip-private_IP.mrs](https://github.com/yagh779/rule/blob/release/geoip-private/geoip-private_IP.mrs)
Text: [geoip-private_IP.txt](https://github.com/yagh779/rule/blob/release/geoip-private/geoip-private_IP.txt)
Source: [geoip-private.original.txt](https://github.com/yagh779/rule/blob/release/geoip-private/geoip-private.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-private/geoip-private_IP.mrs
```

### mrs(domain)

#### geoip-private_Domain.mrs

GitHub: [geoip-private_Domain.mrs](https://github.com/yagh779/rule/blob/release/geoip-private/geoip-private_Domain.mrs)
Text: [geoip-private_Domain.txt](https://github.com/yagh779/rule/blob/release/geoip-private/geoip-private_Domain.txt)
Placeholder: upstream currently has no domain rules; contains blackhole.invalid only
Source: [geoip-private.original.txt](https://github.com/yagh779/rule/blob/release/geoip-private/geoip-private.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-private/geoip-private_Domain.mrs
```

### yaml(remaining)

#### geoip-private.yaml

GitHub: [geoip-private.yaml](https://github.com/yagh779/rule/blob/release/geoip-private/geoip-private.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [geoip-private.original.txt](https://github.com/yagh779/rule/blob/release/geoip-private/geoip-private.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-private/geoip-private.yaml
```
