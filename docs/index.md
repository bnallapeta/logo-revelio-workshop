# Introduction

Our agenda for today's workshop is an exploration into the transformative ecosystem of Kubernetes, Tekton, and ArgoCD, all deployed on the robust infrastructure of Equinix Metal. This workshop is designed to be hands-on. So, feel free to follow along by getting your hands dirty throughout the process. Our goal is to provide an opportunity for you to gain practical experience with these wonderful technologies, and to showcase the integration of these with Equinix Metal. 

## About the workshop

In this interactive workshop, our primary focus is to harness the capabilities of Tekton and ArgoCD. Tekton, an open-source platform, empowers developers to construct flexible CI/CD systems directly within Kubernetes. On the other hand, ArgoCD, a GitOps continuous delivery tool, allows automatic synchronization and deployment of application updates from Git repositories to the production environment.

We will begin with provisioning Kubernetes on Equinix Metal, utilizing the Cluster API. Subsequently, we will guide you on setting up Metallb Load Balancer, a key step to ensure your application's external IP exposure.

Next, we'll dive into setting up ArgoCD, leveraging kustomize for declarative GitOps, and Tekton for Continuous Integration and Continuous Deployment. Additionally, we will demonstrate the implementation of Pipelines as Code, making the whole process as automated as possible for least effort in maintaining the CI/CD and focusing on your core application development.


## Workshop agenda

The workshop is split in a structured format, divided into three key parts:

Setup & Provisioning: This phase will guide you through the process of setting up and provisioning the environment, specifically focusing on provisioning Kubernetes on Equinix Metal with the help of Cluster API.
Application Deployment: In this segment, we will direct you through the application deployment process, spotlighting the functionalities of Tekton and ArgoCD.
Conclusion: This final part will wrap up our workshop, providing a comprehensive summary of our journey, achievements, and the knowledge you've gained from this session.

