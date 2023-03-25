$ kubectl apply -f namespace.yaml

# pgsql installation

$ kubectl apply -f pgsql/pv.yaml -n strapi

$ kubectl apply -f pgsql/pgsql-configmap.yaml  -n strapi

$ kubectl apply -f pgsql/pgsql-deploymnet.yaml -n strapi

$ kubectl apply -f pgsql/pgsql-service.yaml -n strapi

# Strapi Deployment

$ kubectl create secret generic strapi-prod --from-env-file=pgsql/.env -n strapi

$ kubectl create secret tls auth-tls-secret --key strapi/auth-tls.key --cert strapi/auth-tls.crt -n strapi

$ kubectl apply -f strapi/strapi.yaml -n strapi

$ kubectl apply -f strapi/strapi-ingress.yaml -n strapi