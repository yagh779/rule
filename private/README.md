# private

Source config: [private.yaml](https://github.com/yagh779/rule/blob/main/source/private/private.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| private | private | true | http | domain | text | rules |  | [private.txt](https://raw.githubusercontent.com/nekolsd/sing-geosite/domain-set/private.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "private"
    type: select
    proxies: []
rules:
  - RULE-SET,private_Domain,private
  - RULE-SET,private,private,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,private_IP,private,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  private_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/private/private_Domain.mrs }
  private: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/private/private.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  private_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/private/private_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### private_IP.mrs

GitHub: [private_IP.mrs](https://github.com/yagh779/rule/blob/release/private/private_IP.mrs)
Text: [private_IP.txt](https://github.com/yagh779/rule/blob/release/private/private_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [private.original.txt](https://github.com/yagh779/rule/blob/release/private/private.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/private/private_IP.mrs
```

### mrs(domain)

#### private_Domain.mrs

GitHub: [private_Domain.mrs](https://github.com/yagh779/rule/blob/release/private/private_Domain.mrs)
Text: [private_Domain.txt](https://github.com/yagh779/rule/blob/release/private/private_Domain.txt)
Source: [private.original.txt](https://github.com/yagh779/rule/blob/release/private/private.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/private/private_Domain.mrs
```

### yaml(remaining)

#### private.yaml

GitHub: [private.yaml](https://github.com/yagh779/rule/blob/release/private/private.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [private.original.txt](https://github.com/yagh779/rule/blob/release/private/private.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/private/private.yaml
```
