# Scaling

As load increases on your application, you can manually increase the number of pod replicas in your deployment. Replicas are managed by a [ReplicaSet](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/).

## Manual

To scale the application to two replicas, run the following command:

{% codetabs name="Windows", type="sh" -%}
kubectl scale deployment %MYPROJECT%-deployment --replicas=2
{%- language name="Bash", type="sh" -%}
kubectl scale deployment $MYPROJECT-deployment --replicas=2
{%- endcodetabs %}

After a shortwhile, you will see two pods for your application in the Kubernetes dashboard (or with `kubectl get pods`). The Ingress controller in the cluster will handles the load balancing between the two replicas. Horizontal scaling can also be made automatic.

## Automatic

Refer to Kubernetes documentation for manual and automatic scaling:

   * [Scaling a deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#scaling-a-deployment)
   * [Horizontal Pod Autoscaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/)
