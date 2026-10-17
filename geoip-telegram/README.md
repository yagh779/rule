# geoip-telegram

Source config: [geoip-telegram.yaml](https://github.com/yagh779/rule/blob/main/source/geoip-telegram/geoip-telegram.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| geoip-telegram | geoip-telegram | true | http | ipcidr | text | rules |  | [telegram.txt](https://raw.githubusercontent.com/nekolsd/geoip/release/text/telegram.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "geoip-telegram"
    type: select
    proxies: []
rules:
  - RULE-SET,geoip-telegram_IP,geoip-telegram,no-resolve
  - RULE-SET,geoip-telegram_Domain,geoip-telegram # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  - RULE-SET,geoip-telegram,geoip-telegram,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  geoip-telegram_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-telegram/geoip-telegram_IP.mrs }
  geoip-telegram_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-telegram/geoip-telegram_Domain.mrs } # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  geoip-telegram: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-telegram/geoip-telegram.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
```

## Artifacts

### mrs(ipcidr)

#### geoip-telegram_IP.mrs

GitHub: [geoip-telegram_IP.mrs](https://github.com/yagh779/rule/blob/release/geoip-telegram/geoip-telegram_IP.mrs)
Text: [geoip-telegram_IP.txt](https://github.com/yagh779/rule/blob/release/geoip-telegram/geoip-telegram_IP.txt)
Source: [geoip-telegram.original.txt](https://github.com/yagh779/rule/blob/release/geoip-telegram/geoip-telegram.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-telegram/geoip-telegram_IP.mrs
```

### mrs(domain)

#### geoip-telegram_Domain.mrs

GitHub: [geoip-telegram_Domain.mrs](https://github.com/yagh779/rule/blob/release/geoip-telegram/geoip-telegram_Domain.mrs)
Text: [geoip-telegram_Domain.txt](https://github.com/yagh779/rule/blob/release/geoip-telegram/geoip-telegram_Domain.txt)
Placeholder: upstream currently has no domain rules; contains blackhole.invalid only
Source: [geoip-telegram.original.txt](https://github.com/yagh779/rule/blob/release/geoip-telegram/geoip-telegram.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-telegram/geoip-telegram_Domain.mrs
```

### yaml(remaining)

#### geoip-telegram.yaml

GitHub: [geoip-telegram.yaml](https://github.com/yagh779/rule/blob/release/geoip-telegram/geoip-telegram.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [geoip-telegram.original.txt](https://github.com/yagh779/rule/blob/release/geoip-telegram/geoip-telegram.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-telegram/geoip-telegram.yaml
```
