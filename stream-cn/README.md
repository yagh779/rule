# stream-cn

Source config: [stream-cn.yaml](https://github.com/yagh779/rule/blob/main/source/stream-cn/stream-cn.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| stream-cn | stream-cn | true | http | domain | text | rules |  | [direct.yaml](https://raw.githubusercontent.com/Sfssup/mihomo-set/main/rule_set/direct.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "stream-cn"
    type: select
    proxies: []
rules:
  - RULE-SET,stream-cn_Domain,stream-cn
  - RULE-SET,stream-cn,stream-cn,no-resolve
  - RULE-SET,stream-cn_IP,stream-cn,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  stream-cn_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/stream-cn/stream-cn_Domain.mrs }
  stream-cn: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/stream-cn/stream-cn.yaml }
  stream-cn_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/stream-cn/stream-cn_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### stream-cn_IP.mrs

GitHub: [stream-cn_IP.mrs](https://github.com/yagh779/rule/blob/release/stream-cn/stream-cn_IP.mrs)
Text: [stream-cn_IP.txt](https://github.com/yagh779/rule/blob/release/stream-cn/stream-cn_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [stream-cn.original.yaml](https://github.com/yagh779/rule/blob/release/stream-cn/stream-cn.original.yaml)

```text
https://raw.githubusercontent.com/yagh779/rule/release/stream-cn/stream-cn_IP.mrs
```

### mrs(domain)

#### stream-cn_Domain.mrs

GitHub: [stream-cn_Domain.mrs](https://github.com/yagh779/rule/blob/release/stream-cn/stream-cn_Domain.mrs)
Text: [stream-cn_Domain.txt](https://github.com/yagh779/rule/blob/release/stream-cn/stream-cn_Domain.txt)
Source: [stream-cn.original.yaml](https://github.com/yagh779/rule/blob/release/stream-cn/stream-cn.original.yaml)

```text
https://raw.githubusercontent.com/yagh779/rule/release/stream-cn/stream-cn_Domain.mrs
```

### yaml(remaining)

#### stream-cn.yaml

GitHub: [stream-cn.yaml](https://github.com/yagh779/rule/blob/release/stream-cn/stream-cn.yaml)
Source: [stream-cn.original.yaml](https://github.com/yagh779/rule/blob/release/stream-cn/stream-cn.original.yaml)

```text
https://raw.githubusercontent.com/yagh779/rule/release/stream-cn/stream-cn.yaml
```
