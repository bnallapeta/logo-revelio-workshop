<!-- See https://squidfunk.github.io/mkdocs-material/reference/ -->
# Part 1: Setup
We're going to start by setting up Kubernetes on Equinix Metal with the help of the Cluster API. We'll also incorporate MetalLB for load balancing, ensuring that we have provision to assign external IPs. Post that, we will jump into installing Argocd, Tekton and Pipelines as Code and finally the application deployment.

## Steps

1. k8s on metal: To get Kubernetes on board with Equinix Metal, here's the blueprint - https://cluster-api.sigs.k8s.io/user/quick-start.html. The link contains customized instructions for our Equinix Metal clusters, making it a lot easier.

_Eager for more? The source repo for the Cluster API Provider Packet is a wealth of knowledge - kubernetes-sigs/cluster-api-provider-packet: https://github.com/kubernetes-sigs/cluster-api-provider-packet/tree/main. From code and docs to tests, it's a comprehensive guide to everything you need._

2. metallb as Loadbalancer: Once we've got our Kubernetes cluster up and running, it's time to deploy MetalLB. Use this guide for a straightforward installation - https://metallb.universe.tf/installation. 

_Note: Manifest method tends to work best - https://metallb.universe.tf/installation/#installation-by-manifest._

You need to manually update the secret 'metal-cloud-config' to add a couple of annotations. This is to make sure that metallb assigns external IPs to our services.
  a. echo "{"apiKey": "xxxxxxxxxxxxxxxxxxxxx","projectID": "56565446-8850c-sadfsd-235435-sadfsadg", "loadbalancer":"metallb:///?crdConfiguration=true", "annotationEIPMetro=da"}" | base64 -w0
    This will give you a base64 encoded string.
  b. Get the secret into a yaml file: kubectl get secret/metal-cloud-config -n kube-system -o yaml > metal-cloud-config.yaml
    Replace the content under .data.cloud-sa.json with the string from step 1.
  c. Apply the secret: kubectl apply -f metal-cloud-config.yaml

Before moving on to our application (logo-revelio), we require some important tools that are the focus of this workshop - Tekton and ArgoCD.

3. Setting up ArgoCD and Tekton are quite straightforward. Follow these instructions on their respective sites. Essentially, its running one “kubectl apply -f ” command on their release.yaml files.
https://argo-cd.readthedocs.io/en/stable/getting_started
https://github.com/tektoncd/pipeline/blob/main/docs/install.md

4. Setup Pipelines as Code:
   a. Much like Argo and Tekton, you can run the kubectl install -f on their release.yaml
https://pipelinesascode.com/docs/install/installation/ 
   b. Additionally, we'll set up a Github app, allowing PaC to monitor the repository for Pull Requests/Push events.
   c. Follow the instructions from the link below where you can either set up the app from the Github GUI. Or, simply install the “tkn pac” utility (https://github.com/tektoncd/cli/releases) and you can set up the whole app quite easily - https://pipelinesascode.com/docs/install/github_apps/ 

5. With our cluster prepped and our toolkit ready, we can finally focus on our application - Logo Revelio. Go ahead and deploy logo-revelio by following the instructions from the Readme - https://github.com/bnallapeta/logo-revelio
It's as simple as running a 'kubectl apply -f' on the ArgoCD app. This will get the app resources deployed to the cluster and we're off!

## Discussion

Before proceeding to the next part let's take a few minutes to discuss what we did. Here are some questions to start the discussion.

* We setup kubernetes on Equinix Metal using Cluster API.
* We setup metallb as our loadbalancer.
* We setup Argocd and Tekton for our CI/CD needs.
* We setup our application Logo Revelio on the cluster.

Now, we are all set to explore the powerful capabilities of Tekton, ArgoCD, and how they seamlessly integrate with Equinix Metal.
