# Build and push the application to a Docker registry

Before you can run the application on the cluster, you first need to push the Docker image to the IBM Cloud private container registry.

1. Find your **namespace** by listing all the namespace in the registry.
   ```sh
   ibmcloud cr namespaces
   ```
2. Set MYNAMESPACE and MYPROJECT environment variables to your namespace and project name respectively
   {% codetabs name="Windows", type="sh" -%}
set MYNAMESPACE=<NAMESPACE>
set MYPROJECT=<PROJECT_NAME>
   {%- language name="Bash", type="sh" -%}
export MYNAMESPACE=<NAMESPACE>
export MYPROJECT=<PROJECT_NAME>
   {%- endcodetabs %}
3. Identify your **Container Registry** (e.g. registry.ng.bluemix.net) by running:
   ```sh
   ibmcloud cr info
   ```
   The output should be similar to:
   ```sh
   Container Registry                registry.ng.bluemix.net
   Container Registry API endpoint   https://registry.ng.bluemix.net/api
   IBM Cloud API endpoint            https://api.ng.bluemix.net
   IBM Cloud account details         John's Account (123456fafafafa)
   IBM Cloud organization details     ()
   ```
4. Set MYREGISTRY env var to your registry (e.g registry.ng.bluemix.net).
   {% codetabs name="Windows", type="sh" -%}
set MYREGISTRY=<REGISTRY>
   {%- language name="Bash", type="sh" -%}
export MYREGISTRY=<REGISTRY>
   {%- endcodetabs %}
5. Build and tag (`-t`) the docker image
   {% codetabs name="Windows", type="sh" -%}
docker build . -t %MYREGISTRY%/%MYNAMESPACE%/%MYPROJECT%:v1.0.0
   {%- language name="Bash", type="sh" -%}
docker build . -t $MYREGISTRY/$MYNAMESPACE/$MYPROJECT:v1.0.0
   {%- endcodetabs %}
6. Ensure you are logged into the IBM container registry
   ```sh
   ibmcloud cr login
   ```
7. Push the docker image to your container registry on IBM Cloud
   {% codetabs name="Windows", type="sh" -%}
docker push %MYREGISTRY%/%MYNAMESPACE%/%MYPROJECT%:v1.0.0
   {%- language name="Bash", type="sh" -%}
docker push $MYREGISTRY/$MYNAMESPACE/$MYPROJECT:v1.0.0
   {%- endcodetabs %}
