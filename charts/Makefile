.RECIPEPREFIX := $(.RECIPEPREFIX) 
.DEFAULT_GOAL := help
.RELEASE := ./release/
.PHONY: *

help:
	@grep -E '^[a-zA-Z0-9_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "  \033[32m%-15s\033[0m %s\n", $$1, $$2}'

service-list: ## List all services
	ls -d release/* | cut -f2 -d'/' | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "  \033[32m%-15s\033[0m %s\n", $$1, $$2}'

service-install-dry-run: ## Dry-Run Install service (Ex: make service-install-dry-run service=DEMO namespace=stage-1)
	helm upgrade --install $(service) --namespace=$(namespace) -f release/$(service)/values.yaml base/symfony/ --dry-run --debug

service-install: ## Install service  (Ex: make service-install service=DEMO namespace=stage-1)
	helm upgrade --install $(service) --namespace=$(namespace) -f release/$(service)/values.yaml base/symfony/

service-delete: ## Delete service (Ex: make service-delete service=DEMO namespace=stage-1)
	helm delete $(service) --namespace=$(namespace)