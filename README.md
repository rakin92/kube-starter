## Kubernetes Starter

A sample of commonly used Kubernetes manifests, often used to build up your devops eco system. This assume you have your clusters setup correctly.

#### Cheat Sheet
Assuming you have `kubectl` setup

> Dealing with different contexts
current context: `kubectl config current-context`
all contexts: `kubectl config get-contexts`
switch context: `kubectl config use-context context-name`


> Deploy or apply changes
`kubectl apply -f name.yaml`
example:
`kubectl apply -f deployment.yaml`


> Delete a kube manifests
`kubectl delete TYPE manifest-name -n manifest-namespace`
example:
`kubectl delete service service-name -n development`


**Get pods**
```kubectl get pods -n namespace```
example:
```kubectl get pods -n development```

**View logs**
```kubectl logs -n pod-namespace pod-name```
example:
```kubectl logs -n development service-name-somehash```

> Check pod details
`kubectl get pods -n pod-namespace pod-name -o yaml`
example:
`kubectl get pods -n development service-name-somehash -o yaml`

> Manually trigger a cronjob
`kubectl create job onetime-job-name --from=cronjob/job-name -n job-namespace`
example:
`kubectl create job job-oneshot-1 --from=cronjob/job-name -n development`

> Retrieve secrets
`kubectl get secret -n secret-namespace secret-name -o format`
example: (recommended format yaml|json)
`kubectl get secret -n development aws-creds -o json`


> Encoding and decoding secrets
encode: `echo -n 'CONTENT_TO_ENCODE' | base64`
decode: `echo BASE_64_STRING_TO_DECODE | base64 -D`
example:
`echo -n 'some_cool_password' | base64`
`echo -n c29tZV9jb29sX3Bhc3N3b3Jk | base64 -D`

#### Suggested Tool

* [K9S](https://k9ss.io/): Allows you to manage and monitor your deployments

#### Helpful URL

* [Kubernetes Docs](https://kubernetes.io/docs/home/)
* [Kubectl cheat sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
* [Cronjob schedule maker](https://crontab.guru/)
