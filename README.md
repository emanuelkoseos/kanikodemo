# Kaniko builds

> Build Docker Images with Docker Daemon

### First create a kubernetes secret with docker registry credentials

Update the exmaple.yaml with your --destination dockerhub settings
Create token in Kubrenetes to allow access to docker hub:
kubectl create secret docker-registry regcred --docker-server=<your-registry-server> --docker-username=<your-name> --docker-password=<your-pword> --docker-email=<your-email>

### update example.yaml

Update the --context setting with your repository information

Github uses a token now for git calls; otherwise you can try https:// format

Other environments as as follows:

Local Directory 	
dir://[path to a directory in the kaniko container] 	
dir:///workspace
*** note you can create a directory using minikube ssh and then add persistent volumes/claims 

Local Tar Gz 	
tar://[path to a .tar.gz in the kaniko container] 	
tar://path/to/context.tar.gz

Standard Input 	
tar://[stdin] 	
tar://stdin

GCS Bucket 	
gs://[bucket name]/[path to .tar.gz] 	
gs://kaniko-bucket/path/to/context.tar.gz

S3 Bucket 	
s3://[bucket name]/[path to .tar.gz] 	
s3://kaniko-bucket/path/to/context.tar.gz

Azure Blob Storage 	
https://[account].[azureblobhostsuffix]/[container]/[path to .tar.gz] 	
https://myaccount.blob.core.windows.net/container/path/to/context.tar.gz

Git Repository 	

git://[repository url][#reference][#commit-id] 	
git://TOKEN@github.com/acme/myproject.git#refs/heads/mybranch#<desired-commit-id>

where TOKEN is a generated personal token on your account; alternatively can use https://
