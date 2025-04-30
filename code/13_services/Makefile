apply:
	kubectl apply -f 01-headless-service.yaml
	kubectl apply -f 02-loadbalancer-service.yaml
	kubectl apply -f 03-statefulset.yaml

delete:
	kubectl delete -f 03-statefulset.yaml
	kubectl delete -f 02-loadbalancer-service.yaml
	kubectl delete -f 01-headless-service.yaml
