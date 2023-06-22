<!-- See https://squidfunk.github.io/mkdocs-material/reference/ -->
# Part 2: Application

1. Introduction: The Web Application and its Features:
    Welcome to the application phase of our workshop. Our focus here is a web application, built on the Go's Gin Gonic framework, featuring a game that challenges your logo identification skills. The application is backed by an integrated SQLite database and keeps things exciting with a leaderboard to track the highest scores. Think of it as a fun, interactive tech quiz that also serves as a practical demonstration of our tools in action.

2. ArgoCD: The Diligent Manager:
    ArgoCD, as we discussed in the setup stage, is like the diligent stage manager of our deployment process, constantly monitoring and reconciling changes between the Git repository and the live cluster. With ArgoCD in the picture, any committed change in Git is automatically detected, leading to the creation of a new pod based on the updated image tag. It’s like having a tireless watchdog that ensures our live cluster is always in sync with our Git repository.

    ArgoCD also offers deployment flexibility. You can switch the branch that ArgoCD tracks with ease. So, when it's time to create a release branch in your Git repository, you simply update the branch name in the Argo Application YAML. This allows you to deploy the updated app to your actual cluster, while you continue to develop on the main branch. ArgoCD takes care of the rest, automatically picking up any updates to the release branch, ensuring your application stays up-to-date on the cluster.

3. Tekton: The Meticulous Craftsman:
    Tekton, on the other hand, plays the role of a meticulous craftsman, taking care of the continuous integration aspect. Whenever changes are committed to the repository, Tekton springs into action, triggering the building of a new image based on the latest commit, as well as an update to the deployment image tag to match the latest image tag. Tekton ensures that our application is always running the latest and greatest version, much like a skilled artisan constantly refining their masterpiece.

4. The Power of Integration: ArgoCD and Tekton in a CI/CD Pipeline: 
    Together, Tekton and ArgoCD form a CI/CD pipeline that's not only efficient but also robust. While the initial setup might feel like assembling a complex puzzle, the end result is a powerful, automated, and adaptive system that's well worth the effort. Moreover, the modular nature of this setup allows for easy expansion with additional pipelines. Imagine being able to introduce an end-to-end test pipeline that's triggered with every PR—it's like adding a new, valuable piece to your automation toolkit with minimal fuss.

## Discussion

- Introduction to the web application built on the Gin framework.
- Role of ArgoCD as a stage manager for deployment.
- Role of Tekton in continuous integration.
- Integration of ArgoCD and Tekton in a CI/CD pipeline.
- Scalability and modularity of the setup.
- Deployment flexibility with ArgoCD.
