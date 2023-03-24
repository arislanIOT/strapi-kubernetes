# strapi-kubernetes
strapi project with ci and kubernetes deployment. 


#
$   kubectl patch pv jhooq-pv -p '{"metadata":{"finalizers":null}}'
$   kubectl patch pvc jhooq-pv-claim -p '{"metadata":{"finalizers":null}}'


#

kubectl port-forward --namespace default svc/psql-postgresql 5432:5432 & PGPASSWORD="$POSTGRES_PASSWORD" psql --host 127.0.0.1 -U postgres -d postgres -p 5432


$ kubectl create secret -n namespace tls auth-tls-secret --key auth-tls.key --cert auth-tls.crt

$ kubectl create secret generic prod --from-env-file=.env