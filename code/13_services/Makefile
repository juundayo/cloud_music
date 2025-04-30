deploy:
	@echo "🚀 Deploying Headless, LoadBalanced Services and Statefull sets..."
	kubectl apply -f 01-headless-service.yaml
	kubectl apply -f 02-loadbalancer-service.yaml
	kubectl apply -f 03-statefulset.yaml
	@echo "✅ Deployment complete."

clean:
	@echo "🧹 Cleaning up Headless, LoadBalanced Services and Statefull sets..."
	kubectl delete -f 03-statefulset.yaml
	kubectl delete -f 02-loadbalancer-service.yaml
	kubectl delete -f 01-headless-service.yaml
	@echo "✅ Cleanup complete."
