# 2048 App

## Kubeconfig

```
aws eks update-kubeconfig --name demo-cluster --region us-east-1
```

## Create Fargate profile

```
eksctl create fargateprofile \
    --cluster demo-cluster \
    --region us-east-1 \
    --name alb-sample-app \
    --namespace game-2048
```

## Deploy the deployment, service and Ingress

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/examples/2048/2048_full.yaml
```

## Get pods

```
kubectl get pods -n game-2048 -w
```

## Get Services (no external ip attached means no access form outside cluster)

```
kubectl get svc -n game-2048 
```

## Get ingress (No ingress controller - address)

```
kubectl get ingress -n game-2048 
```



![Screenshot 2023-08-03 at 7 57 15 PM](https://github.com/iam-veeramalla/aws-devops-zero-to-hero/assets/43399466/93b06a9f-67f9-404f-b0ad-18e3095b7353)
