
deploy:
	@echo "🚀 Deploying Kubernetes PostgreSQL + Web Server setup..."
	kubectl apply -f 01-secret.yaml
	kubectl apply -f 02-configmap.yaml
	kubectl apply -f init-sql-configmap.yaml
	kubectl apply -f 03-pvc.yaml
	kubectl apply -f 04-postgres.yaml
	kubectl wait --for=condition=Ready pod/postgres
	kubectl cp music/. postgres:/songs
	kubectl apply -f 05-postgres-service.yaml
	kubectl apply -f 06-web-content-configmap.yaml
	kubectl apply -f 07-webserver.yaml
	kubectl apply -f 08-webserver-service.yaml
	@echo "✅ Deployment complete."

clean:
	@echo "🧹 Cleaning up Kubernetes PostgreSQL + Web Server setup..."
	-kubectl delete -f 08-webserver-service.yaml
	-kubectl delete -f 07-webserver.yaml
	-kubectl delete -f 06-web-content-configmap.yaml
	-kubectl delete -f 05-postgres-service.yaml
	-kubectl delete -f 04-postgres.yaml
	-kubectl delete -f 03-pvc.yaml
	-kubectl delete -f init-sql-configmap.yaml
	-kubectl delete -f 02-configmap.yaml
	-kubectl delete -f 01-secret.yaml
	@echo "✅ Cleanup complete."

deployBlyat:
	@echo "🚀 Deploying Kubernetes PostgreSQL + Web Server setup..."
	kubectl apply -f 01-secret.yaml
	kubectl apply -f 02-configmap.yaml
	kubectl apply -f init-sql-configmap.yaml
	kubectl apply -f 03-pvc.yaml
	kubectl apply -f 04-postgres.yaml
	kubectl apply -f 10-mongo.yaml
	kubectl wait --for=condition=Ready pod/postgres
	kubectl wait --for=condition=Ready pod/mongodb-0
	kubectl wait --for=condition=Ready pod/mongodb-1
	kubectl cp music/. mongodb-0:/data/music
	kubectl cp music/. mongodb-1:/data/music
	kubectl apply -f 05-postgres-service.yaml
	kubectl apply -f 06-web-content-configmap.yaml
	kubectl apply -f 09-webserver-deployment.yaml
	kubectl apply -f 08-webserver-service.yaml
	@echo "✅ Deployment complete."

cleanBlyat:
	@echo "🧹 Cleaning up Kubernetes PostgreSQL + Web Server setup..."
	-kubectl delete -f 08-webserver-service.yaml
	-kubectl delete -f 10-mongo.yaml
	-kubectl delete -f 09-webserver-deployment.yaml
	-kubectl delete -f 06-web-content-configmap.yaml
	-kubectl delete -f 05-postgres-service.yaml
	-kubectl delete -f 04-postgres.yaml
	-kubectl delete -f 03-pvc.yaml
	-kubectl delete -f init-sql-configmap.yaml
	-kubectl delete -f 02-configmap.yaml
	-kubectl delete -f 01-secret.yaml
	@echo "✅ Cleanup complete."

