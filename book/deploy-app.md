# Deploy the application with Helm

With the application Docker image pushed to the IBM Cloud private container registry, you can now proceed to create a Kubernetes deployment pointing to that image.

1. Helm is a tool to manage Kubernetes applications through Helm Charts, which help define, install, and upgrade even the most complex Kubernetes application. Initialize Helm by running the below command in your cluster
   ```bash
   helm init
   ```
   {% hint style='tip' %}
   To upgrade helm, run this command `helm init --upgrade`
   {% endhint %}

1. To install a Helm chart, change to the `chart\YOUR PROJECT NAME` directory and run the install command
   {% codetabs name="Windows", type="sh" -%}
helm install . --name %MYPROJECT% --set image.repository=%MYREGISTRY%/%MYNAMESPACE%/%MYPROJECT% --debug
   {%- language name="Bash", type="sh" -%}
helm install . --name $MYPROJECT --set image.repository=$MYREGISTRY/$MYNAMESPACE/$MYPROJECT --debug
   {%- endcodetabs %}
1. Identity the public port the service is listening on. The port is a 5-digit number (e.g., 31569) under `PORT(S)`.
   {% codetabs name="Windows", type="sh" -%}
kubectl get service %MYPROJECT%-service
   {%- language name="Bash", type="sh" -%}
kubectl get service $MYPROJECT-service
   {%- endcodetabs %}
11. For the public IP of worker node, run the below command and pick the public IP of one of the workers. Replace `<CLUSTER_NAME>` with the cluster assigned to you:
   {% codetabs name="Windows", type="sh" -%}
ibmcloud ks workers <CLUSTER_NAME>
   {%- language name="Bash", type="sh" -%}
ibmcloud ks workers <CLUSTER_NAME>
   {%- endcodetabs %}
12. Access the application at `http://worker-ip-address:portnumber/`.
