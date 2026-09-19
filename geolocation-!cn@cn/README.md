# geolocation-!cn@cn

Source config: [geolocation-!cn@cn.yaml](https://github.com/yagh779/rule/blob/main/source/geolocation-!cn%40cn/geolocation-!cn%40cn.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| geolocation-!cn@cn | geolocation-!cn@cn | true | http | domain | text | rules |  | [geolocation-!cn@cn.txt](https://raw.githubusercontent.com/nekolsd/sing-geosite/domain-set/geolocation-!cn@cn.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "geolocation-_cn_cn"
    type: select
    proxies: []
rules:
  - RULE-SET,geolocation-_cn_cn_Domain,geolocation-_cn_cn
  - RULE-SET,geolocation-_cn_cn,geolocation-_cn_cn,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,geolocation-_cn_cn_IP,geolocation-_cn_cn,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  geolocation-_cn_cn_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/geolocation-!cn%40cn/geolocation-_cn_cn_Domain.mrs }
  geolocation-_cn_cn: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/geolocation-!cn%40cn/geolocation-_cn_cn.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  geolocation-_cn_cn_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/geolocation-!cn%40cn/geolocation-_cn_cn_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### geolocation-_cn_cn_IP.mrs

GitHub: [geolocation-_cn_cn_IP.mrs](https://github.com/yagh779/rule/blob/release/geolocation-!cn%40cn/geolocation-_cn_cn_IP.mrs)
Text: [geolocation-_cn_cn_IP.txt](https://github.com/yagh779/rule/blob/release/geolocation-!cn%40cn/geolocation-_cn_cn_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [geolocation-_cn_cn.original.txt](https://github.com/yagh779/rule/blob/release/geolocation-!cn%40cn/geolocation-_cn_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geolocation-!cn%40cn/geolocation-_cn_cn_IP.mrs
```

### mrs(domain)

#### geolocation-_cn_cn_Domain.mrs

GitHub: [geolocation-_cn_cn_Domain.mrs](https://github.com/yagh779/rule/blob/release/geolocation-!cn%40cn/geolocation-_cn_cn_Domain.mrs)
Text: [geolocation-_cn_cn_Domain.txt](https://github.com/yagh779/rule/blob/release/geolocation-!cn%40cn/geolocation-_cn_cn_Domain.txt)
Source: [geolocation-_cn_cn.original.txt](https://github.com/yagh779/rule/blob/release/geolocation-!cn%40cn/geolocation-_cn_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geolocation-!cn%40cn/geolocation-_cn_cn_Domain.mrs
```

### yaml(remaining)

#### geolocation-_cn_cn.yaml

GitHub: [geolocation-_cn_cn.yaml](https://github.com/yagh779/rule/blob/release/geolocation-!cn%40cn/geolocation-_cn_cn.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [geolocation-_cn_cn.original.txt](https://github.com/yagh779/rule/blob/release/geolocation-!cn%40cn/geolocation-_cn_cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geolocation-!cn%40cn/geolocation-_cn_cn.yaml
```
