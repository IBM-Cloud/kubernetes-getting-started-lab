# Target your environment

## Kubernetes

In this step, you'll configure kubectl to point to your cluster going forward. [kubectl](https://kubernetes.io/docs/user-guide/kubectl-overview/) is a command line tool that you use to interact with a Kubernetes cluster.

1. Target the resource group you have been assigned to:
   ```sh
   ibmcloud target -g <RESOURCE_GROUP_NAME>
   ```
1. Retrieve the cluster configuration by setting MYCLUSTER environment variable to your cluster name:
   {% codetabs name="Windows PowerShell", type="sh" -%}
$env:MYCLUSTER=<CLUSTER_NAME>
ibmcloud ks cluster-config -s --cluster %MYCLUSTER% --export
   {% codetabs name="Windows Command", type="sh" -%}
set MYCLUSTER=<CLUSTER_NAME>
ibmcloud ks cluster-config -s --cluster %MYCLUSTER% --export
   {%- language name="Bash", type="sh" -%}
export MYCLUSTER=<CLUSTER_NAME>
ibmcloud ks cluster-config -s $MYCLUSTER --export
   {%- endcodetabs %}
1. Copy and paste the displayed **set** command to set the KUBECONFIG environment variable as directed. To verify whether the KUBECONFIG environment variable is set properly or not, run the following command: `echo %KUBECONFIG%`
1. Check that the `kubectl` command is correctly configured
   ```sh
   kubectl cluster-info
   ```

   The output should look like:
   ![](images/kubectl_cluster-info.png)

## Cloud Foundry

Although you are going to deploy a Kubernetes application, the `ibmcloud dev` plugin requires a Cloud Foundry organization and space to be targeted in case you want to deploy the application in Cloud Foundry or provision Cloud Foundry services.

1. Select the organization and space assigned to you for the lab:
   ```
   ibmcloud target --cf
   ```
