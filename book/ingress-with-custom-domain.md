# Use a custom domain

To use your custom domain, you need to update your DNS records with either a CNAME record pointing to your IBM-provided domain or an A record pointing to the portable public IP address of the IBM-provided Ingress. As a paid cluster comes with fixed IP addresses, an A record is a good option.

Given it may take time for DNS to propagate, this step is out of the scope of this tutorial. You will find detailed instructions on how to use your own custom domain in the service document under [Using the Ingress controller with a custom domain](https://cloud.ibm.com/docs/containers/cs_apps.html#custom_domain_cert) and in [this other tutorial](https://cloud.ibm.com/docs/tutorials/scalable-webapp-kubernetes.html#custom_domain).
