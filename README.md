
Feel free to contribute to this Readme file :)

The cloud native application is architected using containers and is presented to the end-user as a web application accessible over the Internet. The application frontend provides the end-user with the ability to vote on one of 6 programming languages: C#, Python, JavaScript, Go, Java, and/or NodeJS. Voting activity within the browser generates AJAX requests being sent to an API which in turn then saves the results into a MongoDB database backend.

The architecture of the cloud native application will expose you to configuring, deploying, and managing the following Kubernetes resources:

- Namespace
- Secret
- Deployment
- Service
- StatefulSet
- PersistentVolume
- PersistentVolumeClaim

### Application Architecture

The EKS cloud native application architecture consists of 3 main components, the Frontend, an API, and a MongoDB database.


References:
https://kubernetes.io/docs/home/
https://www.mongodb.com/docs/manual/tutorial/query-documents/
https://repost.aws/knowledge-center/eks-api-server-unauthorized-error (how to edit configmap if you get the error message : ""You must be logged in to the server (Unauthorized)")


>> Bonus steps:

- Within the AWS console, examine the ELBs that were created as a result of deploying the Frontend and API Services into the EKS cluster
- Try scaling up and down the Frontend deployment
- Try scaling up and down the API deployment
- Using the mongo shell, examine the replicated data copied into the Mongo Secondary nodes (`mongo-1` and `mongo-2`) within the replica set
- Deploy the Application using Terraform and ArgoCd 

**Summary**

In this Lab Step, you learnt how to deploy a cloud native application into EKS. Once deployed and up and running, you used your local workstation's browser to test out the application. You later confirmed that your activity within the application generated data which was captured and recorded successfully within the MongoDB ReplicaSet back end within the cluster.
