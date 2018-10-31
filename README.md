# CAP deployment



TODO: 

```
Add option to set/configure the storage class
Add option to configure the version
Add option to configure the sizing of the deployment ???
```



This script covers the deployment and the test of SUSE Cloud Application Platform (CAP).

**Note for CAP**:

The script will only work from **CAP 2.8.0**.

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

    --deploy-cap                                  Deploy Cloud Application Platform

  * Test CAP

    --test-cap                                    Run tests on Cloud Application Platform

  * Destroy CAP

    --destroy-cap                                 Destroy the Cloud Application Platform deployment

* General Options

    -ds|--deploy-server                           Deploy the server part when used with --test-volumetype (see example 2)
    -e|--environment     <FNAME>                  'environment.json' file path ($ENVIRONMENT)
    -k|--kubeconfig      <FNAME>                  'kubeconfig' file path ($KUBECONFIG)
    -sc|--ssh-config     <FNAME>                  'environment.ssh_config' file path ($ENVIRONMENT_SSH)

  * Examples:

  ./deploy-cap --deploy-cap -k kubeconfig -sc environment.ssh_config -e environment.json
  ./deploy-cap --test-cap -k kubeconfig -sc environment.ssh_config -e environment.json
    # is the same as:
  ./deploy-cap --test-cap -ds -k kubeconfig -sc environment.ssh_config -e environment.json

  ./deploy-cap --destroy-cap -k kubeconfig -sc environment.ssh_config -e environment.json

# Requirements:
 - 'kubeconfig' file
 - 'environment.json' file
 - 'environment.ssh_config' file
 - 'kubectl' executable in path
 - 'helm' executable in path
 - 'jq' executable in path
 - 'cf' executable in path
```
