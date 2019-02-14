# Build and push the application to a Docker registry

Before you can run the application on the cluster, you first need to push the Docker image to the IBM Cloud private container registry.

1. Set MYPROJECT environment variable. Replace <PROJECT_NAME> with your project name.
   {% codetabs name="Windows", type="sh" -%}
set MYPROJECT=<PROJECT_NAME>
   {%- language name="Bash", type="sh" -%}
export MYPROJECT=<PROJECT_NAME>
   {%- endcodetabs %}
1. Set MYNAMESPACE and MYREGISTRY and env vars. Copy and paste these commands.
   {% codetabs name="Windows", type="sh" -%}
set MYNAMESPACE=think-iks
set MYREGISTRY=registry.ng.bluemix.net
   {%- language name="Bash", type="sh" -%}
export MYNAMESPACE=think-iks 
export MYREGISTRY=registry.ng.bluemix.net
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
