# cn-additional-list

Source config: [cn-additional-list.yaml](https://github.com/yagh779/rule/blob/main/source/cn-additional-list/cn-additional-list.yaml)

## Source Files

| name |description |enabled |type |behavior |format |mihomo |headers |url |path |payload |
| --- |--- |--- |--- |--- |--- |--- |--- |--- |--- |--- |
| cn-additional-list | cn-additional-list | true | http | domain | yaml | rules |  | [cn-additional-list-clash.yaml](https://static-file-global.353355.xyz/rules/cn-additional-list-clash.yaml) |  |  |

## Mihomo Config

```yaml
proxy-groups:
  - name: "cn-additional-list"
    type: select
    proxies: []
rules:
  - RULE-SET,cn-additional-list_Domain,cn-additional-list
  - RULE-SET,cn-additional-list,cn-additional-list,no-resolve # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  - RULE-SET,cn-additional-list_IP,cn-additional-list,no-resolve # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
rule-anchor:
  github-token-header: &github-token-header { Authorization: ["Bearer <YOUR_GITHUB_TOKEN>"] }
  ip: &ip { type: http, behavior: ipcidr, format: mrs, interval: 86400, header: *github-token-header }
  domain: &domain { type: http, behavior: domain, format: mrs, interval: 86400, header: *github-token-header }
  yaml: &yaml { type: http, behavior: classical, format: yaml, interval: 86400, header: *github-token-header }
rule-providers:
  cn-additional-list_Domain: { <<: *domain, url: https://raw.githubusercontent.com/yagh779/rule/release/cn-additional-list/cn-additional-list_Domain.mrs }
  cn-additional-list: { <<: *yaml, url: https://raw.githubusercontent.com/yagh779/rule/release/cn-additional-list/cn-additional-list.yaml } # placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
  cn-additional-list_IP: { <<: *ip, url: https://raw.githubusercontent.com/yagh779/rule/release/cn-additional-list/cn-additional-list_IP.mrs } # placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
```

## Artifacts

### mrs(ipcidr)

#### cn-additional-list_IP.mrs

GitHub: [cn-additional-list_IP.mrs](https://github.com/yagh779/rule/blob/release/cn-additional-list/cn-additional-list_IP.mrs)
Text: [cn-additional-list_IP.txt](https://github.com/yagh779/rule/blob/release/cn-additional-list/cn-additional-list_IP.txt)
Placeholder: upstream currently has no ipcidr rules; contains 203.0.113.1/32 only
Source: [cn-additional-list.original.yaml](https://github.com/yagh779/rule/blob/release/cn-additional-list/cn-additional-list.original.yaml)

```text
https://raw.githubusercontent.com/yagh779/rule/release/cn-additional-list/cn-additional-list_IP.mrs
```

### mrs(domain)

#### cn-additional-list_Domain.mrs

GitHub: [cn-additional-list_Domain.mrs](https://github.com/yagh779/rule/blob/release/cn-additional-list/cn-additional-list_Domain.mrs)
Text: [cn-additional-list_Domain.txt](https://github.com/yagh779/rule/blob/release/cn-additional-list/cn-additional-list_Domain.txt)
Source: [cn-additional-list.original.yaml](https://github.com/yagh779/rule/blob/release/cn-additional-list/cn-additional-list.original.yaml)

```text
https://raw.githubusercontent.com/yagh779/rule/release/cn-additional-list/cn-additional-list_Domain.mrs
```

### yaml(remaining)

#### cn-additional-list.yaml

GitHub: [cn-additional-list.yaml](https://github.com/yagh779/rule/blob/release/cn-additional-list/cn-additional-list.yaml)
Placeholder: upstream currently has no remaining rules; contains DOMAIN,blackhole.invalid only
Source: [cn-additional-list.original.yaml](https://github.com/yagh779/rule/blob/release/cn-additional-list/cn-additional-list.original.yaml)

```text
https://raw.githubusercontent.com/yagh779/rule/release/cn-additional-list/cn-additional-list.yaml
```
