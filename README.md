# Déployer un Container App - CLI

### Créer un groupe de ressources 

```bash
RESOURCE_GROUP="mon-container-apps"
LOCATION="canadacentral"
CONTAINERAPPS_ENVIRONMENT="mon-environment"
az group create --name $RESOURCE_GROUP --location $LOCATION
```
### Créer un environnement
```bash
az containerapp env create --name $CONTAINERAPPS_ENVIRONMENT --resource-group $RESOURCE_GROUP --location $LOCATION
```
### Créer Container App
```bash
az containerapp create \
  --name my-container-app \
  --resource-group $RESOURCE_GROUP \
  --environment $CONTAINERAPPS_ENVIRONMENT \
  --image mcr.microsoft.com/azuredocs/containerapps-helloworld:latest \
  --target-port 80 \
  --ingress 'external' \
  --query properties.configuration.ingress.fqdn
  ```
