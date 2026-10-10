# category-speedtest@cn

Source config: [category-speedtest@cn.yaml](https://github.com/yagh779/rule/blob/main/source/category-speedtest%40cn/category-speedtest%40cn.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| category-speedtest@cn | category-speedtest@cn | true | http | domain | text | rules |  | [category-speedtest@cn.txt](https://raw.githubusercontent.com/nekolsd/sing-geosite/domain-set/category-speedtest@cn.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "category-speedtest_cn"
    type: select
    proxies: []
rules:
  - RULE-SET,category-speedtest_cn_Domain,category-speedtest_cn
  - RULE-SET,category-speedtest_cn,category-speedtest_cn,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,category-speedtest_cn_IP,category-speedtest_cn,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  category-speedtest_cn_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/category-speedtest%40cn/category-speedtest_cn_Domain.mrs }
  category-speedtest_cn: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/category-speedtest%40cn/category-speedtest_cn.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  category-speedtest_cn_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/category-speedtest%40cn/category-speedtest_cn_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### category-speedtest_cn_IP.mrs

GitHub: [category-speedtest_cn_IP.mrs](https://github.com/yagh779/rule/blob/release/category-speedtest%40cn/category-speedtest_cn_IP.mrs)
Text: [category-speedtest_cn_IP.txt](https://github.com/yagh779/rule/blob/release/category-speedtest%40cn/category-speedtest_cn_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [category-speedtest_cn.original.txt](https://github.com/yagh779/rule/blob/release/category-speedtest%40cn/category-speedtest_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/category-speedtest%40cn/category-speedtest_cn_IP.mrs
```

### mrs(domain)

#### category-speedtest_cn_Domain.mrs

GitHub: [category-speedtest_cn_Domain.mrs](https://github.com/yagh779/rule/blob/release/category-speedtest%40cn/category-speedtest_cn_Domain.mrs)
Text: [category-speedtest_cn_Domain.txt](https://github.com/yagh779/rule/blob/release/category-speedtest%40cn/category-speedtest_cn_Domain.txt)
Source: [category-speedtest_cn.original.txt](https://github.com/yagh779/rule/blob/release/category-speedtest%40cn/category-speedtest_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/category-speedtest%40cn/category-speedtest_cn_Domain.mrs
```

### yaml(remaining)

#### category-speedtest_cn.yaml

GitHub: [category-speedtest_cn.yaml](https://github.com/yagh779/rule/blob/release/category-speedtest%40cn/category-speedtest_cn.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [category-speedtest_cn.original.txt](https://github.com/yagh779/rule/blob/release/category-speedtest%40cn/category-speedtest_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/category-speedtest%40cn/category-speedtest_cn.yaml
```
