# 合约生成：contract.yaml / codes.yaml 是事实源，生成物不得手改。
APPKIT ?= GOWORK=off go run github.com/forgeplex/appkit/cmd/appkit@v0.9.9

.PHONY: generate generate-check build
generate:
	$(APPKIT) gen contract -in catalogv1/contract.yaml -dir catalogv1
	$(APPKIT) gen errors -in catalogv1/codes.yaml -out catalogv1/codes.gen.go

generate-check: generate
	git diff --exit-code -- .

build:
	GOWORK=off go build ./... && GOWORK=off go vet ./...
