# CAP deployment

This script covers the deployment and the test of SUSE Cloud Application Platform (CAP).

## SUSE Cloud Application Platform (CAP)

SUSE Cloud Application Platform is an interesting use case for Ceph RBD storage class 
and also because it leverages many kind of other Kubernetes 
resources (Daemonsets, Deployments, StatefulSets, Services, Jobs...).

The steps are:

1. Deploy CAP (~30-45min)
2. Push a demo app in PHP (https://github.com/cloudfoundry-samples/cf-ex-php-info)
3. Destroy CAP

## CLI Syntax

```
Usage:

# SUSE Cloud Application Platform (CAP)

  * Deploy CAP

    --deploy                                  Deploy Cloud Application Platform

  * Test CAP

    --test                                    Run tests on Cloud Application Platform

  * Destroy CAP

    --destroy                                Destroy the Cloud Application Platform deployment

* General Options

    --deploy-server                          Deploy the server part when used with --test-volumetype (see example 2)
    --uaa-chart-version                      UAA helm chart version, use latest if not specified
    --scf-chart-version                      SCF helm chart version, use latest if not specified
    --stratos-chart-version                  STRATOS helm chart version, use latest if not specified
    --storage-class                          'persistent' name of the storage class to use for persistent storage
    -k|--kubeconfig      <FNAME>             'kubeconfig' file path ($KUBECONFIG)
    --internal-ip        <IP>                Internal interface IP (e.g 172.16.0.1)
    --floating-ip        <IP>                For OpenStack, use the floating IP for the UAA DOMAIN (e.g 10.86.0.2)

  * Examples:

  ./cap --deploy -k kubeconfig --internal-ip 10.84.72.211 --storage-class ses6-rbd-dev
  ./cap --deploy -k kubeconfig --internal-ip 172.16.0.1 --external-ip 10.86.0.2 --storage-class cinder
  ./cap --test -k kubeconfig
    # is the same as:
  ./cap --test -ds -k kubeconfig

  ./cap --destroy -k kubeconfig

# Requirements:
 - 'kubeconfig' file
 - 'kubectl' executable in path
 - 'helm' executable in path
 - 'jq' executable in path
 - 'cf' executable in path
```
