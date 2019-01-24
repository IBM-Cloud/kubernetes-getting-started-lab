# Use IBM ingress domain

In the previous step, the application was accessed with a not standard port. The service was exposed by way of Kubernetes NodePort feature.

**Paid clusters come with an IBM-provided domain.** This gives you a better option to expose applications with a proper URL and on standard HTTP/S ports.

Using the Kubernetes Ingress, you can set up the cluster inbound connection to the service:
![Ingress](images/Ingress.png)

1. Identify your IBM-provided **Ingress domain**:
   {% codetabs name="Windows", type="sh" -%}
ibmcloud ks cluster-get %MYCLUSTER%
   {%- language name="Bash", type="sh" -%}
ibmcloud ks cluster-get $MYCLUSTER
   {%- endcodetabs %}
   to find
   ```
   Ingress subdomain: mycluster.us-south.containers.appdomain.cloud
   Ingress secret:    mycluster
   ```
2. Create an Ingress file `ingress-ibmdomain.yml` pointing to your domain with support for HTTP and HTTPS. Use the following file as a template, replacing all the values wrapped in <> with the appropriate values from the above output. **service-name** is the name under `==> v1/Service` in the above step or run `kubectl get svc` to find the service name of type **NodePort**.
   ```yaml
   apiVersion: extensions/v1beta1
   kind: Ingress
   metadata:
     name: ingress-for-ibmdomain-http-and-https
   spec:
     tls:
     - hosts:
       -  <nameofproject>.<ingress-sub-domain>
       secretName: <ingress-secret>
     rules:
     - host: <nameofproject>.<ingress-sub-domain>
       http:
         paths:
         - path: /
           backend:
             serviceName: <service-name>
             servicePort: 9080
   ```
3. Deploy the Ingress
   ```sh
   kubectl apply -f ingress-ibmdomain.yml
   ```
4. Access your application at `https://<nameofproject>.<ingress-sub-domain>`
