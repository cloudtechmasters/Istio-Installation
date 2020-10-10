# Istio-Installation.md

# Step1: DOWNLOAD AND INSTALL ISTIO CLI
Before we can get started configuring Istio we’ll need to first install the command line tools that you will interact with. To do this run the following.
  
    echo 'export ISTIO_VERSION="1.5.2"' >> ${HOME}/.bash_profile
    source ${HOME}/.bash_profile
    mkdir environment
    cd ~/environment
    curl -L https://istio.io/downloadIstio | sh -
The installation directory contains:
*Installation YAML files for Kubernetes in install/kubernetes
*Sample applications in samples/
*The istioctl client binary in the bin/ directory (istioctl is used when manually injecting Envoy as a sidecar proxy).

    cd ${HOME}/environment/istio-${ISTIO_VERSION}
    sudo cp -v bin/istioctl /usr/bin/
We can verify that we have the proper version in our $PATH
    
    istioctl version --remote=false
# INSTALL ISTIO
Istio will be installed in the istio-system namespace.
    
    istioctl manifest apply --set profile=demo
We can verify all the services have been installed.

    kubectl -n istio-system get svc
and check the corresponding pods with

    kubectl -n istio-system get pods
