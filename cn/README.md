# cn

Source config: [cn.yaml](https://github.com/yagh779/rule/blob/main/source/cn/cn.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| cn | cn | true | http | domain | text | rules |  | [cn.txt](https://raw.githubusercontent.com/nekolsd/sing-geosite/domain-set/cn.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "cn"
    type: select
    proxies: []
rules:
  - RULE-SET,cn_Domain,cn
  - RULE-SET,cn,cn,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,cn_IP,cn,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  cn_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/cn/cn_Domain.mrs }
  cn: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/cn/cn.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  cn_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/cn/cn_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### cn_IP.mrs

GitHub: [cn_IP.mrs](https://github.com/yagh779/rule/blob/release/cn/cn_IP.mrs)
Text: [cn_IP.txt](https://github.com/yagh779/rule/blob/release/cn/cn_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [cn.original.txt](https://github.com/yagh779/rule/blob/release/cn/cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/cn/cn_IP.mrs
```

### mrs(domain)

#### cn_Domain.mrs

GitHub: [cn_Domain.mrs](https://github.com/yagh779/rule/blob/release/cn/cn_Domain.mrs)
Text: [cn_Domain.txt](https://github.com/yagh779/rule/blob/release/cn/cn_Domain.txt)
Source: [cn.original.txt](https://github.com/yagh779/rule/blob/release/cn/cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/cn/cn_Domain.mrs
```

### yaml(remaining)

#### cn.yaml

GitHub: [cn.yaml](https://github.com/yagh779/rule/blob/release/cn/cn.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [cn.original.txt](https://github.com/yagh779/rule/blob/release/cn/cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/cn/cn.yaml
```
