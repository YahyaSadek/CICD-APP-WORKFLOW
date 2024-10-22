YahyaSadek


PREREQUISITES:
-Customized Docker image of the application database on DockerHub [its dockerfile is in ./db-dockerfile]
- Infrastructure already set using Terraform's workflow and ingress controller is already set.
-Create acc in SonarCloud, Organization, Project. in the org, create a Quality gate & attach it to the project 
-IAM User, ECR Repository
-GitHub Repository secrets:
    AWS_ACCESS_KEY_ID
    AWS_SECRET_ACCESS_KEY
    REGISTRY (which is the URL of the ECR [without mentioning /yourRepo])
    SONAR_TOKEN
    SONAR_ORGANIZATION
    SONAR_URL

Workflow:
(Testing, Build&Push, DeployToEKS)



Notes:
-After the terraform workflow is executed for the first time, a loadbalancer will come up at your AWS console due to creation of an ingress controller
-Attach the endpoint of this LB to your domain provider registrar (CNAME Record)
-in ./helm/vprofilecharts/templates/vproingress.yaml make sure to put your own domain so that the domain will route to the application stack properly


