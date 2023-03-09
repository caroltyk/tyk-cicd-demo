# petstore

This is a helm chart that deploys https://petstore3.swagger.io and a Tyk API.

1. In `image` section, configure the application image tag. Alternatively, modify `appVersion` in `Charts.yaml`
```
image:
  repository: swaggerapi/petstore3
  pullPolicy: IfNotPresent
  # Overrides the image tag whose default is the chart appVersion.
  tag: ""
```

2. To install manually using Helm
```
kubectl create ns petstore-app
helm install petstore . -n petstore-app -f values.yaml
```

3. To redeploy with an updated OAS JSON file

- Update `configs/petstore3-oas.json`
- Redeploy the Chart (double check if tykoasapidefinition.tyk.io/tyk-cicd-demo-petstore-app is reloaded)

4. To test the API
```
curl {GATEWAY_URL}/petstore3/pet/findByStatus?status=available
```
