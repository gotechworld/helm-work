# Quickstart Guide

This guide covers how you can quickly get started using [Helm](https://helm.sh/).

### Prerequisites

Install [Kubernetes](https://kubernetes.io/) or have access to a [cluster](https://aws.amazon.com/):
+ You must have Kubernetes installed. For the latest release of Helm, we recommend the latest stable release of Kubernetes,
which in most cases is the second-latest minor release.
+ You should also have a local configured copy of [kubectl](https://kubernetes.io/docs/tasks/tools/).

### Install the Helm Chart

To list releases across all namespaces, use '__helm list --all-namespaces__'.

To see the list of chart repositories, use '__helm repo list__'. To search for charts in a repository, use '__helm search__'.

To install a [chart](https://gitlab.altex.ro/iac/helm/-/tree/master/charts), you can run the __helm install__ command.

+ For example:

helm install <release_name> --namespace <namespace_name> _--set_ serviceKey=<parse_the_service_key> _--dry-run_ _--debug_
<path_to_an_unpacked_chart_directory>

+ #### Simulate installation:

helm install __catalog-api__ --namespace __stage-1__ --set serviceKey=<_parse_the_service_key_> _--dry-run_ _--debug_
__./hapi-catalog__

+ #### Installation:

helm install __catalog-api__ --namespace __stage-1__ --set serviceKey=<_parse_the_service_key_> __./hapi-catalog__

&nbsp;

<font color='red'> *Pay attention* </font> to the __hapi-reviews__ Helm chart  when you'll decide to install the release. Before installing it make sure you possess the 
_serviceKey_, _key_, _token_, and _XRequestAtxApi_ because these parameters are defined in the __values.yaml__ file.

+ #### Simulate installation:

helm install __reviews-api__ -n __stage-1__
--set serviceKey=<parse_the_service_key>
--set key=<parse_the_key>
--set token=<parse_the_token>
--set XRequestAtxApi=<parse_the_X-Request-AtxApi>
--dry-run
--debug
__./hapi-reviews__

+ #### Installation:

helm install __reviews-api__ -n __stage-1__
--set serviceKey=<parse_the_service_key>
--set key=<parse_the_key>
--set token=<parse_the_token>
--set XRequestAtxApi=<parse_the_X-Request-AtxApi>
__./hapi-reviews__

&nbsp;

<font color='red'> *Pay attention* </font> to the __hapi-data-transformer__ Helm chart  when you'll decide to install the release. Before installing it make sure you possess the _serviceKey_, _key_, and _Ftp password_ because these parameters are defined in the __values.yaml__ file.



+ #### Simulate installation:


helm install __data-transformer-api__ -n __stage-1__
--set serviceKey=<parse_the_service_key>
--set key=<parse_the_key>
--set password=<parse_the_Ftp_password>
--dry-run
--debug
__./hapi-data-transformer__



+ #### Installation:


helm install __data-transformer-api__ -n __stage-1__
--set serviceKey=<parse_the_service_key>
--set key=<parse_the_key>
--set password=<parse_the_Ftp_password>
__./hapi-data-transformer__

&nbsp;

__N.B.__

__Procure your serviceKey before launching the Helm chart installation.__

_--set_ stringArray = > set values on the command line (can specify multiple or separate values with commas:
key1=val1,key2=val2)

_--dry-run_ => simulate an install

_--debug_ => enable verbose output

&nbsp;

![Helm](https://www.infracloud.io/assets/img/academy/basics-of-helm.png)





