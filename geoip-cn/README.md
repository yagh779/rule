# geoip-cn

Source config: [geoip-cn.yaml](https://github.com/yagh779/rule/blob/main/source/geoip-cn/geoip-cn.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| geoip-cn | geoip-cn | true | http | ipcidr | text | rules |  | [cn.txt](https://raw.githubusercontent.com/nekolsd/geoip/release/text/cn.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "geoip-cn"
    type: select
    proxies: []
rules:
  - RULE-SET,geoip-cn_IP,geoip-cn,no-resolve
  - RULE-SET,geoip-cn_Domain,geoip-cn # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  - RULE-SET,geoip-cn,geoip-cn,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  geoip-cn_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-cn/geoip-cn_IP.mrs }
  geoip-cn_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-cn/geoip-cn_Domain.mrs } # placeholder: upstream currently has no domain rules; contains blackhole.invalid only
  geoip-cn: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/geoip-cn/geoip-cn.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
```

## Artifacts

### mrs(ipcidr)

#### geoip-cn_IP.mrs

GitHub: [geoip-cn_IP.mrs](https://github.com/yagh779/rule/blob/release/geoip-cn/geoip-cn_IP.mrs)
Text: [geoip-cn_IP.txt](https://github.com/yagh779/rule/blob/release/geoip-cn/geoip-cn_IP.txt)
Source: [geoip-cn.original.txt](https://github.com/yagh779/rule/blob/release/geoip-cn/geoip-cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-cn/geoip-cn_IP.mrs
```

### mrs(domain)

#### geoip-cn_Domain.mrs

GitHub: [geoip-cn_Domain.mrs](https://github.com/yagh779/rule/blob/release/geoip-cn/geoip-cn_Domain.mrs)
Text: [geoip-cn_Domain.txt](https://github.com/yagh779/rule/blob/release/geoip-cn/geoip-cn_Domain.txt)
Placeholder: upstream currently has no domain rules; contains blackhole.invalid only
Source: [geoip-cn.original.txt](https://github.com/yagh779/rule/blob/release/geoip-cn/geoip-cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-cn/geoip-cn_Domain.mrs
```

### yaml(remaining)

#### geoip-cn.yaml

GitHub: [geoip-cn.yaml](https://github.com/yagh779/rule/blob/release/geoip-cn/geoip-cn.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [geoip-cn.original.txt](https://github.com/yagh779/rule/blob/release/geoip-cn/geoip-cn.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/geoip-cn/geoip-cn.yaml
```
