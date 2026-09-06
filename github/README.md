# github

Source config: [github.yaml](https://github.com/yagh779/rule/blob/main/source/github/github.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| github | github | true | http | domain | text | rules |  | [github.txt](https://raw.githubusercontent.com/nekolsd/sing-geosite/domain-set/github.txt) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "github"
    type: select
    proxies: []
rules:
  - RULE-SET,github_Domain,github
  - RULE-SET,github,github,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,github_IP,github,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  github_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/github/github_Domain.mrs }
  github: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/github/github.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  github_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/github/github_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### github_IP.mrs

GitHub: [github_IP.mrs](https://github.com/yagh779/rule/blob/release/github/github_IP.mrs)
Text: [github_IP.txt](https://github.com/yagh779/rule/blob/release/github/github_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [github.original.txt](https://github.com/yagh779/rule/blob/release/github/github.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/github/github_IP.mrs
```

### mrs(domain)

#### github_Domain.mrs

GitHub: [github_Domain.mrs](https://github.com/yagh779/rule/blob/release/github/github_Domain.mrs)
Text: [github_Domain.txt](https://github.com/yagh779/rule/blob/release/github/github_Domain.txt)
Source: [github.original.txt](https://github.com/yagh779/rule/blob/release/github/github.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/github/github_Domain.mrs
```

### yaml(remaining)

#### github.yaml

GitHub: [github.yaml](https://github.com/yagh779/rule/blob/release/github/github.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [github.original.txt](https://github.com/yagh779/rule/blob/release/github/github.original.txt)

```text
https://raw.githubusercontent.com/yagh779/rule/release/github/github.yaml
```
