# Strapi with PostgresSQL
---

## Create namespace for strapi and pgsql

    $ kubectl apply -f strapi/namespace.yaml

# pgsql installation

#### If the cluster is provisioned with dynamic storage we don't need to provision persistant volume and persistant volume claim manually. 

## provisioning pv and pvc for the database persistant storage


    $ kubectl apply -f pgsql/pv.yaml -n strapi

    $ kubectl apply -f pgsql/pgsql-configmap.yaml  -n strapi

    $ kubectl apply -f pgsql/pgsql-deploymnet.yaml -n strapi

    $ kubectl apply -f pgsql/pgsql-service.yaml -n strapi

# Strapi Deployment

## Create secret for strapi to connect with database. 

    $ kubectl create secret generic strapi-prod --from-env-file=pgsql/.env -n strapi

## Install strapi and ingress 

    $ kubectl apply -f strapi/strapi.yaml -n strapi

    $ kubectl apply -f strapi/strapi-ingress.yaml -n strapi


## In this repo both minimal and production level Dockerfile is provide for the custom image building of the strapi image. 

## Command to build and push strapi image

    $ docker build -t repository_username/repository_name:tag  .

    $ docker push repository_username/repository_name:tag

    