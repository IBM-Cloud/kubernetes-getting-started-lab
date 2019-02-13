# Build the application locally

You can build and run the application as you normally would using `mvn` for Java local development or `npm` for Node. You can also build a docker image and run the application in a container to ensure consistent execution locally and on the cloud. Use the following steps to build your docker image.

1. Ensure your local Docker engine is started.
   ```sh
   docker ps
   ```
2. Change to the generated project directory.
   ```sh
   cd <project name>
   ```
3. Build the application.
   ```sh
   ibmcloud dev build
   ```

   {% hint style='info' %}
   This might take a few minutes to run as all the application dependencies are downloaded and a Docker image, which contains your application and all the required environment, is built.
   {% endhint %}

