# commerce-contracts

Commerce SaaS 各域之间共享、版本化的 Go 合约（module `github.com/forgeplex/commerce-contracts/go`）。
`go/*/contract.yaml` 与 `codes.yaml` 是事实源，AppKit 生成的 Go、HTTP client/server 与 OpenAPI 文件不得手改。

| 合约 | 提供方 | 消费方 | 说明 |
| --- | --- | --- | --- |
| `catalogv1.GetListing` | commerce-catalog | commerce-channel（上架） | 读取当前租户一个商品的上架资料 |

这些是**内部服务合约**，不是对外 HTTP API。请求不携带租户：提供方只按可信 callctx 里的租户读取。

```sh
cd go
make generate        # 重新生成
make generate-check  # 生成物与事实源一致
```
