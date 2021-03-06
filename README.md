[![Docker Stars](https://img.shields.io/docker/stars/bmcclure89/docker-pythonpackager.svg?style=flat-square)](https://hub.docker.com/r/bmcclure89/docker-pythonpackager/) [![Docker Pulls](https://img.shields.io/docker/pulls/bmcclure89/docker-pythonpackager.svg?style=flat-square)](https://hub.docker.com/r/bmcclure89/docker-pythonpackager/) ![Docker Image Size (latest by date)](https://img.shields.io/docker/image-size/bmcclure89/docker-pythonpackager)

This image can be used to build your python packages using wheel, push the package to our Azure Devops repo, and then clean up after it's self. 

build this image:
```
docker build -t pythonpackagebuild .
```

You will need to generate a PAT from your Azure devops account with the following scopes: `Packaging (Read & Write)`
From your package directory (ie the directory with your setup.py script) run this command: 
```
docker run --rm -e "PAT=YourPAT" -e "AZURE_DEVOPS_ARTIFACT_REPO_URL=https://pkgs.dev.azure.com/YourOrg/YourProject/_packaging/ArtifactRepoName/pypi/upload" -e "AZURE_DEVOPS_ARTIFACT_REPO_NAME=ArtifactRepoName" -v ${PWD}:/src pythonpackagebuild
```
