# Target your environment

In this step, you'll configure kubectl to point to your cluster going forward. [kubectl](https://kubernetes.io/docs/user-guide/kubectl-overview/) is a command line tool that you use to interact with a Kubernetes cluster.

1. Target the resource group you have been assigned to:
   ```sh
   ibmcloud target -g think-iks --cf
   ```
2. Retrieve the cluster configuration:
   {% codetabs name="Windows", type="sh" -%}
ibmcloud ks cluster-config <CLUSTER_NAME>
   {%- language name="Bash", type="sh" -%}
ibmcloud ks cluster-config <CLUSTER_NAME>
   {%- endcodetabs %}
1. Copy and paste the displayed **set** command to set the KUBECONFIG environment variable as directed. To verify whether the KUBECONFIG environment variable is set properly or not, run the following command: `echo %KUBECONFIG%`
2. Check that the `kubectl` command is correctly configured
   ```sh
   kubectl cluster-info
   ```

   The output should look like:
   ![](images/kubectl_cluster-info.png)