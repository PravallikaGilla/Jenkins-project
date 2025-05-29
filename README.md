# Jenkins-project

Project Description: Build a Java Application, create a docker image from it and push to docker repository. Then, update the Kubernetes manifest (yaml file) which resides in another git repository. 

These pipelines are build using Jenkins.

Pipeline 1: Java application is build using maven, a docker image is created from java app and pushed it to private docker hub repository. Then, pipeline waits for manual input to trigger next pipeline( Proceed - it triggers next pipeline i.e pipeline-2, Abort - doesn't trigger the next pipeline). This pipeline will pass yaml file name and version to piepline-2

Pipeline 2: Clone the yaml file repo from git, update the image with the version provided by pipeline-1 in the yaml file and push the updated file back to the repo.

Pipeline-2 repo will be triggered by Argo CD