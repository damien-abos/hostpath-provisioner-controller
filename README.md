# Kubernetes hostpath provisioner controller

## Introduction

hostpathctl is a batch script to manage Kubernetes persistent volumes provisioner using a hostpath configuration.

hostpathctl automates creation of Role-based User Access Control, storage class and provisioner pod.

It was developed by studying the minikube default-storageclass and storage-provisioner addons.

It shall be usefull for testing purpose.

It is free software licensed under the Apache Licence version 2.

## Quick start

### Create hostpath storageclass
To create the hostpath storageclass with its provisioner.

1. create the storage directory on cluster node.
~~~~sh
mkdir -p /tmp/hostpath
~~~~
2. execute the hostpathctl create command
~~~~sh
hostpathctl create hostpath -n kube-system
~~~~

### Delete hostpath storageclass
To delete the hostpath storageclass with its provisioner.

1. execute the hostpathctl delete command
~~~~sh
hostpathctl delete hostpath -n kube-system
~~~~
2. Optionally remove the directory on cluster node.
~~~~
rm -Rf /tmp/hostpath
~~~~

## Usage

You can change somes parameters using environment variables or command-line options. 

~~~~
Usage: hostpathctl <command> [options] <storage>

Available Commands:
  create  Create a storageclass and its provisioner
  delete  Delete a storageclass and its provisioner

Options:
    -a, --account=<storage>-account   indicate the security account allowed to create persistent volumes
    -h, --help                        print this help message
    -i, --image                       indicate the pod provider image
    -n, --namespace=default           indicate the target namespace
    -p, --path=/tmp/<storage>         indicate the path where persistent volumes will be provisioned on cluster node. It must already exists.
    -s, --service=<storage>-provider  indicate the pod provider name
    --default                         annotate the StorageClass as default
    --dry-run='none'                  must be "none", "server", or "client".
~~~~