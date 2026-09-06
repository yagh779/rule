# category-ai-!cn

Source config: [category-ai-!cn.yaml](https://github.com/yagh779/rule/blob/main/source/category-ai-!cn/category-ai-!cn.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| category-ai-!cn | category-ai-!cn | true | http | domain | text | rules |  | [category-ai-!cn.txt](https://raw.githubusercontent.com/nekolsd/sing-geosite/domain-set/category-ai-!cn.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "category-ai-_cn"
    type: select
    proxies: []
rules:
  - RULE-SET,category-ai-_cn_Domain,category-ai-_cn
  - RULE-SET,category-ai-_cn,category-ai-_cn,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,category-ai-_cn_IP,category-ai-_cn,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  category-ai-_cn_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/category-ai-!cn/category-ai-_cn_Domain.mrs }
  category-ai-_cn: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/category-ai-!cn/category-ai-_cn.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  category-ai-_cn_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/category-ai-!cn/category-ai-_cn_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### category-ai-_cn_IP.mrs

GitHub: [category-ai-_cn_IP.mrs](https://github.com/yagh779/rule/blob/release/category-ai-!cn/category-ai-_cn_IP.mrs)
Text: [category-ai-_cn_IP.txt](https://github.com/yagh779/rule/blob/release/category-ai-!cn/category-ai-_cn_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [category-ai-_cn.original.txt](https://github.com/yagh779/rule/blob/release/category-ai-!cn/category-ai-_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/category-ai-!cn/category-ai-_cn_IP.mrs
```

### mrs(domain)

#### category-ai-_cn_Domain.mrs

GitHub: [category-ai-_cn_Domain.mrs](https://github.com/yagh779/rule/blob/release/category-ai-!cn/category-ai-_cn_Domain.mrs)
Text: [category-ai-_cn_Domain.txt](https://github.com/yagh779/rule/blob/release/category-ai-!cn/category-ai-_cn_Domain.txt)
Source: [category-ai-_cn.original.txt](https://github.com/yagh779/rule/blob/release/category-ai-!cn/category-ai-_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/category-ai-!cn/category-ai-_cn_Domain.mrs
```

### yaml(remaining)

#### category-ai-_cn.yaml

GitHub: [category-ai-_cn.yaml](https://github.com/yagh779/rule/blob/release/category-ai-!cn/category-ai-_cn.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [category-ai-_cn.original.txt](https://github.com/yagh779/rule/blob/release/category-ai-!cn/category-ai-_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/category-ai-!cn/category-ai-_cn.yaml
```
