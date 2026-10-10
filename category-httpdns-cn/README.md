# category-httpdns-cn

Source config: [category-httpdns-cn.yaml](https://github.com/yagh779/rule/blob/main/source/category-httpdns-cn/category-httpdns-cn.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| category-httpdns-cn | category-httpdns-cn | true | http | domain | text | rules |  | [category-httpdns-cn.txt](https://raw.githubusercontent.com/nekolsd/sing-geosite/domain-set/category-httpdns-cn.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "category-httpdns-cn"
    type: select
    proxies: []
rules:
  - RULE-SET,category-httpdns-cn_Domain,category-httpdns-cn
  - RULE-SET,category-httpdns-cn,category-httpdns-cn,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,category-httpdns-cn_IP,category-httpdns-cn,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  category-httpdns-cn_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/category-httpdns-cn/category-httpdns-cn_Domain.mrs }
  category-httpdns-cn: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/category-httpdns-cn/category-httpdns-cn.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  category-httpdns-cn_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/category-httpdns-cn/category-httpdns-cn_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### category-httpdns-cn_IP.mrs

GitHub: [category-httpdns-cn_IP.mrs](https://github.com/yagh779/rule/blob/release/category-httpdns-cn/category-httpdns-cn_IP.mrs)
Text: [category-httpdns-cn_IP.txt](https://github.com/yagh779/rule/blob/release/category-httpdns-cn/category-httpdns-cn_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [category-httpdns-cn.original.txt](https://github.com/yagh779/rule/blob/release/category-httpdns-cn/category-httpdns-cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/category-httpdns-cn/category-httpdns-cn_IP.mrs
```

### mrs(domain)

#### category-httpdns-cn_Domain.mrs

GitHub: [category-httpdns-cn_Domain.mrs](https://github.com/yagh779/rule/blob/release/category-httpdns-cn/category-httpdns-cn_Domain.mrs)
Text: [category-httpdns-cn_Domain.txt](https://github.com/yagh779/rule/blob/release/category-httpdns-cn/category-httpdns-cn_Domain.txt)
Source: [category-httpdns-cn.original.txt](https://github.com/yagh779/rule/blob/release/category-httpdns-cn/category-httpdns-cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/category-httpdns-cn/category-httpdns-cn_Domain.mrs
```

### yaml(remaining)

#### category-httpdns-cn.yaml

GitHub: [category-httpdns-cn.yaml](https://github.com/yagh779/rule/blob/release/category-httpdns-cn/category-httpdns-cn.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [category-httpdns-cn.original.txt](https://github.com/yagh779/rule/blob/release/category-httpdns-cn/category-httpdns-cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/category-httpdns-cn/category-httpdns-cn.yaml
```
