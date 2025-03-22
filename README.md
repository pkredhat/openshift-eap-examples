# openshift-eap-examples
Examples of how to build EAP in Openshift

## Template
#### Generate the secret
```
oc apply -f secret.yaml
```
#### Generate the Template (Creates a Deploy file + service/routes)
```
oc apply -f eap-deployment-template.yaml
```
#### Process The Template
```
oc process eap-deployment-template | oc create -f -
```


### Generating Config Map
oc create configmap custom-standalone-config --from-file=standalone-openshift.xml






### Generating a PAT
https://access.redhat.com/RegistryAuthentication#getting-a-red-hat-login-2


oc create secret docker-registry redhat-pull-secret \
  --docker-server=registry.access.redhat.com \
  --docker-username="<accountname>" \
  --docker-password="<name of secret>" \
  --docker-email="<email>"

```
oc secrets link default redhat-pull-secret --for=pull -n <namespace>
```