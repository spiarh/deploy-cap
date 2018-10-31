# CAP deployment

This script covers the deployment and the test of SUSE Cloud Application Platform (CAP).

## SUSE Cloud Application Platform (CAP)

SUSE Cloud Application Platform is an interesting use case for Ceph RBD storage class 
and also because it leverages many kind of other Kubernetes 
resources (Daemonsets, Deployments, StatefulSets, Services, Jobs...).

The steps are:

1. Deploy CAP (~30-45min)
2. Push a demo app in GO (https://github.com/cloudfoundry-samples/test-app)
3. Push a demo app in PHP (https://github.com/cloudfoundry-samples/cf-ex-php-info)
4. Destroy CAP

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

    -ds|--deploy-server                      Deploy the server part when used with --test-volumetype (see example 2)
    --uaa-chart-version                      UAA helm chart version, use latest if not specified
    --scf-chart-version                      SCF helm chart version, use latest if not specified
    --stratos-chart-version                  STRATOS helm chart version, use latest if not specified
    -sc|--storage-class                      'persistent' name of the storage class to use for persistent storage
    -e|--environment     <FNAME>             'environment.json' file path ($ENVIRONMENT)
    -k|--kubeconfig      <FNAME>             'kubeconfig' file path ($KUBECONFIG)
    -ssh|--ssh-config    <FNAME>             'environment.ssh_config' file path ($ENVIRONMENT_SSH)

  * Examples:

  ./cap --deploy -k kubeconfig -sc persistent -ssh environment.ssh_config -e environment.json
  ./cap --test -k kubeconfig -ssh environment.ssh_config -e environment.json
    # is the same as:
  ./cap --test -ds -k kubeconfig -ssh environment.ssh_config -e environment.json

  ./cap --destroy -k kubeconfig -ssh environment.ssh_config -e environment.json

# Requirements:
 - 'kubeconfig' file
 - 'environment.json' file
 - 'environment.ssh_config' file
 - 'kubectl' executable in path
 - 'helm' executable in path
 - 'jq' executable in path
```
