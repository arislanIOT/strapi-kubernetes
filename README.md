# strapi-kubernetes
strapi project with ci and kubernetes deployment. 


#
$   kubectl patch pv jhooq-pv -p '{"metadata":{"finalizers":null}}'
$   kubectl patch pvc jhooq-pv-claim -p '{"metadata":{"finalizers":null}}'


#

kubectl port-forward --namespace default svc/psql-postgresql 5432:5432 & PGPASSWORD="$POSTGRES_PASSWORD" psql --host 127.0.0.1 -U postgres -d postgres -p 5432





# Installing Kong gateway API without DB(dbless mode) and with kong ingress controller. 

$   helm install kong/kong --generate-name --set ingressController.enabled=true 
    --set postgresql.enabled=false --set env.database=off --create-namespace --namespace=kong

# Setting up strapi 

1. Docker image without .env. That is need to add .dockerignore file while building the image 
    .env
    .cache/
    .git/
    build/
    node_modules/
    .env
    data/

    general ones, cross check with developer on the same. 

$ docker build -t docker_repository_name/image_name:tag  Dockefile.prod 

$ docker push docker_repository_name/image_name:tag

$ generate SSL cert 

# Generate secret with the SSL certs 

$ kubectl create secret -n namespace tls auth-tls-secret --key auth-tls.key --cert auth-tls.crt

# Split the sensitive data and general data with configmap and secrets 

# Create a secret and configmap from the .env for production, here I created secret only for poc 

$ kubectl create secret generic prod --from-env-file=.env




    