# Setup Artifactory repository and deploy example with Artifactory Maven plugin

## Purpose

Installing the Artifactory repository in the Kubernets cluster on the GCE
Deploy 'artifactory-maven-plugin-example' to the Artifactory repository

## Requirements

Jenkins with Maven and Artifactory plugin

## Usege

1. Create new pipline item in Jenkins
2. Enable "This is a parameterized assembly" checkbox
3. Add following parameters:
    - SERVER_URL (String parameter)
    - USERNAME   (String parameter)
    - PASSWORD   (Passwor parameter)
4. Add content from jenkins file to Pipeline field (Definition - Pipeline script)
5. Save the pipeline item
6. Push 'Build with parameters'
7. Fill in the fields as follows:
    SERVER_URL - Your cluster Endpoint
    USERNAME   - Cluster admin username
    PASSWORD   - Cluster admin password

## Expected result

Jenkins will perform a download of the `kubectl` and `helm`.
Then it'll create the `kubeconfig` file based on the entered parameters.
On the next step it'll  configure `Tiller` in the cluster and deploy
Artifactory repository with helm-chart with default credentials to `default` namespace.
In the next step, Jenkins will make changes to the `pom.xml` file.
Next Jenkins will build `'artifactory-maven-plugin-example'` with Maven and the Artifactory plug-in.
