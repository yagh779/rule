# cn@!cn

Source config: [cn@!cn.yaml](https://github.com/yagh779/rule/blob/main/source/cn%40!cn/cn%40!cn.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| cn@!cn | cn@!cn | true | http | domain | text | rules |  | [cn@!cn.txt](https://raw.githubusercontent.com/nekolsd/sing-geosite/domain-set/cn@!cn.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "cn_cn"
    type: select
    proxies: []
rules:
  - RULE-SET,cn_cn_Domain,cn_cn
  - RULE-SET,cn_cn,cn_cn,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,cn_cn_IP,cn_cn,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  cn_cn_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/cn%40!cn/cn_cn_Domain.mrs }
  cn_cn: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/cn%40!cn/cn_cn.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  cn_cn_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/cn%40!cn/cn_cn_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### cn_cn_IP.mrs

GitHub: [cn_cn_IP.mrs](https://github.com/yagh779/rule/blob/release/cn%40!cn/cn_cn_IP.mrs)
Text: [cn_cn_IP.txt](https://github.com/yagh779/rule/blob/release/cn%40!cn/cn_cn_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [cn_cn.original.txt](https://github.com/yagh779/rule/blob/release/cn%40!cn/cn_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/cn%40!cn/cn_cn_IP.mrs
```

### mrs(domain)

#### cn_cn_Domain.mrs

GitHub: [cn_cn_Domain.mrs](https://github.com/yagh779/rule/blob/release/cn%40!cn/cn_cn_Domain.mrs)
Text: [cn_cn_Domain.txt](https://github.com/yagh779/rule/blob/release/cn%40!cn/cn_cn_Domain.txt)
Source: [cn_cn.original.txt](https://github.com/yagh779/rule/blob/release/cn%40!cn/cn_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/cn%40!cn/cn_cn_Domain.mrs
```

### yaml(remaining)

#### cn_cn.yaml

GitHub: [cn_cn.yaml](https://github.com/yagh779/rule/blob/release/cn%40!cn/cn_cn.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [cn_cn.original.txt](https://github.com/yagh779/rule/blob/release/cn%40!cn/cn_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/cn%40!cn/cn_cn.yaml
```
