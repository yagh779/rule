# telegram

Source config: [telegram.yaml](https://github.com/yagh779/rule/blob/main/source/telegram/telegram.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| telegram | telegram | true | http | domain | text | rules |  | [telegram.txt](https://raw.githubusercontent.com/nekolsd/sing-geosite/domain-set/telegram.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "telegram"
    type: select
    proxies: []
rules:
  - RULE-SET,telegram_Domain,telegram
  - RULE-SET,telegram,telegram,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,telegram_IP,telegram,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  telegram_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/telegram/telegram_Domain.mrs }
  telegram: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/telegram/telegram.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  telegram_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/telegram/telegram_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### telegram_IP.mrs

GitHub: [telegram_IP.mrs](https://github.com/yagh779/rule/blob/release/telegram/telegram_IP.mrs)
Text: [telegram_IP.txt](https://github.com/yagh779/rule/blob/release/telegram/telegram_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [telegram.original.txt](https://github.com/yagh779/rule/blob/release/telegram/telegram.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/telegram/telegram_IP.mrs
```

### mrs(domain)

#### telegram_Domain.mrs

GitHub: [telegram_Domain.mrs](https://github.com/yagh779/rule/blob/release/telegram/telegram_Domain.mrs)
Text: [telegram_Domain.txt](https://github.com/yagh779/rule/blob/release/telegram/telegram_Domain.txt)
Source: [telegram.original.txt](https://github.com/yagh779/rule/blob/release/telegram/telegram.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/telegram/telegram_Domain.mrs
```

### yaml(remaining)

#### telegram.yaml

GitHub: [telegram.yaml](https://github.com/yagh779/rule/blob/release/telegram/telegram.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [telegram.original.txt](https://github.com/yagh779/rule/blob/release/telegram/telegram.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/telegram/telegram.yaml
```
