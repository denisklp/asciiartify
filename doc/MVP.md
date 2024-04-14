# Argo CD App

Argo CD dployment cycle for Go application that takes a PNG image as input with curl and returns ASCII art based on the PNG image.

## ArgoCD App Health Status

The ArgoCD application health status is currently "Progressing" due to the inability of the load balancer to obtain an external IP. Status can be seen in the screenshot below:

![Progressing Status Screenshot](mvp-1.png)

To resolve the issue with the load balancer, the deployment has been switched to use a NodePort instead using values.yaml file. The ArgoCD automatically synced app state on GitHub commit and application health status is now "Healthy" with the NodePort configuration. This can be seen in the screenshot and demo below:

![Healthy Status Screenshot](mvp-2.png)
![Demo0](demo-mvp-1.gif)

## Access

The application is deployed using Argo CD. To make the app service accessible, run the following command:

```bash
kubectl port-forward -n demo svc/ambassador 8081:80&
```
## Usage

To use the application, you need to have curl installed. Use the following command to send a PNG image to the application and receive ASCII art in response:

```bash
curl -F 'image=@image.png' localhost:8081/img/
```
## Demo

Check out the demo of the application in action:
![Demo](demo-mvp.gif)


